FreeBSD
========

### Updating
```
freebsd-update fetch
freebsd-update install
```

Starting point for `/etc/rc.conf`

```
hostname="fbsd1.joshrendek.com"
sshd_enable=YES
pf_enable="YES"
pf_rules="/etc/pf.conf"
pflog_logfile="/var/log/pflog"
pf_flags=""
static_routes=linklocal
ezjail_enable=YES
cloned_interfaces="lo1"
ipv4_addrs_lo1="192.168.1.1-9/29"
haproxy_enable=YES
linux_enable="YES"
syslogd_enable="YES"
syslogd_flags="-ss -C"
```

### Enable PF (firewall)


`/etc/pf.conf`:
```
external_if="vtnet0"
jail_if="lo1"

IP_PUBLIC="(PUBLIC_IP)"
IP_JAIL_WWW="192.168.1.1" # the first jail you made on this IP

NET_JAIL="192.168.1.0/24"

PORT_WWW="{80,443}"

scrub in all

# nat jail traffic
nat pass on $external_if from $NET_JAIL to any -> $IP_PUBLIC

# web forward
rdr pass on $external_if proto tcp from any to $IP_PUBLIC port $PORT_WWW -> $IP_JAIL_WWW

# demo only, passing all traffic
pass out
pass in
```

### Creating a local network ontop of a lo0 clone (loopback)

Add to `/etc/rc.conf`:
``` 
cloned_interfaces="lo1"
ipv4_addrs_lo1="192.168.1.1-9/29"
```


### Enable Jails

Add to `/etc/rc.conf`:
```
ezjail_enable=YES
```

`pkg install ezjail`

#### Create a jail

```
ezjail-admin create wordpress 192.168.1.1
ezjail-admin start wordpress
```

#### Access the jail
`ezjail-admin console wordpress`

Make sure `/etc/resolv.conf` has something like:
```
nameserver 8.8.8.8
```


Ensure networking works by installing the pkg command by just typing `pkg`



