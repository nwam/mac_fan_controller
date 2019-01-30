# Control a Mac's fan speeds on Linux
This script sets your Macbook's fan speed based on the highest CPU temperature. It currently only supports one fan, but can easily be generalized to work with n fans. This script was made to avoid an expensive hardware fix on a Macbook with a broken motherboard temperature sensor.

## Installation
Run `sudo setup.sh` then run `sudo crontab -e` and append the following line to the file that opens:
```
* * * * * /usr/local/bin/run_every_x_seconds 10 /usr/local/bin/fan_control
```

This will make `fan_control` run every 10 seconds.

## System-specific changes
You Macbook might store its SMC files under a different path. If the directory `/sys/devices/platform/applesmc.768/` does not exist, you should change the line
```
APPLE_SMC = '/sys/devices/platform/applesmc.768/'
```
in `fan_control` to point the proper directory (hopfully it is as simple as a different number after `applesmc`) then re-run `sudo setup.sh`.
