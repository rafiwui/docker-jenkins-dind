# Dockerized Jenkins Server with DinD installed
With these files you can spin up a dockerized Jenkins server with Docker and docker-compose installed and ready to use.

I recommend to use this compose file with my [*nginx-proxy compose*](https://github.com/rafiwui/docker-nginx-proxy).

If you want to use this as a standalone compose, you have to add portforwarding into the nginx container and probably edit it further so it can handle certificate creation.

## Prerequisites
You have to update the permissions of `/var/run/docker.sock` on the host system:
```
sudo chmod 666 /var/run/docker.sock
```

## Setup
### Environment
Update the environment variables in [`docker-compose.yml`](docker-compose.yml) to your fitting:

*TZ*, *VIRTUAL_HOST*, *LETSENCRYPT_HOST* and *LETSENCRYPT_EMAIL*

### Plugins
[`plugins.txt`](jenkins/plugins.txt) contains a list of plugins that are automatically installed when initializing the container.
If you already know plugins you want to have in your installation, you can extend this list before spinning up the container.

## Usage
Currently `docker-compose` does only work as `docker-compose` in pipelines and not as a built-in `docker compose` command.