---
layout: post
title: "Taka - Quite a journey"
description: "A public transportation app for Nantes, France"
preview: "kfc/logo.png"
preview2x: "kfc/logo@2x.png"
previewAlt: "TAKA Preview"
tags: [poc, project, ios, android, react-native, expo]
---

# TL;DR
<br />
- A POC is not enough to ship a project, but actually the project will never be ready.
    Just ship it at some point.
- A project without a business opportunity in mind is hard to work on.
- I spent a lot of money and time but I have learned a lot - no ragrets
- Procrastination sucks

<br /><br />
# How it started
<br />

Summer 2016, move from Paris to Nantes.<br />
Fall 2016, I broke my One Plus X, then bought an iPhone 7.

> image of both phones

And a during an April 2017 lunch I was complaining about Google Maps which doesn't work in Nantes and that the TAN application is terrible and I told my coworkers:

```
(aksels)    I will code my own simple version of google
            maps for Nantes
(coworkers) rofl, too complex
```

<br />

Few days later, I'm there with my POC:

{% include image.html path="taka-quite-a-journey/taka-web-early.png" path-detail="taka-quite-a-journey/taka-web-early.png" alt="Taka WEB version early" %}

with a decent architecture orchestred on GCP Kubernetes.

> architecture

And on top of that you have 300$ credit as a welcoming gift from google to try it out.

{% include image.html path="taka-quite-a-journey/google-free-tier.png" path-detail="taka-quite-a-journey/google-free-tier.png" alt="Google Free Tier" %}


But a week later you take an AIR France plane (delayed but you are getting used to)

{% include image.html path="taka-quite-a-journey/af-delay.jpg" path-detail="taka-quite-a-journey/af-delay.jpg" alt="AF Delay" %}

and meet some friends in Singapore

{% include image.html path="taka-quite-a-journey/aksels-singapore.jpg" path-detail="taka-quite-a-journey/aksels-singapore.jpg" alt="Aksels @ Singapore early May 2018" %}

and you go with them in Vietnam, Cambodia and Thailand for a couple of weeks and take a classic selfie of someone who grew up in britanny.

{% include image.html path="taka-quite-a-journey/aksels-vietnam-bretagne.jpg" path-detail="taka-quite-a-journey/aksels-vietnam-bretagne.jpg" alt="Aksels @ Vietnam early May 2018" %}

and then you come back, your shaving cream exploded in your backpack and next day you go back to work and catch up on everything you missed.

{% include image.html path="taka-quite-a-journey/aksels-bad-luck.jpg" path-detail="taka-quite-a-journey/aksels-bad-luck.jpg" alt="Aksels @ unluck early May 2018" %}

<br />
<br />
<br />

Days are passing and.. Oh, I was talking about an app right.. 

<br />
<div style="text-align:center;"><b><u>The fun part of developing this project ended up here.</u></b></div>
{% include image.html path="taka-quite-a-journey/fun-ended-here.png" path-detail="taka-quite-a-journey/fun-ended-here.png" alt="Where is the fun part" %}


> some words about : details are important, bug free, you want to deliver a perfect ux but still it's a side project so you don't have a lot of time to invest

<br /><br />
# Mobile application

At some point <a href="https://nantes.cool" target="_blank">nantes.cool</a> was not enough. And don't even try at this point to make your users install your webapp on their phones.
<br />

{% include image.html path="taka-quite-a-journey/taka-very-responsive.gif" path-detail="taka-quite-a-journey/taka-very-responsive.gif" alt="Very responsive" %}
<br />
Oh it is reponsive right, but 99.99% (if not 100%) of your users won't install your webapp unless you tell them how to do it. I know this very well because at <a href="https://fizix.io" target="_blank">FIZIX</a> where I work we have a webapp for our personal trainers. Oh boy..

```
(pers. trainer) I can't find your app on the store
(aksels)        Well, I'll send you this PDF explaining
                how to install our application (a
                webapp) on your phone.
(pers. trainer) I give up sorry
```
<br />

Actually I'm exagerrating they don't give up - mostly because we bring them a decent amount of income, but still we have to explain each time how to do it. But once they have it on the phone everything is alright, but it couldn't work for our project.

<br /><br />
# What are the other app alternatives ?

Why are we even trying to create an app ?<br />
To know how to get around Nantes you have two main options (on iPhone):

> talk about naoned

### Google Maps

Which doesn't work for public transportation in Nantes. It will offer you two choices:
- grab an Uber
- walk by foot

{% include image.html path="taka-quite-a-journey/google.jpg" path-detail="taka-quite-a-journey/google.jpg" alt="Google Maps." %}

### TAN

{% include image.html path="taka-quite-a-journey/tan-preview.jpg" path-detail="taka-quite-a-journey/tan-preview.jpg" alt="TAN Preview" %}


It may seem a little bit harsh but:
- ￼❌ ￼it is slow
- ❌ the UI is more than outdated
- ❌ it doesn't work 100% of the time
- ❌ don't expect any updates

The only thing that prevents user from uninstalling this app is that it allows you to buy dematerialized tickets.

# Native app development


### Cross-Platform 

We need a cross-platform app because Android users have a wonderful unofficial-app for public transportations : Naoned. It's clean, it works and it has 10 years of development behind it. It's written in Java, no chance to get it on iOS anytime soon.

So I heard you wanted to create a cross-platform native app, choose between:
- react-native
- flutter
- xamarin
- ionic, cordova, phonegap
- NativeScript
- expo (which is on top of react-native)

And this is how I made my choice:

- react-native
    - I have 4 years of experience in React development, LGTM
- flutter
    - no maps (fixed 29 nov 2018)
- xamarin
    - .NET, I pass
- ionic and cie
    - I don't want my website in a webview
- NativeScript
    - I don't like Angular
- expo
    - react-native but without the headache : ok, <u>that's the best choice</u>


### Google API

rip

### Algolia

yeah

### You are probably not a designer

<br />
{% include image.html path="taka-quite-a-journey/taka-mobile-app-first-release.png" path-detail="taka-quite-a-journey/taka-mobile-app-first-release.png" alt="Taka mobile app first release" %}

Beautiful isn't it ?

We are here :

{% include image.html path="taka-quite-a-journey/taka-activity-first-poc.png" path-detail="taka-quite-a-journey/taka-activity-first-poc.png" alt="TAKA activity graph" %}

What happened during the following months ? Oh yes, absolutly nothing.
Why ? Because your app works but it is ugly AF but in the same time you don't want to spend to much time on design because... you are not a designer and it's not something you like that much. In the meantime you started a bunch of another projects and they are way more interesting than finishing this.

### GCP

I've talked about free tier right ?

7 months later..

{% include image.html path="taka-quite-a-journey/gcp-outch.png" path-detail="taka-quite-a-journey/gcp-outch.png" alt="GCP is expensive" %}

Oh yeah, that's <b>330 euros</b> from your pocket only for having a fancy orchestration for your side project. But at least you know how to do handle apps over Kubernetes and you made it to your day-to-day work and that's something.

In that price is included GCP Load balancer (ingress):

{% include image.html path="taka-quite-a-journey/google-loadbalancing.png" path-detail="taka-quite-a-journey/google-loadbalancing.png" alt="GCP is very expensive" %}

Yes, <b>127 euros</b> for forwarding your requests.<br />
How many users ? Let's ask Google Analytics:

{% include image.html path="taka-quite-a-journey/google-analytics-2018.png" path-detail="taka-quite-a-journey/google-analytics-2018.png" alt="GCP is very very expensive" %}

<b>102 users</b>, probably 80% of this visits are myself.

<div style="text-align:center;">
That's <b>1.24 euros per visit of load balancing</b>. Worth it.
</div>

### OVH

cheaper







# Actually you don't even use your own app

because public transportation are terrible here and you are way faster with your ES2.

> they see me rolling

<br /><br /><br />
