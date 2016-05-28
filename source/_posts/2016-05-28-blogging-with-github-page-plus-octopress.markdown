---
layout: post
title: "Blogging with Github Page + Octopress"
date: 2016-05-28 12:05:14 +0800
comments: true
categories: General 
---

Greate *User Pages site*
-
Note that *User Pages site* and *Project Pages* are different,
please go to this link
[Github io page](https://help.github.com/articles/user-organization-and-project-pages/)
to check the difference between them.
In this tutorial, I only present how to use Octopress to create static webpages 
with *User Page Site*. [[MORE]]

Envronment Check
-
```bash
$ lsb_release -a
```
and here is my working envrionment
```
LSB modules are available.
Distributor ID:	LinuxMint
Description:	Linux Mint 17.3 Rosa
Release:	17.3
Codename:	rosa
```
Install **Octopress** and dependend packages
-
To install packages:
```bash
$ sudo apt-get install ruby1.9.1-dev
$ sudo apt-get install nodejs
$ sudo apt-get install rebenv
$ sudo apt-get install rbenv
$ sudo gem install bundler
$ rbenv rebash
```
To install **Octopress**
```bash
$ git clone https://github.com/imathis/octopress 
$ cd octopress
$ rake install
$ bundle install 
```
To init **Octopress** with User Page Site 
-
You need to provide **Github IO** URL during this command execution, 
and please make sure the URL you provide should be look like this:
`https://github.com/<username>/<username>.github.io.git`

```bash
$ rake setup_github_pages
```
and you can go to [official pages](http://octopress.org/docs/deploying/github/)
to check what have been down when setting up **Github IO** URL. 
Now you can generate and deploy the static pages:
```bash
$ rake generate
$ rake deploy
```
This step will genenrate html css files and put them into this folder `_deploy`.
Remember that the command `setup_github_pages` has replaced `git remote origin`
with `source` so the whole project now is dis-linked to the official Octopress 
repository, and now it's managed by you own repository's branch `source`.
Meanwhile, `master` now is to manage the rendered webpages which will be shown
in **Github IO** user pages.  
To make sure this has bee done, please check the current branch:
```bash
$ git branch 
```
and you should see:
```
* source
```
Now you are good to commit all the things have been changed:
```bash
$ git add .
$ git commit -m 'your message'
$ git push origin source
```
Configure **Octopress**
-
Please refere to [Configuring Octopress](http://octopress.org/docs/configuring/)
to see all the details, and I only change the tile, author, username...etc here.
Please edit `_config.yml`:
```
url: http://<username>.github.io
title: <your title> 
subtitle: <your subtitle> 
author: <your author name> 
simple_search: https://www.google.com/search
description: Note for everything
```
First Post
-
To create a new post:
```bash
$ rake new_post["<post title>"]
```
then a new markdown file will be generated in this place `source/_posts`.
You can preview the post locally with this command:
```bash
$ rake preview
```
and the local preview URL is avaiable here `localhost:4000`, you can simply
close it with `ctrl+c`. To deploy the posts, use this command:
```bash
$ rake deploy
```
Now everything is good to go.
Reference
-
* [Chinese Tutorial](http://wen00072-blog.logdown.com/posts/258497-octopress-installed-and-deployed-on-the-github-pages)
* [Chinese Tutorial](http://zerodie.github.io/blog/2012/01/19/octopress-github-pages/)
* [Official Website](http://octopress.org/docs/blogging/)
* [Github IO Page](https://help.github.com/articles/user-organization-and-project-pages/)
