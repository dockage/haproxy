# Lightweight HA Proxy Docker image

Lightweight HAProxy container based on Alpine 3.8 and HA Proxy 1.8.5
(about ~6 MB)

## Build instructions

### In case you want to customize haproxy image

1. Clone the Project to your work directory

2. Make sure you have docker installed/running by running `docker -v` and getting a response from docker-daemon

3. Run the Command `docker build -t haproxy-alpine(yourname):(tag) .

4. Wait for the process to finish

Now you have successfully built the docker image.

## How to Use the image to build other images / in a compose project

1.In a Dockerfile:

You simply put the `haproxy-alpine(yourname):(yourtag) .`in From line`.

example:

```
FROM haproxy-alpine(yourname):(yourtag)

MAINTAINER <khashayar.danesh@gmail.com>

COPY haproxy.cfg /etc/haproxy/
```

2.In a Compose File:

You Create a Service Block in `docker-compose.yml` which uses this image:

example:

```
version: '2'
services:
  airports:
    image: "haproxy-alpine(yourname):(yourtag)" 
    container_name: haproxy
    ports:
      - "yourhostport:yourcontainerport"
      - "yourhostport2:yourcontainerport2"
```

## Configuration

the haproxy-configuration is placed in /etc/haproxy/haproxy.cfg

So you may create a docker-image based on this container and put your config in the mentioned directory or just create a service-block and mount the directory containing this config in /etc/haproxy