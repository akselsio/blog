---
layout: post
title: "Raspberry Pi email LED notifier"
description: "Create a Raspberry email LED notifier in less than 30 minutes."
tags: [node, raspberrypi, js, email, diy]
---

# What do you need ?

- x1 breadboard
- x2 jumper (wire) (male/female)
- x1 led
- x1 330Ω resistor
- x1 Raspberry Pi (v3 prefered)

{% include sideBySideImages.html
  path1="raspberry/breadboard.jpg" path1-detail="raspberry/breadboard@2x.jpg" alt1="Breadboard"
  path2="raspberry/jumpers.jpg" path2-detail="raspberry/jumpers@2x.jpg" alt2="Jumper wires"
%}
{% include sideBySideImages.html
  path1="raspberry/led.jpg" path1-detail="raspberry/led@2x.jpg" alt1="LED"
  path2="raspberry/resistor.jpg" path2-detail="raspberry/resistor@2x.jpg" alt2="Resistor"
%}

------------
<br />
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

> <small>__protip__: led direction matters - but you won't burn your house down if you have misplaced it</small>

<br />

###### Connecting jumpers to your Raspberry

<br />
{% include image.html path="raspberry/pin_layout.png" path-detail="raspberry/pin_layout@2x.png" alt="Our set up" %}
<br />
- __blue jumper :__ GND PIN
- __red jumper :__ GPIO24 PIN

###### Testing your setup

<br />

If you are not sure about your setup, or if you are not sure about the positioning of your led, you can easily test it.

Disconnect the __red jumper__ from the Raspberry, connect to the power supply your Raspberry Pi.
Plug in the __red jumper__ into the 3.3V or the 5V pin briefly.

{% include sideBySideImages.html
  path1="raspberry-pi-email-notification/schema.jpg" path1-detail="raspberry-pi-email-notification/schema@2x.jpg" alt1="Testing your setup 1)"
  path2="raspberry-pi-email-notification/test-schema.jpg" path2-detail="raspberry-pi-email-notification/test-schema@2x.jpg" alt2="Testing your setup 2)"
%}

Led lights up ? All good.
No ? Reverse your led.<br/>
Plug the red jumper back to GPIO24.

------------
<br />
# (very) Little programming
[source here](https://github.com/akselsio/raspberry-pi-email-notification/){:target="_blank"}

> assuming that:
>
> you have basic knowledge of npm, a shell, nodejs
>
> npm >= 3
>
> node >= 4

#### Dependencies

- [config](https://github.com/lorenwest/node-config){:target="_blank"} 1.24.x
- [onoff](https://github.com/fivdi/onoff){:target="_blank"} 1.1.x
- [imap](https://github.com/mscdex/node-imap){:target="_blank"} 0.8.x
- [gpio-misc](https://github.com/akselsio/gpio-misc-node){:target="_blank"}: 0.0.1


Open your favorite term and start a new npm project and install these dependencies.

{% highlight shell %}
$ npm init
$ npm i --save --save-exact config@1.24.0 onoff@1.1.x \
  imap@0.8.x gpio-misc@0.0.1
{% endhighlight %}

`imap` is here to retrieve information from our mailbox

`config` to handle configuration files.

`gpio-misc` to make the led flash -- a small package I wrote, [source here](https://github.com/akselsio/gpio-misc-node/blob/master/src/blink/index.js){:target="_blank"}.

`onoff` is a dependency of _gpio-misc_, it's used to handle the communication between our little program and the raspberry's GPIOs.<br />
**You should read installation instruction [here](https://github.com/fivdi/onoff#installation){:target="_blank"}.**


#### Configuration

Let's create a `config` folder and create a `default.json` file inside.

{% highlight json %}
{
  "auth": {
    "email": "youremail@gmail.com",
    "password": "yourpassword"
  },
  "imap": {
    "host": "imap.gmail.com",
    "port": 993,
    "tls": true
  }
}
{% endhighlight %}
default.json

Use the same structure, but fill it with your information of course :)<br/>
The imap configuration for Gmail/Inbox is correct. If you use another mail service, such as <small>[Outlook](https://support.office.com/en-us/article/POP-and-IMAP-settings-for-Outlook-Office-365-for-business-7fc677eb-2491-4cbc-8153-8e7113525f6c){:target="_blank"},
<small>[Yahoo](https://help.yahoo.com/kb/SLN4075.html){:target="blank"},
<small>[Aol](https://www.lifewire.com/what-are-aol-mail-imap-settings-1170847){:target="blank"}
</small>
</small>
</small>
,you'll have to change this section also.


<br />
#### Creating your server
<br />
- Require Imap, to create the connection to our mailbox. <br />
config to retrieve our variables previously set in default.json. <br />
blink module from gpio-misc to make the led.. blink, you've guessed.

{% highlight js %}
var Imap = require('imap');
var config = require('config');
var blink = require('gpio-misc').blink;
{% endhighlight %}

- create an IMAP object, which can handle the connection to our mailbox, but also events
such as receiving a new mail

{% highlight js %}
// Create an IMAP object
var imap = new Imap({
  user: config.get('auth.email'),
  password: config.get('auth.password'),

  host: config.get('imap.host'),
  port: config.get('imap.port'),
  tls: config.get('imap.tls'),
});
{% endhighlight %}

- once the connection is successful to your email service, we'll open your inbox called __INBOX__ (the name of the inbox may change if you use a service other than gmail)
{% highlight js %}
// Open your Inbox
imap.once('ready', () => {
  imap.openBox('INBOX', true, () => {
    console.log(`successfully connected to ${config.get('auth.email')}`);
  });
});
{% endhighlight %}

- we'll print errors, quite useful for debugging purposes
{% highlight js %}
// Display errors
imap.once('error', err => {
  console.error(`error: ${err.textCode}`);
});
{% endhighlight %}

- remember you connected your LED on GPIO24 ? well when we will receive a mail, we will make blink this one, [42](http://goo.gl/xPe7W8){:target="_blank"} times

{% highlight js %}
// On new mail blink
imap.on('mail', () => {
  // Blink on GPIO24, 42 times
  blink(24,42);
})
{% endhighlight %}

- finally we'll launch or connection to our email service and wait for these events

{% highlight js %}
imap.connect();
{% endhighlight %}

------------
<br />
# Testing on your Raspberry Pi
<br />

> assuming that:
>
> node >= 4 & npm >= 3 is installed on it
>
> you have already logged into the Raspberry and configured an ssh connection

##### Find your Raspberry PI's IP address and connect

<br />
We'll run the `nmap` command with `-sn` flag wich will ping scan all the subnet range, and it'll print its hostname.
In this example __192.168.1.21__ is our Raspberry local ip.

{% highlight shell %}
# scan this subnet range
$ nmap -sn 192.168.1.0/24 | grep raspberry

# expected result
Nmap scan report for raspberrypi.home (192.168.1.21)
{% endhighlight %}

- we will create a folder where you will `scp` all our stuff to your Raspberry
{% highlight shell %}
# replace with your IP address of course
$ ssh pi@192.168.1.21

# create the folder
pi@raspberry:~ $ mkdir email-notification

# and just logout
pi@raspberry:~ $ logout
{% endhighlight %}
-  Copying our project to your Raspberry with `scp` from the root of our folder


{% highlight shell %}
scp -r . pi@raspberrypi:/home/pi/email-notification
{% endhighlight %}


<small>_nb: If you have also copied the folder **node_modules**, consider removing it on the Raspberry. Indeed, you surely have a different architecture between your Raspberry and your PC._</small>

{% highlight shell %}
# log back to your Raspberry
$ ssh pi@192.168.1.21

# go to the folder where you did your scp
pi@raspberry:~ $ cd email-notification

# install node modules
pi@raspberry:~/email-notification $ npm i

# launch your server
# (npm start if you have configured your package.json)
pi@raspberry:~/email-notification $ node server.js

{% endhighlight %}

{% include image.html path="raspberry-pi-email-notification/blink.gif" path-detail="raspberry-pi-email-notification/blink@2x.gif" alt="End result" %}

------------
<br />
# Troubleshooting
<br />

#### File system permissions issues
{% highlight shell %}
fs.js:640
  return binding.open(pathModule._makeLong(path), stringToFlags(flags), mode);
                 ^

Error: EACCES: permission denied, open '/sys/class/gpio/export'
{% endhighlight %}

If you encounter this error, 2 options:

1) messy but works: `sudo node server.js` or `sudo npm start`<br />
2) install Raspbian Jessie - from scratch not with apt-get
