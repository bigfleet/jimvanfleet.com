---
layout: post
title: "Facebook OAuth using OmniAuth and Rails 4"
Date: 2013-10-21
comments: true
categories: facebook, oauth, omniauth
---

<h2>Allowing Facebook logins in Rails 4</h2>


<p>I had to copy and paste in information from a variety of sources to end up
with something I liked at the time of this writing.  Since I want to walk my
students in <a href="http://www.launchpadcodeacademy.com/">Launchpad Code
Academy</a> through this process, I figured I'd make this walkthrough public.
It may help newcomers for quite some time to come!</p>

<h3>About this solution</h3>

<p>We are going to be using a server-side OAuth authorization.  The mechanism
uses some JavaScript checks and interfaces with the JS Facebook API, but
ultimately the connection is made on the server-side.</p>

<p>You don't necessarily have to be using Devise, but if you're not, our tips
about how to leverage this approach for Facebook login may not be helpful.</p>

<p>With a little extra work, you can allow users that have attached their
Facebook account to log in with Facebook.  You might even be able to adapt this
approach to allowing users to create accounts with a single click.  But you
won't like that as much when you want to get Twitter involved, since Twitter
doesn't send an email address in its OAuth callback.  It's best to have existing
users affiliate their accounts and then providing login as a convenience.</p>

<h3>Getting started</h3>

<span class="step">Step 1: Installing gems</span>

<p>Include these gems in your Gemfile:</p>

``` ruby Gemfile
gem "omniauth"
gem 'omniauth-facebook', '1.4.0'
```

<p>Install them in your terminal with the bundle command:</p>

``` bash Terminal
bundle install
```

<span class="step">Step 2</span>

<p>Per the <a href="https://github.com/mkdynamic/omniauth-facebook#usage">usage
instructions for omniauth-facebook</a>, create a new file in config/initializers
named omniauth.rb:</p>

```ruby config/initializers/omniauth.rb
OmniAuth.config.logger = Rails.logger

Rails.application.config.middleware.use OmniAuth::Builder do
  provider :facebook, ENV['FACEBOOK_KEY'], ENV['FACEBOOK_SECRET']
end
```

<p>The config/initializers directory is designed for use on Rails startup to
configure how libraries are intended to operate.  In this case, we want our
Rails application to know that we are using Omniauth, and are configuring the
Facebook provider to reference environment variables to run.</p>

<p>To set these environment variables properly, we'll need to go get some info
from Facebook.</p>

<h3>Creating and configuring a Facbook App</h3>

<span class="step">Step 1: An app</span>

<p>I honestly don't remember what it's like to register for a Facebook developer
account, other than it should be free, and it should happen at the
<a href="https://developers.facebook.com/">Facebook Developers</a> site.</p>

<p>When you've registered properly, there should be an "Apps" tab in your
navigation.  Click on that to travel to <a href="https://developers.facebook.com/apps">
your list of apps.</a></p>

<p>Click "Create New App".  You should pick a name that indicates you are doing
testing.  You can place it in a namespace, if you like, but that's optional.</p>

Mine looked like this:

![](https://www.evernote.com/shard/s1/sh/7383f6e2-cebb-4bcc-b630-6df857a7ee54/6cb1990638eea3cedcbf2bb5372279e6/deep/0/Facebook%20Developers.png)

Click "Continue", and you should be brought to an application screen that
contains your App ID (or API Key) and your App Secret.  Note those, but we'll
need to fill in some information here.

In the "App Domains" box, put 'localhost'

Click the green check on "Website with Facebook Login", and fill that in with
http://localhost:5000/.  My students (or anyone who uses <a href="https://github.com/bigfleet/rails-templates">my Rails templates</a>)
will be able to use this.  This value may be different for you-- make sure that it
matches whatever you use in development.  localhost:3000 would be common if you
are using <code>rails s</code> and appname.dev would be likely if you were using
Pow.

![](https://www.evernote.com/shard/s1/sh/45f415ea-8f8c-4249-ba0e-d7e2c40dde6c/800ff5c9285390d745236d13f5464b03/deep/0/Basic-%20Facebook%20Developers.png)

Mine looked like this

<span class="step">Step 2: Installing application details</span>

<p>Students in my class use <a
href="https://github.com/ddollar/foreman">foreman</a> to run their development
environment.  If you won't, perhaps you can consider <a href="https://github.com/bkeepers/dotenv">dotenv</a>,
to load env variables from files for you?  It's important not to commit
sensitive information like this Facebook App Secret to your repository.  Note
the difficulties and caveats, should you ever need to <a href="https://help.github.com/articles/remove-sensitive-data">remove sensitive data</a>.
Usage of foreman or dotenv can help with that.</p>

<p>If you are using foreman, you can add these files to your .env file (which is
not in version control).  Instead of the values below, they should match your
own app's key and secret that you obtained previously.  You cannot just copy and
paste this file.  I totally made up these numbers, and they will not work.</p>

```ruby .env
FACEBOOK_KEY=686338067928534
FACEBOOK_SECRET=60b9fe21ab431897eabc0743b39a5406
```

<h3>Facebook Powers: Activate!</h3>

<span class="step">Step 1: Create a model to store the authentications</span>

<p>We don't want to tie authentications to a user in a 1-1 way, since we'd love
to allow connecting with other social networks by default.  We want a user to
have many social networks attached, potentially, so we'll create a model that
appropriately attaches to users.</p>

<p>Create an Authentication model using this command: </p>

```bash Terminal
bundle exec rails g model Authentication user_id:integer provider:string uid:string name:string oauth_token:string oauth_expires_at:datetime
```

<p>This will create a migration for you similar to this:</p>

```ruby db/migrate/20131015222934_create_authentications.rb
class CreateAuthentications < ActiveRecord::Migration
  def change
    create_table :authentications do |t|
      t.integer :user_id
      t.string :provider
      t.string :uid
      t.string :name
      t.string :oauth_token
      t.datetime :oauth_expires_at
 
      t.timestamps
    end
  end
end
```

<p>You'll also need to provide a mechanism for Omniauth to save the data it can
provide to your DB for your use.  After you issue the above command, you should
have an <code>app/models/authentications.rb</code> file.  Replace that file with
these contents:</p>


```ruby app/models/authentication.rb
class Authentication < ActiveRecord::Base

  belongs_to :user

  def self.from_omniauth(user, auth)
    where(auth.slice(:provider, :uid)).first_or_initialize.tap do |authentication|
      authentication.user = user
      authentication.provider = auth.provider
      authentication.uid = auth.uid
      authentication.name = auth.info.name
      authentication.oauth_token = auth.credentials.token
      authentication.oauth_expires_at = Time.at(auth.credentials.expires_at)
      authentication.save!
    end
  end

end
```

<p>Be sure to also add <code>has_many :authentications</code> to your
<code>app/models/user.rb</code> file.  And don't forget to run your database
migrations here!</p>

<span class="step">Step 2: Create the authentication user interface</span>

```bash Terminal
bundle exec rails g controller authentications index
```

<p>This will create an authentications controller, and a view file for you.  We
don't quite want any of what we get out of the package.  Copy these file
contents into your authentications controller:</p>

```ruby app/controllers/authentications_controller.rb
class AuthenticationsController < ApplicationController

  def index
    @authentications = current_user.authentications if current_user
  end

  def create
    auth = Authentication.from_omniauth(current_user, env["omniauth.auth"])
    flash[:notice] = "Authentication successful."
    redirect_to authentications_url
  end

  def destroy
    @authentication = current_user.authentications.find(params[:id])
    @authentication.destroy
    flash[:notice] = "Successfully destroyed authentication."
    redirect_to authentications_url
  end

end
```
<p>Place this file into your JavaScript directory.  Note that <strong>this one won't
work either by just copying and pasting</strong>!  You need to include your non-sensitive
App ID :</p>

```javascript app/assets/javascripts/facebook.js
// Additional JS functions here
window.fbAsyncInit = function() {
  FB.init({
    appId      : 686338067928534, // App ID
    status     : true, // check login status
    cookie     : true, // enable cookies to allow the server to access the session
    xfbml      : true  // parse XFBML
  });
};

// Load the SDK Asynchronously
(function(d){
   var js, id = 'facebook-jssdk', ref = d.getElementsByTagName('script')[0];
   if (d.getElementById(id)) {return;}
   js = d.createElement('script'); js.id = id; js.async = true;
   js.src = "//connect.facebook.net/en_US/all.js";
   ref.parentNode.insertBefore(js, ref);
}(document));

function fblogin() {
  FB.getLoginStatus(function(response) {
    if(response.status == "connected") {
      location.href =
        '/auth/facebook/callback?' +
        $.param({ signed_request: response.authResponse.signedRequest })
    } else {
     FB.login(function(response) {
      if (response.authResponse) {
          '/auth/facebook/callback?' +
          $.param({ signed_request: response.authResponse.signedRequest })
      }
     })
    }
  })
};
```
<p>Copy this view file into place, as the bulk of our tutorial actions will
happen there.  There are HTML comment blocks below-- my blog assumes I want a
hyphen, when I really do want two dashes.  Be sure the file matches <a href="https://gist.github.com/bigfleet/7088190">this gist</a>. </p>

```erb app/views/authentications/index.html.erb
<% if @authentications %>
  <% unless @authentications.empty? %>
    <p><strong>You can sign in to this account using:</strong></p>
    <div class="authentications">
      <% for authentication in @authentications %>
        <div class="authentication">
          <%= image_tag "#{authentication.provider}_32.png", :size => "32x32" %>
          <div class="provider"><%= authentication.provider.titleize %></div>
          <div class="uid"><%= authentication.uid %></div>
          <%= link_to "X", authentication, :confirm => 'Are you sure you want to remove this authentication option?', :method => :delete, :class => "remove" %>
        </div>
      <% end %>
      <div class="clear"></div>
    </div>
  <% end %>
  <p><strong>Add another service to sign in with:</strong></p>
<% else %>
  <p><strong>Sign in through one of these services:</strong></p>
<% end %>

<!--
<a href="/auth/twitter" class="auth_provider">
  <%= image_tag "twitter_64.png", :size => "64x64", :alt => "Twitter" %>
  Twitter
</a>
-->
<% unless @authentications.select{ |a| a.provider == "facebook" }.any? %>
  <%= link_to_function image_tag("facebook_64.png", :size => "64x64", :alt => "Facebook"), 'fblogin()' %>
<% end %>
<!--
<a href="/auth/google_apps" class="auth_provider">
  <%= image_tag "google_64.png", :size => "64x64", :alt => "Google" %>
  Google
</a>
-->

<div class="clear"></div>
```

<p>Let's pretty this up a little with some CSS:</p>

```sass app/stylesheets/authentications.css.scss
.authentications {
  margin-bottom: 30px;
}

.authentication {
  width: 130px;
  float: left;
  background-color: #EEE;
  border: solid 1px #999;
  padding: 5px 10px;
  -moz-border-radius: 8px;
  -webkit-border-radius: 8px;
  position: relative;
  margin-right: 10px;
}

.authentication .remove {
  text-decoration: none;
  position: absolute;
  top: 3px;
  right: 3px;
  color: #333;
  padding: 2px 4px;
  font-size: 10px;
}

.authentication .remove:hover {
  color: #CCC;
  background-color: #777;
  -moz-border-radius: 6px;
  -webkit-border-radius: 6px;
}

.authentication img {
  float: left;
  margin-right: 10px;
}

.authentication .provider {
  font-weight: bold;
}

.authentication .uid {
  color: #666;
  font-size: 11px;
}

.auth_provider img {
  display: block;
}

.auth_provider {
  float: left;
  text-decoration: none;
  margin-right: 20px;
  text-align: center;
  margin-bottom: 10px;
}
```

<span class="step">Step 3: Putting it all together</span>

<p>First, the above step created some cruft in your routes that will make you
unhappy later.  Remove the line that says <code>get
"authentications#index"</code> from your routing file.  Your route file should contain 
a trace of the authentications you plan on dealing with.  Use this snippet:</p>

```ruby config/routes.rb
  resources :authentications

  match 'auth/:provider/callback', to: 'authentications#create', via: [:get, :post]
  match 'auth/failure', to: redirect('/'), via: [:get, :post]
```



<p>Ensure that your Facebook JavaScript is loaded into the asset pipeline:</p>

```coffeescript app/assets/javascripts/application.js
//= require facebook
```

<p>Ensure that your authentications CSS is loaded into the asset pipeline:</p>

```sass app/assets/stylesheets/application.css.scss
@import "authentications";
```

<p>Include a link to social logins to your already logged in accounts:</p>

```erb app/views/layouts/application.html.erb
<%= link_to "Social Accounts", authentications_path %>
```

<p>Download some Facebook icons:</p>

```bash Terminal
curl -o app/assets/images/facebook_32.png https://www.evernote.com/shard/s1/sh/c3303305-ff8f-4829-a315-9ee91709f479/49b3985624af8fb0cae8e3223333c61a/deep/0/facebook_32.png
cp app/assets/images/facebook_32.png app/assets/images/facebook_64.png
```

<p>You can use Facebook to let people create new accounts, but that's left as an
exercise to the reader!</p>

<span class="step">Step 4: Boot it up</span>

<p>Issue a command to start your server:</p>

```bash Terminal
bundle exec foreman start
```

<p>Since setting environment variables is important to the application running
properly, <code>rails s</code> probably won't work any longer!  Foreman will put
us in good position to manage environment variables (and pull user social
graphs via Sidekiq later!)</p>

<p>You should be able to click through to the 

<h3>Acknowledgements:</h3>

<p>Many of the file contents are avialable in <a href="https://gist.github.com/bigfleet/7088190">this gist</a>.</p>

<p>The amazing RailsCasts series provided not <a href="http://railscasts.com/episodes/235-omniauth-part-1">one</a> but <a href="http://railscasts.com/episodes/360-facebook-authentication">two</a> pieces of this finished puzzle.  Thanks, Ryan!</p>

<p>This StackOverflow post on <a href="http://stackoverflow.com/questions/11597130/omniauth-facebook-keeps-reporting-invalid-credentials">invalid_credentials in Omniauth-facebook</a> pointed out the need to use a particular omniauth-facebook release.  Another StackOverflow post pointed out the need to <a href="http://stackoverflow.com/questions/12370056/omniauth-strategies-facebook-noauthorizationcodeerror-must-pass-either-a-code">send a signed_request parameter with the GET to the Facebook SDK</a>.  That's incorporated into the above JavaScript.</p>





