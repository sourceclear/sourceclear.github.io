---
layout: post
title: "Introducing Headlines Library"
date: 2013-07-10 10:00
comments: true
categories: headlines labs open-source java
author: Jason Nichols 
published: false
---
Here at <a title="SourceClear.com" href="https://www.sourceclear.com">SourceClear</a>, we've been inspired!  We saw Twitter's excellent <a title="SecureHeaders" href="https://github.com/twitter/secureheaders">SecureHeaders</a> library, which offers an easy way to include several security related HTTP response headers into your Rails applications.  Why should Rails have all the fun?  As a response (pun intended) we're rolling out our own Java-based secure headers library for servlet based applications.  Say Hello to <a title="Headlines" href="https://github.com/sourceclear/headlines">Headlines</a>.
Headlines is a library which uses servlet filters to inject HTTP response headers coming out of your app server.<!-- more -->
With a few simple configuration directives, you can instruct client browsers to take several precautions that will decrease the attack surface area of your app.  These reduce the risk of a number of common web vulnerabilities. Specifically HeadLines locks down your app with:
<ul>
	<li><a title="HSTS" href="https://tools.ietf.org/html/rfc6797">Http Strict Transport Security (HSTS)</a></li>
	<li><a title="X-Frame Options" href="https://tools.ietf.org/html/draft-ietf-websec-x-frame-options-00">X-Frame Options</a></li>
	<li><a title="XSS Filter" href="http://msdn.microsoft.com/en-us/library/dd565647.aspx">Microsoft's XSS Filter</a></li>
	<li><a title="CSP" href="https://developer.mozilla.org/en-US/docs/Security/CSP">Content Security Policy</a></li>
	<li><a title="HttpOnly" href="https://www.owasp.org/index.php/HttpOnly">HTTP Only Cookies</a></li>
</ul>
I'll go into detail each of these technologies in future posts, but for now I'll give a quick overview of the entire package:

<strong>HSTS</strong> is a rad little header that specifies to the browser that *all* future requests to the server should be over HTTPS.  This helps guard against insecure man in the middle attacks as well as developer goofs where a link may specify HTTP instead of HTTPS.

<strong>X-Frame Options</strong> instruct client browsers to never show your app pages within a frame (or only frames from certain hosts).

<strong>Microsoft's XSS Filter</strong> is an opaque IE8+ technology that detects and mitigates <a title="Reflected XSS" href="https://en.wikipedia.org/wiki/Cross-site_scripting#Non-persistent">reflected XSS</a> attacks.

<strong>Content Security Policy (CSP)</strong> allows you to specify to the browser where it should be allowed to load resources from.  It's a powerful technology that allows you to make rules such as 'only load JavaScript  from our domain, and never allow the use of inline script'.

<strong>Http Only Cookies</strong> When a cookie is marked HttpOnly, the browser will not allow scripts to access cookie contents, only sending it back to the server over HTTP or HTTPS.  This is ideal for use on session cookies.

Headlines is open sourced under the Apache 2.0 license, check out the source and developer docs on Github:  <a title="HeadLines" href="https://github.com/sourceclear/headlines">https://github.com/sourceclear/headlines</a>

Maven users can enjoy this goodness right now by including it in their project (and following the simple instructions in the Github README):

{% gist 5724892 %}