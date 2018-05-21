# Ardour Control

OSC Control Surface for Ardour. Based on Len Ovens' control surface.

## Requirements

- Ardour 5.12
- [Open Stage Control](https://github.com/jean-emmanuel/open-stage-control)

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
<<<<<<< HEAD
=======

## Troubleshooting

If the interface doesn't sync properly, try increasing the udp buffer size :
https://www.systutorials.com/241303/how-to-enlarge-linux-udp-buffer-size/
```bash
# check buffer size
/proc/sys/net/core/rmem_default

# change buffer size
sudo sysctl -w net.core.rmem_default=262144


```
## Screenshots
>>>>>>> 6932dba69fd9e1ea6fd9b054f5a658953b43eb41

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


