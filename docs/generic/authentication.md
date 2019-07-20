# Authentication

If you do not have an account as it is, get one using one of the partners below : 

Accounts by default can only access certain endpoints.
Accounts can be given [permissions](#account-flags) to other endpoints by an administrator.

Locked endpoints and upgraded accounts can be acquired through Patreon subscriptions. Check out the plans [Here](https://www.patreon.com/raidandfade)
For any support with your account, or any part of the api, join the [Discord server](https://discord.gg/Hfq2djq)

Partner | Link
--- | ---
Github | [Link](https://github.com/login/oauth/authorize?client_id=4463c0899e48730d72c7&scope=user:email&redirect_uri=https://api.gocode.it/auth/auth?partner=github)
Google | [Link](https://accounts.google.com/o/oauth2/v2/auth?response_type=code&client_id=822145115373-mkkumnomvdsfhgbobk9f9ih7rp1820im.apps.googleusercontent.com&scope=email&redirect_uri=https://api.gocode.it/auth/auth?partner=google)

## Account Flags

Flag | Purpose
--- | ---
ADMIN | Access to all endpoints (including some undocumented ones)
UPGRADED | Higher limits and some special endpoints
EXECUTE | Access to the [execute](/generic/miscellaneous/#execute-code) endpoint
IP | Access to the [IP](/generic/miscellaneous/#ip-information) endpoint
WOWDB | Access to the [WoWDB](/wowdb/) endpoints

## Invalidate Token
__URL__ `GET /auth/invalidate`

> Invalidates your current token and gives you a new one.

## Information Request
__URL__ `GET /auth/info`

> Fetch information related to your token. such as the email, flags, and id of the account.
