---
layout: post
title:  Enabling SSO on Discurse using SAML or OpenID Connect
date:   2015-07-15 15:30:00
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

Recently I was asked to enable SAML authentication on a
[Discourse](http://www.discourse.org) instance which was deployed for the [project
Sci-Gaia](http://discourse.sci-gaia.eu) because the service should be added into the
[GrIDP Identity Federation](https://gridp.garr.it) to enable Single Sign-On (SSO)
with other project services.

Discourse comes with a nice support for SSO but it implements a proprietary
protocol which the identity provider has to support, and this is not the case for
SAML based identity providers ([protocol details
here](https://meta.discourse.org/t/official-single-sign-on-for-discourse/13045)).
Actually, there are several plug-ins that enable SAML based authentication into
Discourse. These can parse the SAML assertions and perform the
authentication/authorisation of the user. Although this is a nice approach only
very simple scenarios are supported using these because not all SAML profiles
and features are supported. An example of such a [plug-in is available
here](https://github.com/PracticallyGreen/omniauth-saml).

As a result, I ended to develop a new service, named **DiscourseSSO**, acting as
proxy between Discourse and the IdP. The service is very simple because it
implements only two APIs: one used to verify the information provided by the
Discourse instance and the other, protected by Shibboleth, perform the
authentication and redirect the user back to Discourse. The following diagram
shows the steps the user agent (the browser) has to perform during the log-in.

![DiscourseSSO sequence diagram](/images/posts/DiscourseSSO.png)

The implementation is made in Python and requires the Flask framework
but the installation is quite simple. Source code and installation instruction are available
on GitHub at [https://github.com/fmarco76/DiscourseSSO](https://github.com/fmarco76/DiscourseSSO).
