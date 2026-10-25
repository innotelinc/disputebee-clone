# CrediSure in the Innotel Platform Stack

**Role: ClientOps** — Credit repair, from report review to the letter in the mail.

Part of the [Innotel Platform Stack](https://github.com/innotelinc/innotel-platform-stack).
The canonical definition of the stack, its shared layers and their owners lives
there; this file records only what CrediSure does inside it.

## Boundaries

### Owns

- the client case and report review
- dispute letters and their rounds
- the progress view

### Consumes

- Cerulean (Authentik SSO, DNS, TLS)
- Cerulean Vault (secrets)
- an SMTP or mail provider for letters

### Does not own

- credit bureau data
- identity (Authentik)
- legal advice

## Service map

| Component | Technology | Job |
| --- | --- | --- |
| CrediSure | Node.js / TypeScript | Credit repair, from report review to the letter in the mail. |
| Identity | Cerulean Authentik | Sign-in and role claims, where the repo has a UI |
| Secrets | Cerulean Vault (KV v2) | Production credentials, referenced as `vault://` |
| Trust | Cerulean | DNS, TLS and the public hostname |
| Edge | NPM Edge | The public route in front of the service |

## In the ecosystem

- **Identity** comes from Cerulean Authentik; this repo holds no second account
  table and no password of its own.
- **Secrets** come from Cerulean Vault. `.env` is local only and is never
  committed; a `vault://` reference is resolved by the deployment.
- **Trust and edge** are Cerulean's and NPM Edge's. This repo does not write DNS
  records or call the NPM API directly.
- **Storage, billing and telephony** belong to ONYX, Magnate and Zeus
  respectively; CrediSure consumes them only where the boundaries above say
  so.

## See also

- [README](../README.md)
- [Innotel Platform Stack](https://github.com/innotelinc/innotel-platform-stack)
