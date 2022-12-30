# Dockerized Jenkins Server with DinD installed

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