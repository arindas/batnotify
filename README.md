# batnotify
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
![init-systemd](https://img.shields.io/badge/init-systemd-brightgreen)

Notification script and systemd timer for triggering low battery notifications.

## How it works
We query battery state and charge percentage by reading from:
- `/sys/class/power_supply/BAT0/status`
- `/sys/class/power_supply/BAT0/capacity`

If the battery state is "discharging" and the current charge percentage is less than the
specified `${SAFE_BATTERY_LEVEL}`, we trigger a notification using `notify-send`

Now we run the script using a systemd service file. In order to repeatedly check
the status, we run a systemd timer for the corresponding service file.

## Installation

```sh
# clone the repo
git clone git@github.com:arindas/batnotify.git
cd batnotify/

# install the relevant files
cp ./batnotify ~/.local/bin
cp ./batnotify.service ~/.config/systemd/user
cp ./batnotify.timer ~/.config/systemd/user

# enable and start the systemd service timer
systemctl --user enable batnotify.timer
systemctl --user start batnotify.timer
```

## Uninstallation
```sh
# disable and stop the systemd service timer
systemctl --user disable batnotify.timer
systemctl --user stop batnotify.timer
```

## See also
- [`poweralertd`](https://sr.ht/~kennylevinsen/poweralertd/): Also handles power notifications for different wireless devices, in addition to main system power.
