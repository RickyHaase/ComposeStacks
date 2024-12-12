# Ghost Blog with Cloudflare Tunnel via Docker Compose

[Ghost Official Documentation for Docker](https://hub.docker.com/_/ghost)

[Cloudflare Tunnels Official Documentation](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/get-started/create-remote-tunnel/)

## Prerequisites:
- Cloudflare account with a domain registered to the account and using Cloudflare as the authoritative name server
- A host with Docker and Docker-Compose (podman and podman-compose might also work)
- A pre-existing methodology for backing up docker compose stacks and their bind-mount locations/databases

## Information for cloudflare tunnel hostname configuration
- Ensure that the public hostname in Cloudflare is the same as the URL specified in the .env file
- The local address just needs to be the name of the container followed by the port. By default with no changes to the compose, that should be http://ghost:2368

## Options
- If running multiple blogs with a shared database and reverse proxy, see section "Multiple Blogs"
- If using a different reverse proxy, see section "No Cloudflare"

### Multiple Blogs
**To-Do** Make instructions for setting up multiple ghost containers in the same stack using the same database and reverse proxy

### No Cloudflare
- To use a reverse proxy other than cloudflared in the stack, simply replace the cloudflared container with the compose for your reverse proxy. Use http://<containername>:2368 to reach the Ghost container from the reverse proxy.
- To use an external reverse proxy, remove cloudflared and expose uncomment the port configuration in the compose for Ghost to expose the Ghost container on the host's port 8080.
- To use a reverse proxy that exists as a docker container outside the stack but still on the same host, remove cloudflared and make sure that the frontend network in the stack is specified as the external network that the reverse proxy is part of. This will give the reverse proxy access to Ghost without having to route traffic outside the docker network. Use http://<containername>:2368 to reach the Ghost container from the reverse proxy.
