---
layout: post
title: "Raspberry Pi email notifier"
description: "Create a Raspberry email led notifier in less than 30 minutes."
tags: [node, raspberrypi, js, email, diy]
---

# What do you need ?

- x1 breadboard
- x2 jumper (wire) (male/female)
- x1 led
- x1 330Ω resistor
- x1 Raspberry Pi (v3 prefered)

{% include sideBySideImages.html
  path1="raspberry-pi-email-notification/breadboard_empty.png" path1-detail="raspberry-pi-email-notification/breadboard_empty@2x.png" alt1="breadboard"
  path2="raspberry-pi-email-notification/breadboard_empty.png" path2-detail="raspberry-pi-email-notification/breadboard_empty@2x.png" alt2="breadboard"
%}
{% include sideBySideImages.html
  path1="raspberry-pi-email-notification/breadboard_empty.png" path1-detail="raspberry-pi-email-notification/breadboard_empty@2x.png" alt1="breadboard"
  path2="raspberry-pi-email-notification/breadboard_empty.png" path2-detail="raspberry-pi-email-notification/breadboard_empty@2x.png" alt2="breadboard"
%}
{% include image.html path="raspberry-pi-email-notification/breadboard_empty.png" path-detail="raspberry-pi-email-notification/breadboard_empty@2x.png" alt="breadboard" %}

<br/>
# Hardware setup

> <small>__warning__: don't plug your Raspberry in.</small>

###### The breadboard
Little explanation on how a breadboard works.

{% include image.html path="raspberry-pi-email-notification/breadboard_empty.png" path-detail="raspberry-pi-email-notification/breadboard_empty@2x.png" alt="breadboard" %}

Actually it's quite simple. Usually there are four rows, two negative and two positive and a bunch of columns.
All the holes in a row are connected, same for the rows.

Easy.

###### Setting up your circuit

<br />
{% include image.html path="raspberry-pi-email-notification/breadboard_pi_led.png" path-detail="raspberry-pi-email-notification/breadboard_pi_led@2x.png" alt="Our set up" %}

<br />
I advise you at first to follow my schema and then experiment by yourself. <br/>
Don't connect anything for the moment to the Raspberry.
<br/>

- __red jumper :__ to a random column
- __blue jumper :__ to a __(-)__ row
- __resistor :__ to the same __(-)__ row where we connected our blue jumper and to a column _(direction does not matter)_
- __led :__ one leg in the __resistor column__ and one in the __red jumper__ one's

<br />

> <small>__protip__: led direction matters - but you won't burn your house down if you have misplaced it.</small>

<br />

###### Connecting jumpers to your Raspberry

<br />
{% include image.html path="raspberry/pin_layout.png" path-detail="raspberry/pin_layout@2x.png" alt="Our set up" %}
<br />
- __blue jumper :__ GND PIN
- __red jumper :__ GPIO24 PIN

###### Testing your setup

<br />
{% include image.html path="raspberry-pi-email-notification/breadboard_pi_led.png" path-detail="raspberry-pi-email-notification/breadboard_pi_led@2x.png" alt="Our set up" %}

If you are not sure about your setup, or if you are not sure about the positioning of your led, you can easily test it.

Disconnect the __red jumper__ from the Raspberry, connect to the power supply your Raspberry Pi.
Plug in the __red jumper__ into the 3.3V or the 5V pin briefly.

Led lights up ? All good.
No ? Reverse your led.<br/>
Plug the red jumper back to GPIO24.

# (very) Little programming

#### This is a title:
  - with a list
  - with items
