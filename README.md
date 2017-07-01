[![License: Apache 2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](https://www.apache.org/licenses/LICENSE-2.0.html)
[![Build Status](https://travis-ci.org/lasley/docker-node-makemkv.svg?branch=master)](https://travis-ci.org/lasley/docker-node-makemkv)

[![](https://images.microbadger.com/badges/image/lasley/node-makemkv.svg)](https://microbadger.com/images/lasley/node-makemkv "Get your own image badge on microbadger.com")
[![](https://images.microbadger.com/badges/version/lasley/node-makemkv.svg)](https://microbadger.com/images/lasley/node-makemkv "Get your own version badge on microbadger.com")

Node MakemKV
==============

This image provides Node MakeMKV as a monolithic Docker image.

Usage
=====

Simply run the Docker image, expose the web ports, and mount all necessary devices:

```
docker run -d \
    --name=node-makemkv \
    --restart=unless-stopped \
    -p 80:80 \
    --device /dev/sr0 \
    lasley/node-makemkv:latest
```

The above will launch NodeMakeMKV on port 80, and will expose the `/dev/sr0` device
to the container.


Build Arguments
===============

The following build arguments are available for customization:


| Name | Default | Description |
|------|---------|-------------|

Environment Variables
=====================

The following environment variables are available for your configuration
pleasure:

| Name | Default | Description |
|------|---------|-------------|
| `CONVERSION_PROFILE` | `/opt/node-makemkv/conversion_profile.xml` | Path to conversion profile |
| `DIR_OUT` | `/var/done` | Directory to save completed rips in |
| `HTTP_PORT` | 80 | Port that NodeMakeMKV should listen on |
| `OUTLIER_MODIFIER` | 0.7 | Used for automatic selection of tracks |
| `APP_KEY` | | For those of us that purchased MakeMKV. Leaving empty will use the current beta key. |

Known Issues / Roadmap
======================

* The `udev` module that Node MakeMKV uses does not support kernel udev
  messages, which is all that Docker does support. Due to this, the automatic
  recognition for the changing of discs does not work. Use `/refresh/device/path`
  to trigger an initial scan, which will show the disc panel in the UI and allow
  for subsequent scans. For example, `http://localhost:80/refresh/dev/sr0` would
  be the refresh command for the usage example.


Bug Tracker
===========

Bugs are tracked on [GitHub Issues](https://github.com/lasley/docker-node-makemkv/issues).
In case of trouble, please check there to see if your issue has already been reported.
If you spotted it first, help us smash it by providing detailed and welcomed feedback.

Credits
=======

Contributors
------------

* Dave Lasley <dave@dlasley.net>

