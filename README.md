# pathfinder-systemd
Starknet pathfinder configuration to run as systemd service

## Prerequisites

- Docker
- Ubuntu or Debian-like distribution

## Install

1. Create user who will execute the client and add to the docker group
```
useradd -s /bin/false starknode
usermod -a -G docker starknode
```
2. Create directory to store node data. You could also mount an external disk.
```
mkdir /mnt/starkdata
chown starknode.starknode /mnt/starkdata
```
3. Replace `INFURAKEY` in `starknode.service` with yours. If you don't have, [create](https://infura.io/register) a free one.
4. Copy `starknode.service` to `/etc/systemd/system`, reload system services and enable the service on restart
```
cp starknode.starknode /etc/systemd/system
systemctl daemon-reload
systemctl enable starknode
```
5. Start the node and enjoy
```
service starknode start
```

To monitor run
```
journalctl -u starknode -f
```

## Contributing
Just open a PR

