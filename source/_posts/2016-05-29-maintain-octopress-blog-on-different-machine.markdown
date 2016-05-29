---
layout: post
title: "Maintain Octopress Blog on Different Machine"
date: 2016-05-29 22:05:44 +0800
comments: true
categories: 
---
Sometimes I need to maintain my blog on different machine but we cannot just git clone
the github pages because it only clone the renders website into local.
This is caused by `rake setup_github_pages` 
which make `remote source` to host source code and `remote master` to host rendered pages.
<!--more-->
To get this done, we need to init git from scratch
```bash
$ mkdir <empty directory> && cd <empty directory>
$ git init 
```
Git add remote origin and pull `remote source` branch to local
```bash
$ git remote add origin <octopress git repository>
$ git pull origin source 
```
note that we need to create the local branch `source` and delete `master` to
avoid ambiguous version control.
```bash
$ git checkout -b source 
$ git branch -D master
```
Now, to eable local preview and deploy, we need to create `_deploy` folder and synced to 
`remote master`: 
```bash
$ mkdir _deploy && cd _deploy
$ git init
$ git remote add origin <octopress git repository>
$ git pull origin master
```
Now, we are ready to maintain Octopress source and deploy website on the 
other machine rather origininal one.


To update source:
```bash
$ git push origin source
```
To deploy pages:
```bash
$ rake deploy
```

