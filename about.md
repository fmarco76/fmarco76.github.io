---
layout: page
permalink: /about/index.html
title: Marco Fargetta
tags: [Marco, Fargetta, fmarco76]
imagefeature: fourseasons.jpg
chart: true
---
<figure>
  <img src="{{ site.url }}/images/me_home_pc.jpg" alt="Marco Fargetta">
  <figcaption>Marco Fargetta</figcaption>
</figure>

{% assign total_words = 0 %}
{% assign total_readtime = 0 %}
{% assign featuredcount = 0 %}
{% assign statuscount = 0 %}

{% for post in site.posts %}
    {% assign post_words = post.content | strip_html | number_of_words %}
    {% assign readtime = post_words | append: '.0' | divided_by:200 %}
    {% assign total_words = total_words | plus: post_words %}
    {% assign total_readtime = total_readtime | plus: readtime %}
    {% if post.featured %}
    {% assign featuredcount = featuredcount | plus: 1 %}
    {% endif %}
{% endfor %}


My name is **Marco Fargetta**, and this is my personal blog. It currently has
{{ site.posts | size }} posts in {{ site.categories | size }} categories which
combinedly have {{ total_words }} words, which will take an average reader
({{ site.wpm }} WPM) approximately <span class="time">{{ total_readtime }}</span>
minutes to read. {% if featuredcount != 0 %}There are
<a href="{{ site.url }}/featured">{{ featuredcount }} featured posts</a>,
you should definitely check those out.{% endif %} The most recent post is {% for post in site.posts limit:1 %}{% if post.description %}
<a href="{{ site.url }}{{ post.url }}" title="{{ post.description }}">"{{ post.title }}"</a>{% else %}
<a href="{{ site.url }}{{ post.url }}" title="{{ post.description }}" title="Read more about {{ post.title }}">
"{{ post.title }}"</a>{% endif %}{% endfor %} which was published on {% for post in site.posts limit:1 %}{% assign modifiedtime = post.modified | date: "%Y%m%d" %}{% assign posttime = post.date | date: "%Y%m%d" %}<time datetime="{{ post.date | date_to_xmlschema }}" class="post-time">{{ post.date | date: "%d %b %Y" }}</time>{% if post.modified %}{% if modifiedtime != posttime %} and last modified on <time datetime="{{ post.modified | date: "%Y-%m-%d" }}" itemprop="dateModified">{{ post.modified | date: "%d %b %Y" }}</time>{% endif %}{% endif %}{% endfor %}. The last commit was on {{ site.time | date: "%A, %d %b %Y" }} at {{ site.time | date: "%I:%M %p" }} [UTC](http://en.wikipedia.org/wiki/Coordinated_Universal_Time "Temps Universel Coordonné").


I graduated in Computer Engineering at the University of Catania (Catania, Italy) in 2002 with a thesis on a new
Java extension for Computational Reflection. In 2007 I held a Ph.D. in Computer Engineering from
the same University (a part of the Ph.D. study was done at the University of Manchester, UK)
with a thesis titled *A Model for Automatically Supporting Advanced Reservation, Allocation and Pricing in a Grid Environment*.
My research activity started with the Ph.D. in 2003 and initially was focused on advanced scheduling of grid jobs. After my interests
have expanded into security, authentication and authorisation aspects of distributed computing environments, including grid and clouds.

Since 2007 I have been involved in different projects at national and international levels. These include:
- the  [TriGrid VL project](http://www.trigrid.it), funded by the Sicilian Regional Government, as member of the University of Catania, Department of Mathematics;
- the  ICEAGE project with the Department of Physics and Astronomy, funded by the European Union;
- the PI2S2 project, funded by the regional government, with Consorzio COMETA (an organization owned by all University and research centre in Sicily);
- the EUAsiaGrid and DECIDE projects, funded by European Union, with INFN;
- the RECAS and PRISMA (currently involved) projects, funded by the Italian PONREC activity.

The activity performed in the context of the Ph.D. and the following projects is documented by many publications in international conferences, journals and books.
An updated list is available in my [google scholar page](https://scholar.google.com/citations?user=NenMzJEAAAAJ&hl=en)

Currently I am working at [INFN](http://www.infn.it) in Catania for the European project
INDIGO-Datacloud and I am also the technical manager of the [GrIDP Identity Federation](http://gridp.garr.it),
a production ready federation managed by INFN and GARR which aims at federating services.

*[INFN]: Italian Institute for Nuclear Physics
*[GARR]: The Italian National Research and Education Network


In my free time (this is very rare considering the effort required to grow-up two kids) I love to take photos and video and spend many hours trying to transform them in something nice.


For more detailed on my current and past activities have a look at my CV ([Italian](/CV/italian.pdf), [English](/CV/english.pdf)) or have a look at my [linked profile](https://www.linkedin.com/in/fmarco76)
