---
layout: post
title: "Remote-launch an X11 application"
categories: linux
---

I found lots of online references to launching an X11 application remotely and viewing it locally (X11 forwarding over ssh etc), but not necessarily to launching AND viewing an X11 application remotely (consider the case of wanting to start a non-interactive graphics test app on a remote PC, which sits beside me on the desk but doesn't have a mouse or keyboard plugged in).

Turns out it's dead simple; from an ssh/bash session on the remote:

```
DISPLAY=':0' x_application_name
```

Where x_application_name is the name of your application (lxterminal is handy to test with on raspbian). Obviously you'll need to be running X on the remote device.

Come to think of it, it might be better to just do:

```
xinit /path/to/x_application_name
```

with no X server running; the 'DISPLAY=':0'' business probably only works without further fiddling if the same user started X as runs the application.

