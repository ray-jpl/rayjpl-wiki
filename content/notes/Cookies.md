---
title: Cookies
enableToc: true
tags:
---
# Cookies
## What are Cookies
A cookie is data sent as a key=value pair  that a server sends to a users web browser. These cookies allow servers to store various **stateful** information on a users device/browser. These cookies are sent with **every** subsequent requests to the server to convey stateful information. All cookies that pass all restrictions (correct domain, path, expiry time etc) are sent with the request, this can make cookies vulnerable to attacks like [CSRF attacks](https://owasp.org/www-community/attacks/csrf).

Cookies are now primarily used for three purposes:
**User Sessions**
- A session cookie will store a unique string associated with a persons user id
	- When navigating a website you do not need to login again for each new page loaded. Each HTTP request to the server for the page will include the session cookie to validate the user.
- Keep track of items in shopping carts

**Personalisation**
- Cookies help a website remember the users preferences to customise user experience
	- E.g 'Remember Me' checkboxes to store username or user id on the browser
	- Browser can store cookies for user preferences such as Dark Mode. You can easily check this with browser tools as some sites such as Twitter and Reddit store this in plaintext or easily identifiable names. Google also outlines how they use some of their cookies [here](https://policies.google.com/technologies/cookies?hl=en-US#types-of-cookies)
	
**Tracking**
- Session cookies can track how many unique visitors has used the website.
- Session cookies can also track how many requests are made by a user, this can be used to rate limit specific users if they have sent too many requests/sec.
- Third Party cookies
	- A cookie is often associated with a particular domain. If the domain of the cookie does not match the current domain then it is considered a third party cookie.
		- Sites cannot use cookies that do not originate from its domain. e.g it cannot read/set third party cookies
	- Often if there is a Like or Share to 'Twitter, Facebook etc' button. For the Like/Share button the browser may need to interact with the facebook.com domain in order to check you have logged in. Since it is interacting with the facebook.com domain it will be able to read any cookies originating from that domain. If you are logged into Facebook on your computer then it is probable that there is a cookie from Facebook that can identify you. 
	- Similarly for pages with Google Ads embedded in them, to load the ads you would need to make a request to one of Google's domains. This request would contain a cookie that identifies you. If this cookie is passed in then Google can then send targeted advertising. 
## Why do we need cookies
Cookies make it easier to build stateful web applications. Other methods of identifying a device or user such as identifying by IP address, embedding state information in the URL or use hidden fields in HTML can be unreliable and failure prone. 

Using an IP address is unreliable as if a proxy is used then the website would see the proxy's IP address and not your device's. Your ISP may also provide temporary IP addresses whenever you connect to it. Therefore your IP address could be different when you visit a website at different times.  

Using the URL or hidden HTML fields to store state  is unreliable as page navigation such as pressing the Back button would roll back the users state. For shopping applications it would mean a users shopping cart would be reverted. 

Cookies solved these problems. Cookies are sent in the HTTP protocol as a header. A user's state is also tracked by the browser instead of the web server. Originally, cookies were created to solve the problem of pending shopping carts in e-commerce. The company did not want its servers to store all partial transaction states. Cookies allowed the state of the shopping cart to be stored in the browser and then only when the order is submitted then the cart information cookie is submitted with the request.   
# Resources
- [HTTP Cookies - MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies)
- [HTTP Cookies: Standards, Privacy and Politics - David M. Kristol](https://arxiv.org/pdf/cs/0105018.pdf)
- [What are cookies - Cloudflare](https://www.cloudflare.com/learning/privacy/what-are-cookies/)