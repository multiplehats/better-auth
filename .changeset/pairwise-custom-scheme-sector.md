---
"@better-auth/oauth-provider": patch
---

Pairwise clients with a custom-scheme redirect URI that includes a host, such as `app://rp.example.com/callback`, now receive a `sub` that no other client shares. Previously, such a client received the same pairwise `sub` as HTTPS clients on the same host.

Better Auth has rejected these redirect URIs since 1.7.0, so affected clients were registered on an earlier version. Their users' pairwise `sub` values change after upgrading, so a relying party that stores `sub` for such a client must re-link its users. Clients that use only HTTPS, loopback, or authority-free redirect URIs are unaffected.
