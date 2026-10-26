# Bunpro API

A community-maintained reverse-engineered API reference for [Bunpro](https://www.bunpro.jp/), a spaced repetition system for learning Japanese grammar.

## ⚠️ Important Notice

This is an **unofficial** reverse-engineered API documentation. It is provided under permission from the Bunpro team as discussed in [this community forum post](https://community.bunpro.jp/t/permission-to-reverse-engineer-the-bunpro-api/164173).

**The Bunpro API may change without warning.** This documentation will be maintained on a best-effort basis, but changes to the official API may not be immediately reflected here.

## Authentication and temporary API-token workaround

The Frontend API normally accepts the short-lived `frontend_api_token` browser cookie. An experimental alternative for integrations uses the API token displayed in **Settings → API** as the authorization token and appends this query parameter to every Frontend API request:

```text
dangerously_authenticate_using_api_token=true
```

For example:

```text
GET https://api.bunpro.jp/api/frontend/user?dangerously_authenticate_using_api_token=true
Authorization: Token token="<your API token>"
```

The API token must be surrounded by double quotation marks in the `Token token="..."` authorization format; `Bearer <token>` does not authenticate it. The API token is a secret. Do not expose it in client-side code, logs, URLs shared with others, or public repositories. The workaround is experimental, unsupported, and may change or be removed without notice. It also does not make the Frontend API an official, stable API.

Stricter request throttling has been in effect since 2026-08-12. Handle HTTP `429` responses, avoid bursts, and use only the requests required by your integration. A route allowlist may replace the current all-routes access; an endpoint that works today may later be unavailable through this workaround. If you distribute a Bunpro-integrated product, disclose these risks to its users.

## About Bunpro

[Bunpro](https://www.bunpro.jp/) is a popular web and mobile application for learning Japanese grammar through spaced repetition. It features:
- Grammar lessons and exercises
- Customizable study paths
- Progress tracking
- Community support

## Project Goals

This project aims to:
- Document the Bunpro API endpoints and methods
- Enable community developers to build tools and integrations
- Maintain up-to-date API documentation as the platform evolves

## Local Testing How To
To test this project locally you can follow these steps:
1. Run the command `redocly lint spec/frontend.yaml` to first lint the project and check the YAML is valid
2. Run http-server to run a local server from the main
3. Enter the docs directory which will launch the index.html

>[!WARNING]
> You may encounter caching issues. If this is the case clear the cache for the localhost page that you're using to test the redoc page locally.

## Credits
highliuk: [Bunpro Postman Collection](https://www.postman.com/technical-meteorologist-63813544/bunpro-api/collection/a7eufz9/bunpro-frontend-api)
