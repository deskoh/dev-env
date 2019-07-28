# Development Environment

Development environment with NGINX reverse proxy and [nip.io](https://nip.io) wildcard DNS server using docker compose.

# NGINX Reverse Proxy

The NGINX reverse proxy listens on port `8080` by default. Requests can be proxied to configured upstream server using NGINX host-based or path-based routing.

## Reloading NGINX Configuration

```
docker exec nginx nginx -s reload
```

# Usage with NIP.IO DNS Service

In an environment with no internet connection, a local nip.io DNS service is provided. See [repo](https://github.com/deskoh/nip.io) here for more details. DNS server has to be set to `127.0.0.1`. If an upstream DNS server is required, the environment variable `PDNS_recursor` can be set in `docker-compose.yml`.

This can easily allow testing of host-based routing. For example, if docker compose is running on `127.0.0.1`, `app.127.0.0.1.nip.io:8080` will reach the NGINX and be routed to configured upstream server.
