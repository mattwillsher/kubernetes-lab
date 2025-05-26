## Linux DNS

Tested on Fedora with modifications because split DNS and stub on
systemd-resolved don't work as expected and result in lookup failures.

Task assumes `/etc/NetworkManager/NetworkManager.conf` contains:

```conf
[main]
dns=dnsmasq
```

and that is has been restarted `systemctl restart NetworkManager`
