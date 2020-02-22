# batnotify

Notification script for low battery warning.

## Installation

```
cp ./batnotify ~/.local/bin
cp ./batnotify.service ~/.config/systemd/user

systemctl --user enable batnotify.service
systemctl --user start batnotify.service
```
