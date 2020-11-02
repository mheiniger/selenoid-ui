# Selenoid UI https
[![Release](https://img.shields.io/github/release/mheiniger/selenoid-ui-https.svg)](https://github.com/mheiniger/selenoid-ui-https/releases/latest)
[![Docker Pulls](https://img.shields.io/docker/pulls/mheiniger/selenoid-ui-https.svg)](https://hub.docker.com/r/mheiniger/selenoid-ui-https)

# Fork description

This is just a fork of https://hub.docker.com/r/aerokube/selenoid-ui and it adds the following:
 - You can use https in `--selenoid-uri=https://selenoid.example.com`
 - Its wrapped into an alpine container, so you now have a shell to debug things

# Original description

Simple status page with UI updates by SSE,
backed by constant polling of status handle
of [selenoid](https://github.com/aerokube/selenoid) on small go backend.

![ui](https://raw.githubusercontent.com/aerokube/selenoid-ui/master/docs/img/stats-sessions.png)

## Usage

We distribute UI as a lightweight [Docker](http://docker.com/) container. To run it type:
```
$ docker run -d --name selenoid-ui  \
    --link selenoid                 \
    -p 8080:8080                    \
    aerokube/selenoid-ui --selenoid-uri=http://selenoid:4444
```

where `--link selenoid` links with running container named `selenoid` with selenoid inside

Then access the UI on port 8080:
```
http://localhost:8080/
```
The following flags are supported:

- `--listen` - host and port to listen (e.g. `:1234`)
- `--period` - data refresh period (e.g. `5s` or `1m`)
- `--selenoid-uri` - selenoid uri to fetch data from (e.g. `http://selenoid.example.com:4444/`)

## Features, Screenshots and Complete Guide

Can be found at http://aerokube.com/selenoid-ui/latest/

## Usage note

This UI is designed for debug purposes for one selenoid node. If you need
monitoring capabilities on more than one selenoid, consider
to use [external monitoring system](http://aerokube.com/selenoid/latest/#_sending_statistics_to_external_systems)
