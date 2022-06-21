# Caddy Namecheap Docker Image

This Dockerfile will build Caddy with the Namecheap module located [here](https://github.com/caddy-dns/namecheap). This allows Caddy to use the Namecheap API to add DNS records to verify ownership of a domain you are trying to get an HTTPS certificate for.

## Build Instructions

Run the following standard Docker `build` command from the image directory.

```sh
docker build --tag caddy-namecheap:latest .
```

