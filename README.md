# random

## Git help

### Get nice logging

==> add 'lognice' as alias (~/.gitconfig)
```
[alias]
  lognice = log --graph  --decorate --format=format:'%C(yellow)%h%C(reset)%C(auto)%d%C(reset) %C(normal)%s%C(reset) %C(dim white)- %an%C(reset) %C(dim blue)(%ar)' --all
```


### Move existing tag to head
```
git push origin :refs/tags/<tagname>
git tag -fa <tagname>
git push origin master --tags
```


## Raspbery PI 

### Finding my pi on the network 

All raspberry devices MAC addresses started with B8:27:EB.
So, on *nix systems, this can be accomplished by executing the following command where 192.168.1.* will be your local network mask
```
sudo nmap -sP 192.168.1.0/24 | awk '/^Nmap/{ip=$NF}/B8:27:EB/{print ip}'
```

### Connecting a Computer to the Pi
Recent versions of Raspbian (which use dhcpcd) allow ssh to work over a link-local address and avahi (which is a zeroconf implementation) enables programs to discover hosts running on a local network.
You can easily connect from Linux and OS X with ssh pi@hostname.local (the default hostname is raspberrypi)
````
ssh pi@raspberrypi.local
````

