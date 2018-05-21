# Ardour Control

OSC Control Surface for Ardour. Based on Len Ovens' control surface.

## Requirements

- Ardour 5.11
- [Open Stage Control](https://github.com/jean-emmanuel/open-stage-control) (>= v0.28.2)

## Features

- all tracks (using banking)
- transport
- plugins (ladspa-like generic ui)
- sends/receives

## Getting started

- Enable OSC in ardour
- launch Open Stage Control :

```bash
# Running from sources:
npm start -- -l path/to/ardour.js -c path/to/ardour-plugins-module.js -s 127.0.0.1:3819

# Running from binaries:
open-stage-control -- -l path/to/ardour.js -c path/to/ardour-plugins-module.js -s 127.0.0.1:3819

# Where 127.0.0.1:3819 is ardour's listening 'ip address:osc port'

```

## Know bug
- With 5 or more ardour's channels, some OSC messages can be drop by the kernel. For fix it change the buffer size with :
    - for a temporary fix
    ```
    # echo '1703936' > /proc/sys/net/core/rmem_default
    ```
    - or a permanent fix
    ```
    # echo 'net.core.rmem_default='1703936' >> /etc/sysctl.d/11-osc-net-patch.conf
    ```


