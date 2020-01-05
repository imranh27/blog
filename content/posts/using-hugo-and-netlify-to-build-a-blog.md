---
title: "Using Hugo and Netlify to Build a Blog"
date: 2019-09-02T08:27:39+01:00
draft: true
toc: false
images:
tags:
  - Hugo
  - Netlify
  - Guide
---

## Introduction

A bit of a weird one this, I intend to describe how I built this blog. What toolset I have used and how I have put this together.

The base of this blog is [Hugo](https://gohugo.io) which is a static site generator. A person would use Hugo to describe their pages in markdown and then the static pages are created from these templates.

Static pages are coming back in to fashion, originally web pages were hand built in HTML. There has been a fashion in the recent past to make web pages more dynamic so web pages have become a lot more complicated. This has made web pages.. slower.. So we have had a shift back towards static pages. Simple(r) HTML files which are, pre generated and smaller in size which makes the site quicker and more responsive.

There has been lot of talk about the JAM Stack recently, it is becoming rather fashionable, in short it is an application stack which focuses in on creating static websites. Websites which are pre-rendered markup.

The backend of this site is hosted on Github and then I am using [Netlify](https://www.netlify.com) which is a cool Continuous Integration/Continuous Delivery (CI/CD) service to actually host the blog.

The process is:

1. Create the post in markdown using Hugo.
2. Use Hugo to build the site locally.
3. Deploy the site to github.
4. Netlify then detects a change and rebuilds the blog from source.
5. A couple of minutes later... Voila!  

* Creating a post

We need to actually create the post.
```
hugo new posts/new-post-name.md
```

Then we can open the post in out mark down editor of choice. At the moment, I am using [Atom](https://atom.io).

Write your content, formatting it using markdown, there are various cheat sheets, this [one](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) I have found rather useful.

Once you have some content and you wish to check how it looks, you can build and run your blog locally.

Build the blog, this generates the HTML pages and makes it available locally.

```
hugo server -D
```
the -D argument is important, as your new post is in draft, this flag includes it so you can see it as part of your generated structure. You can preview your page in your editor, but it is good to see this working in a browser.

Navigate to to see the blog.
```
http://localhost:1313
```

Running the blog locally like this is very useful as once you save any changes to your markdown you can, refresh your browser page and the changes will be there.

Once you are happy with your post you are ready to deploy it live, Change the draft status of the page to false.

Then run hugo to build the pages, from the command line run:

```
hugo
```
* Commit to Github

Save the blog page and commit the page to github.

```
commit .
```
push the changes to Github

```
git push origin master
```

Setup Netlfiy, hugo have a great guide to do [this](https://gohugo.io/hosting-and-deployment/hosting-on-netlify/).

If all goes according to plan then Netlify will build your site and hoist it. Voila.
