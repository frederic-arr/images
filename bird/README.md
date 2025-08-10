# BIRD Internet Routing Daemon

A rootless container image for the BIRD Internet Routing Daemon.

> [!IMPORTANT]
> This is an unofficial Docker image

## Requirements

The container should have the following capabilities:

- `NET_BIND_SERVICE`
- `NET_BROADCAST`
- `NET_ADMIN`
- `NET_RAW`

## Configuration

This image expects the BIRD config to be placed under `/app/config/bird.conf`.

The following files will also be created at runtime:

- **PID file**:  
  `/app/run/bird.pid`

- **BIRD control socket**:  
  `/app/run/bird.ctl`

## Supported tags

- `latest`
- `3.1.2`

## Quick reference

- **BIRD Source Code**:  
  https://gitlab.nic.cz/labs/bird/tree/master

- BIRD User's Guide:  
  https://bird.network.cz/?get_doc&f=bird.html&v=30

- **Where to file issues:**  
  https://github.com/frederic-arr/images

- **Source of the image**:  
  https://github.com/frederic-arr/images/tree/main/bird

- **Maintained by**:  
  Frédéric Arroyo (https://github.com/frederic-arr)
