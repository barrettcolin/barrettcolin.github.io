---
layout: post
title: "Ubuntu backporting using apt-src"
categories: linux
---

A worked example, backporting cmake from Ubuntu 12.10 (quantal) to Ubuntu 12.04 (precise). You'll need to install apt-src using your package manager of choice.

### Add the source deb repository

Create an apt source list (the name isn't important, but I gather it must have a .list extension):

```
sudoedit /etc/apt/sources.list.d/quantal.list
```

and add the following line (edit to taste):

```
deb-src http://ie.archive.ubuntu.com/ubuntu quantal main universe multiverse restricted
```

Then update apt-src:

```
sudo apt-src update
```

### Get source and build

You don't have to be root to build; just make a directory, say:

```
mkdir ~/quantal-backports && cd ~/quantal-backports
```

Install source:

```
apt-src install cmake | tee apt-src-install.log
```

And build: 

```
apt-src build cmake | tee apt-src-build.log
```

### Install packages

Assuming no errors, the output of the build process is one or more .deb packages. Install them like so:

```
sudo dpkg -i cmake*.deb
```

And you're done! (Well, maybe dpkg fails because of missing dependencies; in that case, apt-get those manually, or read the Debian docs about 'Using APT locally')

