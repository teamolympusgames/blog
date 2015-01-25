---
layout: post
title:  "Building with Travis"
categories: blogging
---

As I mentioned [last time]({% post_url 2015-01-13-catchup %}), static-html blogging process is a lot like software development: build, test, deploy. I started wondering if there were a way to use hosted build tools to automatically build and deploy the website to S3. Turns out the Jekyll docs actually have a page on how to do [Continuous Integration with Travis!](http://jekyllrb.com/docs/continuous-integration/)

After a bit of Googling, I found [this page](http://www.paperplanes.de/2013/8/13/deploying-your-jekyll-blog-to-s3-with-travis-ci.html) that describes, step-by-step, exactly what I had to do! I did have a couple of oops moments:

1. You need a file literally named _Gemfile_ in the root of your repo. That's what the article means by "the Gemfile," and it is used by the _bundler_ utility to install the pre-req gems on the build instance
2. I didn't properly copy/paste the travis command to add secure environment vars to my travis yaml. Be sure to include the "--add env.global" bit.

Otherwise, very straight forward! All I have to do now, to publish a post, is to push the changed file to Github. And right this very instant, I'm going to try editing it via the Github web UI, to see if my changes get published...
