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
please go to [Github user pages][Github_user_pages] to check the difference between them.
Follow [Chinese_guide][], I only present how to use Octopress to create static webpages 
with *User Page Site*. <!--More-->
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
Note taht LinuxMint 17.3 is forked form Ubuntu 14.04 LTS, and Octopress 3.0 need
Ruby 19.1+ support.
If your working environment is Ubuntu 12.04, please following
[this guide][Ubuntu1204_wit_Ruby193] to install Ruby 19.1+.
Install **Octopress** and dependend packages
-
To install packages:
```bash
$ sudo apt-get install ruby1.9.1-dev
$ sudo apt-get install nodejs
$ sudo apt-get install rbenv
$ sudo apt-get install rake
$ sudo gem install bundler
$ rbenv rehash
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
and you can go to [Octopress_deploying][]
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
Please refere to [Octopress_configuring][]
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

<!---Reference--->
[Chinese_guide]: http://wen00072-blog.logdown.com/posts/258497-octopress-installed-and-deployed-on-the-github-pages "Chinese Tutorial"
[Octopress_configuring]: http://octopress.org/docs/blogging/ "Official Website"
[Octopress_deploying]: http://octopress.org/docs/deploying/github/
[Github_user_pages]: https://help.github.com/articles/user-organization-and-project-pages/ "Github IO Page"
[Ubuntu1204_wit_Ruby193]: https://leonard.io/blog/2012/05/installing-ruby-1-9-3-on-ubuntu-12-04-precise-pengolin/

