---
layout: post
title: Deferred Work Using Sidekiq
Date: 2013-11-03
comments: true
categories: lpca 

---

As we've discussed at certain points in the past, user experience is extremely
important, and back-end developers have a lot to do with that as well.  Many
users can deal with 'ugly' if the interface is clear, but no one on Earth likes
slow!  We'll look at how to take needed work out of the request/response cycle
in this exercise.

Step 0
------

We'll be revisiting the [house project](https://github.com/itsbspoke/aitfc) with
this exercise.  I've merged the work that we've accomplished into master, so
that you'll be able to either update your forks, or pull the changes down
locally.

What's that, you *weren't* working on a branch when you made your changes, and you
can't apply my changes quickly?

If you have made changes on master that are now irrelevant, try issuing these
commands:

```bash Terminal
git commit -a -m "Saving my work, just in case"
git checkout -b save-my-work
git branch -D master
git checkout -b master -t origin/master
```
That should get you ready to work again.  But create branches when you start
working!  It's easy!  Here's the branch I'd start here:

```bash Terminal
git checkout -b friend-graph-sidekiq
```

Step 1
------

Add these files to your Gemfile:

``` ruby Gemfile
gem "koala", "~> 1.8.0rc1"
gem 'sidekiq'

# add this in the test group
gem 'mocha', :require => 'mocha/api'
```

Install them.  You should know how by now!  Ask a neighbor if you don't.

Step 2
------

Put these contents in spec/models/social_connection_spec.rb

``` ruby spec/models/social_connection_spec.rb
require 'spec_helper'

describe SocialConnection do

  describe "validation" do
    subject{ build(:social_connection) }
    it{ should be_valid }
    it "should require a user" do
      build(:social_connection, user: nil).should_not be_valid
    end
    it "should require a provider" do
      build(:social_connection, provider: nil).should_not be_valid
    end
    it "should require a uid" do
      build(:social_connection, uid: nil).should_not be_valid
    end
  end

  describe "associations" do
    it "should be present on user" do
      build(:user).respond_to?(:social_connections).should == true
    end
  end

  describe "Facebook" do
    let(:user){ create(:user) }

    describe "interface" do
      subject{ FacebookInterface.for(user) }
      it {should_not be_nil}
      it {should be_a(FacebookInterface::StubInterface)}
    end

    describe "usage" do
      let(:fbi){ FacebookInterface.for(user) }
    end

  end
end
```
This will give you a spec to pass!  Run your specs with either:

```bash Terminal
bundle exec guard start -i
```

or

```bash Terminal
bundle exec rake spec
```

if you know that guard isn't working for you.

To pass this test, you'll need to:

* create a model with the right fields and types
* add the proper associations throughout the domain
* add validations to the class you create

If you'd like a hint, download [this file](https://gist.github.com/bigfleet/7292464#file-social_connections-rb) into 
<code>spec/factories/social_connections.rb</code>, or simply refer to it inline.

Our goal with this step is to create a record that allows us to keep track of
some basic information for social connections on the part of our users.  When
you have this spec passing, you have the domain layer ready!  Now let's proceed
to the integration.

Step 3
------

Place this file in <code>spec/support/facebook_interface.rb</code>.

``` ruby spec/support/facebook_interface.rb
class FacebookInterface

  class StubInterface

    def friends
      [
        {
          "name" => "James Schaffer",
          "id" => "11670"
        },
        {
          "name" => "Brian O'Malley",
          "id" => "615125"
        },
        {
          "name" => "Greg Staff",
          "id" => "1507686"
        },
        {
          "name" => "Katherine McNerney",
          "id" => "1530325"
        },
        {
          "name" => "Joel Bonasera",
          "id" => "1905046"
        },
        {
          "name" => "Denny Abraham",
          "id" => "1911249"
        }
      ]
    end

    def friend_detail(id)
      {
        "id" => id.to_s,
        "name" => "James Schaffer",
        "first_name" => "James",
        "last_name" => "Schaffer",
        "link" => "https://www.facebook.com/jas.schaffer",
        "username" => "jas.schaffer",
        "gender" => "male",
        "locale" => "en_US",
        "updated_time" => "2013-09-23T02:08:44+0000"
      }
    end
  end
end

FacebookInterface.stubs(:for).returns(FacebookInterface::StubInterface.new)
```

Place this file in <code>spec/support/sidekiq.rb</code>

``` ruby spec/support/sidekiq.rb
require 'sidekiq/testing'
Sidekiq::Testing.fake!
```

Finally, place this spec in place in
<code>spec/models/facebook_friend_worker_spec.rb</code>:

``` ruby spec/models/facebook_friend_worker_spec.rb
require 'spec_helper'

describe FacebookFriendWorker do

  subject{ FacebookFriendWorker.new }

  it "should include the line 'include Sidekiq::Worker'" do
    subject.respond_to?(:jid).should == true
  end

  context "when processing friends" do

    before(:each) do
      @user = create(:user)
    end

    it "should save all friends" do
      lambda{ subject.perform(@user.id) }.should change(SocialConnection, :count).by(6)
    end

    context  "attribute saving" do
      before(:each) do
        subject.perform(@user.id)
        @friend = SocialConnection.where(uid: "1905046").first
      end

      it "should store uid" do
        @friend.should_not be_nil
      end

      it "should save provider" do
        @friend.provider.should == "facebook"
      end

      it "should store name" do
        @friend.name.should == "Joel Bonasera"
      end

      it "should be bidirectional" do
        @friend.follower.should == true
        @friend.follows.should == true
      end

    end
  end

end
```

This will give you the next spec to run.  This will test that you can progress
through the Facebook API response, and save the results to the DB in the
appropriate manner.

It's customary to create an <code>app/workers</code> directory to place your
<code>FacebookFriendWorker</code>, as well as any other background workers that
you create.  So the code that you write to pass this test should go in
<code>app/workers/facebook_friend_worker.rb</code>.

When your specs are passing here, we've added the ability to defer work outside
of the request/response cycle.  We're most of the way to seeing this work!

Step 4
------

**Add** this spec to your <code>spec/models/authentication_spec.rb</code> file:

``` ruby spec/models/authentication_spec.rb
 context "saving Facebook auths" do
   subject{ build(:authentication) }
   it "should enqueue a Facebook friend saver when saved" do
     expect { subject.save }.to change(FacebookFriendWorker.jobs, :size).by(1)
   end
 end
```

Write a lifecycle method on Authentication that will enqueue the worker.  We're
definitely getting close now!

Step 5: Putting it all together
------

Code wise, you are ready to go!  We have a few more things to put in place
before we can actually **run** the code and have everything work.

First, sidekiq requires redis, so let's install that.

```bash Terminal
brew install redis
```

We don't want redis to run all the time-- it's not as cool as postgres.  It does
need some configuration to run, so let's save [this file](https://gist.github.com/bigfleet/7292464#file-redis-conf) at
<code>config/redis.conf</code>

Finally, **add** these two lines to your <code>Procfile</code>:

```ruby Procfile
redis: redis-server config/redis.conf
worker: bundle exec sidekiq
```

Step 6:
---

```bash Terminal
bundle exec foreman start
```
And try it in your web browser!

You should see something in your server window like:

```
11:15:52 worker.1 | 2013-11-03T16:15:52Z 60093 TID-ovijid2f0 FacebookFriendWorker JID-afefbf22f98c6c4f37a82132 INFO: done: 4.197 sec
```

if it worked.  You can then use the data in there to print out various things in
the rest of your app.  Try it out!



