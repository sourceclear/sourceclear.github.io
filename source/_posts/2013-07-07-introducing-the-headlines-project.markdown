---
layout: post
title: "Introducing The Headlines Project"
date: 2013-07-10 9:15
comments: true
categories: headlines labs open-source java
author: Mark Curphey
published: false
---
We have just pushed a new project live called Headlines. Headlines is all about security HTTP Headers and consists of two parts:

* Headlines Scan
* Headlines Library <!-- more -->

Headlines Scan is a free service that analyzes HTTP response headers returned from any web site on the Internet and reports on the presence of HTTP security headers that can be used by software developers to prevent common security vulnerabilities like Cross Site Scripting (XSS), Cross Site Request Forgery (CSRF) and Click Jacking. We test for the following headers:

- Content Security Policy
- Strict Transport Security
- X-Frame Options
- X-Content-Type-Options
- X-XSS-Protection

Headlines Library is an open source Java library which uses servlet filters to inject HTTP response headers coming out of your app server.

Given the prevelance of vulnerabilities like Cross Site Scripting (XSS), Cross Site Request Forgery (CSRF) and Click Jacking It is not suprising that progressive technology companies like Twitter, FaceBook and Google are all using security headers to raise the security bar. Sadly broader adoption is low. 

We will follow-up with posts and screencasts on both Headlines Scan and Headlines Library and publish an on-going report tracking the Top 1,000 web sites on the Internet soon. 