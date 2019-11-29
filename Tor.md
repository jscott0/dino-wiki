# Run
If you configured a system-wide SOCKS proxy, Dino will honor that setting.

Otherwise, you can specifically set Dino to use Tor by starting it with
```
$ torsocks dino
```

# DNS

You can have your system route DNS requests through Tor by writing `nameserver 127.0.0.1` into your `/etc/resolv.conf`.

XMPP uses `SRV` records by default, which cannot be queried through Tor. As a fallback, XMPP uses `A` records, which **can** be queried through Tor. Thus, make sure the domain of your server has an `A` record set to the IP of the XMPP server. Public servers are very frequently set up accordingly.

# Anonymity and privacy distributions

## Tails
* Download and install the Dino Debian package from [OBS](https://software.opensuse.org/download.html?project=network:messaging:xmpp:dino&package=dino).
* Start Dino from the console with `torsocks dino`.
* Don't worry about DNS - Tails forces all traffic through Tor.