---
title: "Just got a refurb laptop to my collection"
excerpt: "New laptop to my collection, my first refurbished laptop"
header:
  overlay_image: /assets/blog-images/20191211_161534.jpg
categories:
  - Random
tags:
  - random
---

I just got a refurbished laptop that i ordered on Ebay a couple of weeks ago. it's a Lenovo X230 with an i7-3520m, with a 256gb ssd and 8gb of ram which i bumped already to 16gb. I decided to go for this laptop as i was pretty affordable and it was in a pretty good condition and didn't need to do a whole lot of upgrades, besides the RAM and the screen which is a TN one. Also i was looking for a lightweight option to carry to the university or anywhere easily.

When it arrived it was a bit dusty and came with a Windows 10 installed... After a cleanup of both the OS and front and back lid (still with a scratch at the front..), i went for installing a debian buster. After 10mins i got my linux up and running.

<figure>
    <a href="/assets/blog-images/natural_transformations.jpeg"><img src="/assets/blog-images/20191211_161650.jpg"></a>
</figure>

Did some tests to check the thermals and apparently i got about 49C on idle and 85C on full load, so i'll leave the repasting for next month.

i was a bit concerned about the battery, which could be a lottery ticket when buying a second hand laptop, the one it came with is a 6-cell battery 44+ lenovo one, and after running this command to check the battery status:

```bash
upower -i /org/freedesktop/UPower/devices/battery_BAT0
```

and got the following output

```
  native-path:          BAT0
  vendor:               LGC
  model:                45N1025
  serial:               74
  power supply:         yes
  updated:              Mon 09 Dec 2019 11:24:33 PM -03 (41 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    warning-level:       none
    energy:              45.65 Wh
    energy-empty:        0 Wh
    energy-full:         45.65 Wh
    energy-full-design:  57.72 Wh
    energy-rate:         2.437 W
    voltage:             12.567 V
    percentage:          100%
    capacity:            78.7422%
    technology:          lithium-ion
    icon-name:          'battery-full-charging-symbolic'
  History (rate):
    1576203873	2.437	charging
```

where apparently the capacity left on the battery is a bit les than 78.75%, which is pretty good so far. I've got about 4-5hr mark with a light use (visualstudio code + browser), so i'll probably start looking for a new 6 or 9-cell battery later on next year, for now i think i'm pretty fine with this one.

So far i'm pleased with my laptop and hope to upgrade soon, probably next month the display to an IPS one.