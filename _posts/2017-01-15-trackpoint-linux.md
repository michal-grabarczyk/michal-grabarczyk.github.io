---
layout: post
title:  "Thinkpad's Trackpoint in Linux"
date:   2017-01-15 17:01:27 +0100
categories: docker spring-profile
---
## T420 TrackPoint Linux Change speed
[source]:https://bbs.archlinux.org/viewtopic.php?id=199998
Due to some unfixed bugs in psmouse driver it's not straight forward to modify trackpoint's attributes on boot.
Here you can find a workaround that worked on my T420.

* /etc/udev/rules.d/99-trackpoint.rules
{% highlight bash %}
KERNEL=="serio2", SUBSYSTEM=="serio", DRIVER=="psmouse", ATTR{speed}="200", ATTR{sensitivity}="255"
{% endhighlight %}

* /etc/systemd/system/trackpoint.service

{% highlight bash %}
[Unit]
Description=Set TrackPoint attributes

[Service]
Type=oneshot
ExecStartPre=/usr/bin/sleep 5
ExecStart=/usr/bin/udevadm trigger --subsystem-match=serio
ExecStartPost=/usr/bin/udevadm info -a -p /sys/devices/platform/i8042/serio1/serio2/

[Install]
WantedBy=multi-user.target
{% endhighlight %}

