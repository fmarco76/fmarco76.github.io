---
layout: post
title:  Enabling SSO on Discurse using SAML or OpenID Connect
date:   2015-07-01 15:30:00
description:
headline:
tags: [discourse, SSO, SAML, Identity Federation]
category: Single Sign-On
imagefeature:
mathjax:
chart:
comments: true
share: true
---

Recently I was asked to include a web forum based on [Discourse](http://www.discourse.org)
inside the [GrIDP Identity Federation](https://gridp.garr.it) in order to enable
Signe Sign-On (SSO) with other services using SAML based authentication.

Discourse comes with a nice support for SSO so the integration would be
effortless but the support provide its own protocol which the identity provider
has to implement. Actually, there are several add-ons to include SAML based
authentication into Discourse and these were developed in Ruby and were able to
parse the SAML assertions internally to the application. Although this is a nice
approach only very simple scenarios are supported using these because not all
SAML profiles and features are supported. As a result, no Discourse add-on fits
with the scenario
