---
layout: :post
title: Create a Blog With Clojure and Cryogen
comments: true
---
 
I wanted to create this blog with Clojure and ["Cryogen"](http://cryogenweb.org/) fit the bill perfectly. Its moto succinctly states its intention "Static sites generated with Clojure". The steps below are derived from ["Practical.li - Quick Start Guide"](https://practical.li/blog/posts/2016-01-07-docs/)

## Getting Started

### Creating the Repository
The first step is to create a cryogen repository, leningen will do this for you with:

```
lein new cryogen my-new-blog
```

### Running
You can run the `my-new-blog` as a standalone server:
```
lein ring server
```
The page is accessible via [http://localhost:3000/blog](http://localhost:3000/blog) , it provides some very useful cryogen reference information.

### Generating the Content
You can generate the static html content via:
```
lein run
```
The output is written to the `public/` directory

## Configuration

The main configuration file is `content/config.edn`. The main site name can be configured here. Another element you may want to change is the url prefixes.

## Content Creation

The default location for posts is `content/md/posts` for posts, and `content/md/pages` for pages. The default markup engine is Markdown, however you can change to Asciidoc if you so desire.

## Deployment

### Nginx 
Nginx can serve your generated content. Details [here](http://cryogenweb.org/docs/deploying-with-nginx-VPS.html)

