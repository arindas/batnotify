# batnotify

Notification script and systemd timer for triggering low battery notifications.

## How it works
We query battery state and charge percentage using `upower`. If the battery
state is "discharging" and the current charge percentage is less than the
specified `${SAFE_BATTERY_LEVEL}`, we trigger a notification using `notify-send`

## Installation

```
cp ./batnotify ~/.local/bin
cp ./batnotify.service ~/.config/systemd/user
cp ./batnotify.timer ~/.config/systemd/user

systemctl --user enable batnotify.timer
systemctl --user start batnotify.timer
```
