---
layout: post
title: Setup a Blog in Two Minutes with Jekyll, Docker, Github Pages and Poole
comments: true
---

Having previously created this site using Clojure and Cryogen, I wanted to remove the bother of having to host the site myself and to make updates as easy as possible. [Github Pages](https://pages.github.com/) addresses both of these concerns by both hosting the static content and allowing updates to be built and pushed from a Github repository. 

Initially I wanted to setup Jekyll locally on linux via installing the gem, however I was not successful due to missing dependencies. Instead of battling with the gem installation, the following was the quickest path for me to get a site deployed.

### Repository Creation

[Poole](https://github.com/poole/poole) is the repository I chose to use as a basis for my Jekyll site as it provides many sensible defaults. In Github, create a fork of the poole repository and name it **your-github-user-name-here.github.io** ([mickrideout.github.io repository](https://github.com/mickrideout/mickrideout.github.io) in my case)

Enter your new repository and click on the **Actions** tab at the top. The will show you when Github has finished building your Jekyll site. Once the repository has built successfully, your new site will be available at https://your-github-user-name-here.github.io (eg [mickrideout.github.io](https://mickrideout.github.io/))

### Local Server

Now that you have a Github Pages site, you may want to modify it and run a local server to see that your changes are good before publishing the site. To do this I used a docker version of [Jekyll](https://hub.docker.com/r/jekyll/jekyll/)

Firstly, clone your Github Pages repository.
Then do a docker pull for Jekyll
{% highlight bash %}
docker pull jekyll/jekyll
{% endhighlight %}

From the root directory of your repository, run the Jekyll server

{% highlight bash %}
docker run --rm \
  --volume="$PWD:/srv/jekyll" \
  --publish [::1]:4000:4000 \
  jekyll/jekyll \
  jekyll serve
{% endhighlight %}

You can now view your site at [http://localhost:4000](http://localhost:4000)

Jekyll will detect page saves and reload the content. All that's left to do now is to mould the site in your own image.



