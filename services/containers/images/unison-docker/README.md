# Unison Sync Docker Image

This Dockerfile will build an image to run [Unison File Synchronizer](https://www.cis.upenn.edu/~bcpierce/unison/). I use it within my network to sync files between serves and virtual machines.

## Build Instructions

```sh
docker build --tag unison-docker:2.51.3 .
```

## Usage Instructions

```sh
docker run --rm --env UNISONLOCALHOSTNAME=example-01 --volume ~/.unison:/home/unison/.unison --volume ~/.ssh:/home/unison/.ssh --volume /srv/ppn:/srv/ppn --volume /var/log:/var/log -it unison-docker:2.51.3 -batch example-01
```

You must set the `UNISONLOCALHOSTNAME` environment variable to avoid Unison creating new archives on each `docker run`. If you don't do this, because the containers are ephemeral they will have a new hostname on each run of `unison-docker` and Unison will create a new archive file on each run.

Each device that runs the container must have a Unison profile (`example-01.prf`), and that should be specified without the `.prf` file ending as shown in the run command above (`-batch example-01`).

```ini
# Sync roots:
root=/srv/ppn/
root=ssh://<username>@<fileserver-ip>//<path-to-sync>

# Sync options:
sshargs=-oIdentityFile=<private-key-path>

# Sync paths:
path=shared/
path=services/containers/compose/dnsmasq
path=services/containers/compose/unbound

# Log options:
log=true
logfile=/var/log/unison/sync_example-01.log
```

