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
you should definitely check those out.{% endif %} The most recent post is
{% for post in site.posts limit:1 %}{% if post.description %}
<a href="{{ site.url }}{{ post.url }}" title="{{ post.description }}">"{{ post.title }}"</a>{% else %}
<a href="{{ site.url }}{{ post.url }}" title="{{ post.description }}" title="Read more about {{ post.title }}">
"{{ post.title }}"</a>{% endif %}{% endfor %} which was published on {% for post in site.posts limit:1 %}{% assign modifiedtime = post.modified | date: "%Y%m%d" %}{% assign posttime = post.date | date: "%Y%m%d" %}<time datetime="{{ post.date | date_to_xmlschema }}" class="post-time">{{ post.date | date: "%d %b %Y" }}</time>{% if post.modified %}{% if modifiedtime != posttime %} and last modified on <time datetime="{{ post.modified | date: "%Y-%m-%d" }}" itemprop="dateModified">{{ post.modified | date: "%d %b %Y" }}</time>{% endif %}{% endif %}{% endfor %}. The last commit was on {{ site.time | date: "%A, %d %b %Y" }} at {{ site.time | date: "%I:%M %p" }} [UTC](http://en.wikipedia.org/wiki/Coordinated_Universal_Time "Temps Universel Coordonné").


I graduated in Computer Engineering at the University of Catania in 2002 with a thesis on a new
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

<figure>
	<img src="{{ site.url }}/images/Hossain-Mohd-Faysal.jpg" alt="Hossain Mohammad Faysal">
	<figcaption>At Bates Linear Accelerator Center</figcaption>
</figure>

I was born and brought up in Doha. Yes, its a desert peninsula, yes we have camels and falcons and all the other Middle Eastern traits/stereotypes you can think of.

<figure class="third">
	<a href="{{ site.url }}/images/about/1.jpg"><img src="{{ site.url }}/images/about/1-001.jpg"></a>
	<a href="{{ site.url }}/images/about/2.jpg"><img src="{{ site.url }}/images/about/2-001.jpg"></a>
	<a href="{{ site.url }}/images/about/3.jpg"><img src="{{ site.url }}/images/about/3-001.jpg"></a>
</figure>
<figure class="half">
	<a href="{{ site.url }}/images/about/4.jpg"><img src="{{ site.url }}/images/about/4-001.jpg"></a>
	<a href="{{ site.url }}/images/about/5.jpg"><img src="{{ site.url }}/images/about/5-001.jpg"></a>
</figure>
<figure class="third">
	<a href="{{ site.url }}/images/about/6.jpg"><img src="{{ site.url }}/images/about/6-001.jpg"></a>
	<a href="{{ site.url }}/images/about/7.jpg"><img src="{{ site.url }}/images/about/7-001.jpg"></a>
	<a href="{{ site.url }}/images/about/8.jpg"><img src="{{ site.url }}/images/about/8-001.jpg"></a>
	<figcaption>Doha at its full glory.</figcaption>
</figure>

At some point in the not-terribly-distant future, I hope to found a self-sustaining collective of clever people, for fun, profit(?), and the promotion of human life in the universe. This might wind up in Qatar, Bangladesh, Scandinavia, the Massachusetts Bay Area, the SF Bay Area, Japan, Germany, or the dustbin of overly idealistic plans. (Yes, I have a special bin for overly idealistic plans. In my district they can't be recycled with residential mixed paper.) The most challenging aspect of this concept is to curtail unproductive competition with other people who will inevitably have the same idea. (Some sort of cooperative federation...) I'm presently looking for people who might be interested in being a part of such an organization.

Anyways, for now I'm just working toward changing the face of Electrical Engineering forever. Not that I necessarily expect to succeed, but it's something to strive for, and it's a fun problem to work on.


Entrepreneur  
Designer  
***Engineer***  
Inventor  

I
make
stuff.


*Beautiful, practical, meaningful stuff.*


I make what I love.

*I love what I do.*


But over the years, I noticed that somehow, along the way, software designed to help us be creative, actually made us less creative. That's because we believe our best ideas emerge when we use pencils and paper.
So I set out to build tools that work the way I do.


Tools for the creative space — the 53 centimeters that magically link head, heart, and hand. Tools as simple as pencil and paper. Tools so essential, I  really can't imagine work without them.


For
the makers,  
the creators,  
the discoverers,  
the original thinkers,  
***This is the space to create.***
