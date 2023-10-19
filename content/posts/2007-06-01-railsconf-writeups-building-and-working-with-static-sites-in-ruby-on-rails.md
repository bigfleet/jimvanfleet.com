---
layout: post
title: ! 'RailsConf Writeups: Building and Working with Static Sites in Ruby on Rails'
tags:
- Tech
- RailsConf
status: publish
type: post
published: true
Date: 2007-06-01
---
Ben Scofield, who I had not met, works with Patrick Reagan, who I have.  Combined with the fact that almost every Rails site that I have written has some amount of static content, I was interested to see the talk.</p>

In the style of Bob Martin's talk early in the day, Ben's presentation dealt with a progression of potential solutions to the problem of handling static material within Rails.  The first solutions were very greasy!  Check out this potential security hole:</p>

```ruby
def show
  page_path = params[:path].join('/')
  if File.exists?("#{RAILS_ROOT}/app/views/static/#{page_path}.rhtml")
    render :template => "static/#{page_path}"
  end
end
```

Obviously, that was from phase one.  In the end, they end up with a solution of some elegance!


I don't want to short-change Ben here, but I would like to give a better writeup when he comes to speak at CVREG in the coming months.