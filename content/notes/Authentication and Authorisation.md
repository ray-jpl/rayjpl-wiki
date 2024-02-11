---
title: Authentication
enableToc: true
tags:
  - Authentication
  - Authorisation
  - Session
  - JWT
---
# Authentication
Authentication is the process of verifying the identity of a user. As HTTP is a stateless protocol, the client and server do not automatically keep track of subsequent requests. 

## Session
Session authentication is associated with using [[notes/Cookies|Cookies]] to manage sessions. The cookie holds identifying information about the user while the state is tracked on the server.

The usual flow for Session based authentication is as follows
1. User submits a login request with their credentials
2. Server validates the credentials. If valid then creates a session on the database and a unique id, this unique id is sent back to the user in the form of a Cookie.
3. User saves the session id in the browser and sends this cookie back for each subsequent request to the server as a header.
4. If the session id is found in the database then it can retrieve information about the client

Cookies should not be storing any important personal identifying information, only the corresponding session id in the server. 

When the user closes their browser the session cookies are automatically cleared. The session information on the server will persist and be cleared until it expires or is explicitly cleared. 

Session IDs are relatively short lived and usually stored in a cache like [[notes/Redis|Redis]] to improve performance instead of being stored in the main DB. 

## Token
The usual flow for token based authentication is as follows:
1. User submits login request with their credentials
2. Sever validates credentials. If valid then creates a signed token and sent back to the user. 
3. User saves the token in the browser and can attach it for any future requests
4. Server can decrypt the token with its secret key to check its validity. If valid then it will authorize the request. 

The difference here is that the server does not need to save anything about the user. State is stored on the token which is stored in the users browser.

[JSON Web Tokens (JWT)](https://jwt.io/) is a popular standard for creating signed data that contains a JSON payload. JWTs are often used tokens in authentication flows.

OpenID Connect (OIDC) and OAuth 2.0 are protocols commonly used in modern authentication and authorization systems.
- OAuth 2.0 is an authorization framework that allows third-party services to access resources on behalf of a resource owner (usually a user) without sharing the user's credentials.
- OIDC allows clients to verify the identity of the end user based on the authentication performed by an authorization server, as well as to obtain basic profile information about the user.
- Read more details
	- [ID token vs Access Token - Auth0](https://auth0.com/blog/id-token-access-token-what-is-the-difference/)
	- [What are Refresh tokens - Auth0](https://auth0.com/blog/refresh-tokens-what-are-they-and-when-to-use-them/)
	- [An Illustrated Guide to OAuth and OIDC](https://youtu.be/t18YB3xDfXI)

# Resources
- [Session-based Authentication - roadmap.sh](https://roadmap.sh/guides/session-based-authentication)
- [JWT vs Cookies for token based authentication - StackOverflow](https://stackoverflow.com/questions/37582444/jwt-vs-cookies-for-token-based-authentication)
