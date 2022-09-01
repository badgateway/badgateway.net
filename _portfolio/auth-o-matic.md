---
caption: #what displays in the portfolio grid:
  title: Auth-o-Matic
  subtitle: "A complete Authentication system for those that don't want to build it themselves."
  thumbnail: /assets/img/portfolio/a12n-server-login-screenshot.png
  emoji: 🤖
  
#what displays when the item is clicked:
title: Auth-o-matic 
subtitle: "A ready-to-launch User and Authentication system for those that don't want to build it. (Initial idea was: Kwik-e-Auth)"
image: /assets/img/portfolio/a12n-server-login-screenshot.png #main image, can be a link or a file in assets/img/portfolio
alt: Image of a robot

---

A ready-to-launch User and Authentication server for those that don't want to build it. The project implements OAuth2 standards where applicable. A12n requires MySQL and Node.js 14.x

A bit more description of the problem this solves goes here, and who it’s for.

{:.list-inline.project-features} 
- OAuth2
  - Supported grants: implicit, client_credentials, authorization_code and password.
  - OAuth2 discovery document
  - PKCE.
- OAuth 2 Token Introspection
  - JSON Web Key Sets.
  - OAuth2 Token Revocation
- MFA
  - Google Authenticator (TOTP)
  - WebauthN / Yubikeys
- Keys included:
  - A simple browseable API
  - User registration, lost password
  - A simple, flat, permission model
  - `secret-token:` URI scheme