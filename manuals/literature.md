# Basic Configuration

### Personalization

```c
// Changing Board Name on Overview

// /etc/rc.local
echo "kuu's Development Board" > /tmp/sysinfo/model
```

### TTY

```c
// auto login on zsh terminal

/bin/login -f root
```

### TTL

```c
// Specify TTL (time to live) for niche provider plan

// /etc/nftables.d/10-custom-filter-chains.nft

// add this line

// TTL 65 without specific interface
chain mangle_postrouting_ttl65 {
    type filter hook postrouting priority 300; policy accept;
    counter ip ttl set 65
}

chain mangle_prerouting_ttl65 {
    type filter hook prerouting priority 300; policy accept;
    counter ip ttl set 65
}

// TTL 65 with specific interface
chain mangle_postrouting_ttl65 {
    type filter hook postrouting priority 300; policy accept;
    oifname { "usb0", "wwan0", "eth1" } counter ip ttl set 65
}

chain mangle_prerouting_ttl65 {
    type filter hook prerouting priority 300; policy accept;
    iifname { "usb0", "wwan0", "eth1" } counter ip ttl set 65
}
```
