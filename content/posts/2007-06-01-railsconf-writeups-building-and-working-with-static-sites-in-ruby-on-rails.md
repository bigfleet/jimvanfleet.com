---
layout: post
title: ! 'RailsConf Writeups: Building and Working with Static Sites in Ruby on Rails'
tags: []
status: publish
type: post
published: true
meta: {}
---
<p>Ben Scofield, who I had not met, works with Patrick Reagan, who I have.  Combined with the fact that almost every Rails site that I have written has some amount of static content, I was interested to see the talk.</p>


	<p>In the style of Bob Martin&#8217;s talk early in the day, Ben&#8217;s presentation dealt with a progression of potential solutions to the problem of handling static material within Rails.  The first solutions were very greasy!  Check out this potential security hole:</p>


<code>
<pre>
def show
  page_path = params[:path].join('/')
  if File.exists?("#{RAILS_ROOT}/app/views/static/#{page_path}.rhtml")
    render :template =&gt; "static/#{page_path}"
  end
end
</pre>
</code>

	<p>Obviously, that was from phase one.  In the end, they end up with a solution of some elegance!</p>


	<p>I don&#8217;t want to short-change Ben here, but I would like to give a better writeup when he comes to speak at <a href="http://www.cvreg.org/"><span class="caps">CVREG</span></a> in the coming months.</p>


	<p><a href="http://www.viget.com/railsconf/">Their plugin</a> is available, as are the <a href="http://culann.com/slides/Static_Site_Railsconf_2007_final.pdf">presentation slides</a>.</p>
