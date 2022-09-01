---
caption: #what displays in the portfolio grid:
  title: Ketting
  subtitle: A blazing fast generic hypermedia client for Javascript
  thumbnail: /assets/img/portfolio/ketting-code.png
  emoji: ⛓

title: Ketting
subtitle: A generic hypermedia client for Javascript
image: /assets/img/portfolio/ketting-code.png
alt: Ketting is the Dutch word for 'chain'. 👉😎👉
website: https://github.com/badgateway/ketting

---
Ketting is a generic hypermedia client for Javascript. It works both on browsers and in node.js. A hypermedia client removes the need to update client applications when adding features to your API - for example a new authentication method or creating new conditions for a new client type.

If your REST API uses Hypermedia in any way, Ketting gets additional powers. Ketting allows you to traverse your API through **links that it exposes** and discover endpoints and features.

For your links to be recognized, they need to either appear in `HTTP Link Headers`, or your API needs to generate one of the following Hypermedia formats:
- Hal
* Siren
- JSON:API
- Collection+JSON
- Or HTML! 

It can pick up links from <a> or <link> tags, as long as they have a have a rel and a href attribute.

Ketting supports the following authentication schemes:

{:.list-inline.project-features}
- HTTP Basic auth
- Bearer token auth
- OAuth2 flows:
  - `password` grant
  - `client_credentials` grant
  - `authorization_code` grant
  - `implicit` grant

When using Ketting across multiple domains, it optionally supports per-domain authentication.
If you use Ketting with React, Ketting ships with a bunch of React bindings that make developing a lot easier.

The API is heavily inspired by Apollo Client, and should be familiar if you've used it in the past.




