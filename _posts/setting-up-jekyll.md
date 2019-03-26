---
layout: post
title:  "Setup Jekyll on Github Pages"
date:   2019-04-11 -0600
categories: dev disciplines, blogging, github pages
---

So I had some growing pains figuring out how to configure Jekyll, my github pages site, and my custom domain. This is one of those scenarios where the thing itself isn't hard, but rather it's a matter of finding the "right" instructions that speak to where you are in the process.

 # Jekyll Setup
Jekyll itelf was fairly straightforward to get set up. Just follow their instruction at https://jekyllrb.com/docs/ and you shouldn't have much trouble.

# Github Pages Setup
The biggest gotcha with the Github Pages set up was that I didn't realize my repository **must** be named in the format <username>.github.io. In retrospect, this was made clear from the instructions. Hindsight, as they say, is 20/20.

I would also remind you to follow this order: 

 1. Create your github repo first 
 2. Clone it locally
 3. Run "jekyll new <directory_of_cloned_rep>"

 I ran into a few issues with GIT conflicts as I had initiated a repository first, then created one at github, then tried to merge everything. I am only at a very basic level in my git knowledge so I couldn't find my way out of that mess. Truly taking time and groking GIT is on my very long list of skills to be learned. For now, however, I'm sticking with "The Plan". 

# Github Pages Custom Domain Setup

First, make sure that you have a custom domain registered somewhere. How to do that can be easily googled so I'm making this an assumption going forward.

The following steps pertain to domains registered with bluehost. The steps should be the same in other registrars, but the field names may be named slightly differently. 

1. Perform a dig command from your domain provider against your github pages site: <username>.github.io. This will tell you what ip address ranges are used for your site.
2. Log into your domain provider and go to the DNS Settings. Set up an "A" record for each ip shown. Use a value of "@" for the Host Record/Name field.
3. Create a CName (Alias) with a Host Record of wwww and a "Points to" value of <username>.github.io.

That should take care of your domain's dns settings. These changes may take hours to propogate so be patient.

1. Go back to your repository on github. 
2. Click the settings button.
3. Scroll down until you see the text box for "Custom domain name". Enter your custom domain name (without wwww) and click save. This will add a CNAME file to your repository.
4. Open the CNAME file. You should see a line with your custom domain name. Copy and paste that line onto the next line below, but add "www." to it. Save and check in the CNAME file.

You should now be good to go. As I said earlier, give it a few hours for your DNS changes to propogate.