---
layout: post
title: "Linux: preparing a Raspbian cross-compile root"
categories: linux
---

Follow the instructions in the [mounting a filesystem]({% post_url 2012-12-01-mounting-a-filesystem-image-the-civilized-way %}) post, then:

```
mkdir -p $HOME/raspbian/2012-10-28-wheezy-raspbian && cd $HOME/raspbian/2012-10-28-wheezy-raspbian
```

Copy files as root (the root image contains device special files that will cause problems for a regular user):

```
sudo cp -r /mnt/* .
```

Own the file hierarchy (my username is 'user' and I'm in the 'user' group):

```
sudo chown -R user:user *
```

