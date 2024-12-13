# Vaultwarden with Tailscale Sidecar

[Vaultwarden Official Insturctions](https://github.com/dani-garcia/vaultwarden/wiki/Using-Docker-Compose)
[Tailscale Official Instructions](https://github.com/tailscale-dev/docker-guide-code-examples)

NOTE: There is a project called [TSD-Proxy]() which can use one docker container to manage multiple other services.
However, for something as critical and sensitive as the password manager, I beleive it is worth it to run the official sidecar (even if it's less efficient)

NOTE: Disable key expiry in tailscale OR re-auth every few months

**To-Do** Flesh out instructions after dialing in env variables
