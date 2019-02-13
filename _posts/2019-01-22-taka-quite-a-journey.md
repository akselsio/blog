---
layout: post
title: "Taka - Quite a journey"
description: "A public transportation app for Nantes, France"
preview: "taka-quite-a-journey/taka-preview.png"
preview2x: "taka-quite-a-journey/taka-preview.png"
previewAlt: "TAKA Preview"
tags: [poc, project, ios, android, react-native, expo, go]
---

# TL;DR
<br />

- A POC is not enough to ship a project, but actually the project will never be ready.
    Just ship it at some point
- A project without a business opportunity in mind is hard to work on
- I spent a lot of money and time, but I have learned a lot - no ragrets
- Procrastination is terrible

<br /><br />
# How it started
<br />

I'm the kind of guy that have a ton of side projects ideas. Which range from far too ambitious to pointless.

During a late April 2017 lunch I was complaining about Google Maps which doesn't work in Nantes and that the TAN application is terrible and I told my coworkers:

```
(aksels)    I will code my own simple version of google
            maps for Nantes
(coworkers) rofl, too complex
```

<br />

A few days later, I'm there with my POC:

{% include image.html path="taka-quite-a-journey/taka-web-early.png" path-detail="taka-quite-a-journey/taka-web-early.png" alt="Taka WEB version early" %}

with a decent architecture orchestrated on GCP Kubernetes.

{% include image.html path="taka-quite-a-journey/first-architecture.png" path-detail="taka-quite-a-journey/first-architecture.png" alt="Archicture" %}

<br /><br />
Why Google Cloud Platform?<br />
You have 300$ credit as a welcoming gift from Google to try it out. Perfect for a side project, isn't it?

{% include image.html path="taka-quite-a-journey/google-free-tier.png" path-detail="taka-quite-a-journey/google-free-tier.png" alt="Google Free Tier" %}

<br /><br />
However, a week later you take an AIR France plane (delayed, but you are getting used to)..

{% include image.html path="taka-quite-a-journey/af-delay.jpg" path-detail="taka-quite-a-journey/af-delay.jpg" alt="AF Delay" %}

..and you meet some friends in Singapore..

{% include image.html path="taka-quite-a-journey/aksels-singapore.jpg" path-detail="taka-quite-a-journey/aksels-singapore.jpg" alt="Aksels @ Singapore early May 2018" %}

..and you ride next to paddy fields in Vietnam..

{% include image.html path="taka-quite-a-journey/aksels-vietnam.jpg" path-detail="taka-quite-a-journey/aksels-vietnam.jpg" alt="Aksels @ Vietnam early May 2018" %}

..and you go with them in Cambodia and Thailand for a couple of weeks. Finally you wait your flight back home, being more tired than at the beginning of the holidays..

{% include image.html path="taka-quite-a-journey/aksels-thailand.jpg" path-detail="taka-quite-a-journey/aksels-thailand.jpg" alt="Aksels @ Thailand early May 2018" %}

..and then you come back to home, your shaving cream exploded in your backpack and next day you go back to work and catch up on everything you missed.

{% include image.html path="taka-quite-a-journey/aksels-bad-luck.jpg" path-detail="taka-quite-a-journey/aksels-bad-luck.jpg" alt="Aksels @ unluck early May 2018" %}

<br />
<br />
<br />

Days are passing and.. Oh, I was talking about a side-project right..

You see the point? It's easy to break your workflow and motivation. It's all about keeping the momentum.

<br />
<div style="text-align:center;"><b><u>The fun part of developing this project ended up here.</u></b></div>
{% include image.html path="taka-quite-a-journey/fun-ended-here.png" path-detail="taka-quite-a-journey/fun-ended-here.png" alt="Where is the fun part" %}

I mean, if the Github's activity graph had a legend it would be:

{% include image.html path="taka-quite-a-journey/activity-graph-fixed.png" path-detail="taka-quite-a-journey/activity-graph-fixed.png" alt="Activity graph" %}

The fun part was looking how a GTFS Server works, implementing a Go API, bootstraping a Vue web application. And then you ask yourself:

```
Can I communicate about this now?
or is this too early?

There are so many things I could improve,
users will be disappointed if I ship this.
```

<br />
The lesson I learned from this side project it's that you won't have enough time. That's your day-to-day job to ship perfect things, but you have 10 hours a day you can dedicate to improve your product. On the other hand, your side project which certainly doesn't have a bright future will not bring enough motivation to work on.

The most effective thing to do is to set on your calendar a 45min window each day (or a few days per week or even per month) where you can work on personal projects. IMHO, 30min is too short, meanwhile 1h is great, but it's too long, it mostly depends on your lifestyle.

Also, forget your long coding sessions after work once you've moved in with someone. You won't be able to eat something quickly and get your hands-on your computer right after your work day. I can't imagine when you have a baby home, maybe the key is to get up before everyone else and find your time window during their sleeps.

<br /><br />
# Mobile application

I've shown my app to some relatives, friends and either they didn't show any interest or they pretended some, but no one will ever use this website. The truth is that you don't go on a website when you are on the go. You launch an app, check next bus / tramway and then leave. You won't open your computer to check the journey for your daily commute.

At some point <a href="https://nantes.cool" target="_blank">nantes.cool</a> was not enough. Don't even try at this point to make your users install your webapp on their phones.

<br />


{% include image.html path="taka-quite-a-journey/taka-very-responsive.gif" path-detail="taka-quite-a-journey/taka-very-responsive.gif" alt="Very responsive" %}
<br />
Oh it is responsive right, but 99.99% (if not 100%) of your users won't install your webapp unless you tell them how to do it. I know this very well because at <a href="https://fizix.io" target="_blank">FIZIX</a> where I work we have a webapp for our personal trainers. Oh boy..

```
(pers. trainer) I can't find your app on the store
(aksels)        Well, I'll send you this PDF explaining
                how to install our application (a
                webapp) on your phone.
(pers. trainer) I give up sorry
```
<br />

Actually I'm exaggerating they don't give up - mostly because we bring them a decent amount of income, but still we have to explain each time how to do it. However, once they have it on the phone everything is alright, but it couldn't work for our project.

<br /><br />
## What are the other app alternatives?

Why are we even trying to create an app?<br />
To know how to get around Nantes you have two main options (on iPhone):

### **Google Maps**

Which doesn't work for public transportation in Nantes. It will offer you two choices:

- walk by foot
- get an Uber ride

{% include image.html path="taka-quite-a-journey/google.jpg" path-detail="taka-quite-a-journey/google.jpg" alt="Google Maps." %}

### TAN

{% include image.html path="taka-quite-a-journey/tan-preview.jpg" path-detail="taka-quite-a-journey/tan-preview.jpg" alt="TAN Preview" %}

It may seem a little bit harsh but:

- ￼❌ ￼it is slow
- ❌ the UI is more than outdated
- ❌ it doesn't work 100% of the time
- ❌ don't expect any updates

The only thing that prevents user from uninstalling this app is that it allows you to buy dematerialized tickets.

<br /><br />
# Development adventures
## Cross-platform mobile app

We need a cross-platform app because Android users have a wonderful unofficial-app for public transportation : NaonedBus. It's clean, it works and it has 10 years of development behind it. But it's written in Java, no chance to get it on iOS any time soon.

So, I heard you wanted to create a cross-platform native app, choose between:

- react-native
- flutter
- xamarin
- ionic, cordova, phonegap
- NativeScript
- expo (which is on top of react-native)

And this is how I made my choice:

- <b>react-native</b> I have 4 years of experience in React development, LGTM
- <b>flutter</b> no maps (fixed 29 nov 2018)
- <b>xamarin</b> .NET, I pass
- <b>ionic and cie</b> I don't want my website in a webview
- <b>NativeScript</b> I don't like Angular
- <b>expo</b> react-native but without the headache : ok, <u>that's the best choice</u>

<br /><br />
## After that, we need to compute our journeys

Open Trip Planner seems to be the most popular solution.

It:

- ✔️ has a documentation
- ✔️ <a href="http://docs.opentripplanner.org/en/latest/Deployments/" target="_blank">seems to be used by many in production</a>
- ✔️ is <a href="https://github.com/opentripplanner/OpenTripPlanner" target="_blank">open source</a>
- ￼❌ ￼is written in JAVA, but no one can be perfect after all
- ￼❌ has many issues
- ✔️ seems in active development


<br /><br />
## Next, we need a Geocoding API

When the users search for an address we need to translate it in coordinates.

{% include image.html path="taka-quite-a-journey/location-search.gif" path-detail="taka-quite-a-journey/location-search.gif" alt="Location search illustration" %}

### Google API

Let's read the <a href="https://www.google.com/intl/fr_US/help/terms_maps.html" target="_blank">TOS of Google's APIs</a>.

{% include image.html path="taka-quite-a-journey/tos.gif" path-detail="taka-quite-a-journey/tos.gif" alt="Google TOS scrolling" %}

Just kidding, here the part which interests us:

```
2. Prohibited Conduct. When using Google Maps/Google Earth,
you may not (or allow those acting on your behalf to):

[...]
d. use Google Maps/Google Earth to create or augment any
other mapping-related dataset (including a mapping or
navigation dataset, business listings database, mailing
list, or telemarketing list) for use in a service that
is a substitute for, or a substantially similar service to,
Google Maps/Google Earth;
[...]
```

<b>"a substantially similar service to, Google Maps"</b>, well our App is quite similar to Google Maps.

{% include image.html path="taka-quite-a-journey/taka-vs-google.png" path-detail="taka-quite-a-journey/taka-vs-google.png" alt="Taka vs Google" %}
{% include image.html path="taka-quite-a-journey/taka-vs-google-2.png" path-detail="taka-quite-a-journey/taka-vs-google-2.png" alt="Taka vs Google" %}

It is even better in our use case. But they look quite <small><small>a lot</small></small> the same, agreed.

We <u>cannot</u> use Google APIs in our project.

<br /><br />
### Alternative: Algolia

{% include image.html path="taka-quite-a-journey/algolia.svg" path-detail="taka-quite-a-journey/algolia.svg" alt="Algolia logo" %}

It has a free plan designed especially for our type of project:

{% include image.html path="taka-quite-a-journey/algolia-plan.png" path-detail="taka-quite-a-journey/algolia-plan.png" alt="Algolia free plan" %}

And it has the <a href="https://community.algolia.com/places/" target="_blank">Algolia Places API</a> and it does everything we need:

- search for an address and get it's position
- reverse geocoding

The free tier is not that awesome, I just hope users won't search that many places and will use the shortcuts feature. It could be quite expensive (40 cents per 1000 requests).


<br />
<div style="text-align:center;"><b>Solution solved for our geocoding needs. (☞ﾟ∀ﾟ)☞</b></div>

<br /><br />
## Where should I deploy it?

### Google Cloud Platform

I've talked about free tier right?

7 months of procrastination later..

{% include image.html path="taka-quite-a-journey/gcp-outch.png" path-detail="taka-quite-a-journey/gcp-outch.png" alt="GCP is expensive" %}

Oh yeah, that's <b>330 euros</b> from your pocket only for having a fancy orchestration for your side project. But at least you know how to handle apps over Kubernetes and you made it to your day-to-day work and that's something.

In that price is included GCP Load balancer (ingress):

{% include image.html path="taka-quite-a-journey/google-loadbalancing.png" path-detail="taka-quite-a-journey/google-loadbalancing.png" alt="GCP is very expensive" %}

Yes, <b>127 euros</b> for forwarding your requests.<br />
How many users? Let's ask Google Analytics:

{% include image.html path="taka-quite-a-journey/google-analytics-2018.png" path-detail="taka-quite-a-journey/google-analytics-2018.png" alt="GCP is very very expensive" %}

<b>102 users</b>, probably half of this visits are myself and the other half are bots.

<div style="text-align:center;">
That's <b>1.24 euros per visit of load balancing</b>. Worth it.
</div>

<br /><br />
### OVH

Now that you wasted a lot of money, you search for a cheaper alternative.

We have 1 API, 1 GTFS Server and 1 server which only serves the front end.<br />Let's be comfortable, just take one VPS for our API and our front-end and one VPS for our GTFS Server.

Remember that our GTFS server (OpenTripPlanner) is written in Java. It takes space.

{% include image.html path="taka-quite-a-journey/ovh-quote.png" path-detail="taka-quite-a-journey/ovh-quote.png" alt="OVH is cheap for side projects" %}

<b>5.98 euros per month</b> before taxes for <b>2 VPS</b>. Suits our needs and it's only <b>7%</b> of our monthly GCP invoice.

Yes you need to log each time to your VPS to upgrade your docker images, but it works and it's really cost-effective. Furthermore, users don't care. And remember you don't have a lot of time on your hands, it's not like you are doing daily or even weekly updates.

<br /><br />
# Why did it take so long?
<br /><br />
### You are probably not a designer

We are here:
{% include image.html path="taka-quite-a-journey/taka-activity-first-poc.png" path-detail="taka-quite-a-journey/taka-activity-first-poc.png" alt="TAKA activity graph" %}

<br />
{% include image.html path="taka-quite-a-journey/taka-mobile-app-first-release.png" path-detail="taka-quite-a-journey/taka-mobile-app-first-release.png" alt="Taka mobile app first release" %}

<div style="text-align:center;">
Beautiful isn't it?
</div>

<br />

What happened during the following months? Oh yes, absolutely nothing.
Why? Because your app works, but it is ugly AF but in the same time you don't want to spend to much time on design because... you are not a designer and it's not something you like that much. In the meantime you started a bunch of another cool projects and they are way more interesting than finishing this.

<br /><br />
### Small tweaks take a lot of time

Because it's something you want to actually ship, you try as much as possible to make it:

- pixel perfect
- reduce user clicks to its minimum
- fast
- secure
- .. splendid !

There are some points you can't avoid (eg: security). There will be always room for improvement, but you have to deal with it. It's only a side project. Something I didn't do for this side project and I should have, is a MVP's roadmap. For my next project, even before prototyping something, I'll write a roadmap and launch it right after its completion.

<br /><br />
### No business opportunities

This greatly depends on your altruism level.
I could put some ads on the mobile app, but it would hide all my efforts on providing the best UX for the users.

Personally, I'll find a project interesting if it's technically challenging or with a great business opportunity.


<br /><br />
### You start an article about your app

... but you still haven't finished it.


<br /><br />
# D-Day

<br />
{% include image.html path="taka-quite-a-journey/last-design.png" path-detail="taka-quite-a-journey/last-design.png" alt="last release (early 2019)" %}

Everything seems alright, your app seems ready. There is even some gradient backgrounds, it's fancy. You can now submit it to the App Store.

{% include image.html path="taka-quite-a-journey/launch.gif" path-detail="taka-quite-a-journey/launch.gif" alt="Archer - Go for it" %}


Eventually you get rejected,

{% include image.html path="taka-quite-a-journey/rejected-1.png" path-detail="taka-quite-a-journey/rejected-1.png" alt="Rejected" %}
{% include image.html path="taka-quite-a-journey/rejected-2.png" path-detail="taka-quite-a-journey/rejected-2.png" alt="Rejected" %}
{% include image.html path="taka-quite-a-journey/rejected-3.png" path-detail="taka-quite-a-journey/rejected-3.png" alt="Rejected" %}

{% include image.html path="taka-quite-a-journey/rejected.gif" path-detail="taka-quite-a-journey/rejected.gif" alt="Archer - rejected" %}

You <a href="https://github.com/TakaApp/mobile-application/commit/fa9ae84a261e54b1b4dbe44e1d3e06037f7a494e" target="_blank">remove the word Android</a> from your application, <a href="https://github.com/TakaApp/mobile-application/commit/69bf3cdab75db402ac184ccc6914394a268b3e53" target="_blank">you explain</a> to your users why you need their location even if it seems obvious, you submit it again.

And less than 12h after, your app has been approved.

{% include image.html path="taka-quite-a-journey/appstore-approved.png" path-detail="taka-quite-a-journey/appstore-approved.png" alt="Appstore approved it" %}


<br /><br />
# In the end, you don't even use your own app

because public transportation are terrible here and you are way faster with your ES2.

{% include image.html path="taka-quite-a-journey/electric-scooter.jpg" path-detail="taka-quite-a-journey/electric-scooter.jpg" alt="My ES2 (electric scooter)" %}

<br /><br />
# But eventually people like it a lot

{% include image.html path="taka-quite-a-journey/appstore.png" path-detail="taka-quite-a-journey/appstore.png" alt="App Store" %}

{% include image.html path="taka-quite-a-journey/average-review.png" path-detail="taka-quite-a-journey/average-review.png" alt="App Store review" %}


<br />
<div style="text-align:center;"><b>And that's a great reward. ヾ(⌐■_■)ノ♪</b></div>


<br /><br /><br />

# FAQ

Why nantes.cool?<br />
Because it's easy to remember: it has the city in the domain and it's a cool app.
