# Basic Configuration

### Personalization

```c
// Changing Board Name on Overview

// /etc/rc.local
echo "kuu's Development Board" > /tmp/sysinfo/model
```

### Custom Mirror

```c
// Radenku custom repository
sed -i 's/option check_signature/# option check_signature/g' /etc/opkg.conf

echo "src/gz custom_generic https://raw.githubusercontent.com/lrdrdn/my-opkg-repo/main/generic" >> /etc/opkg/customfeeds.conf

echo "src/gz custom_arch https://raw.githubusercontent.com/lrdrdn/my-opkg-repo/main/$(grep "OPENWRT_ARCH" /etc/os-release | awk -F '"' '{print $2}')" >> /etc/opkg/customfeeds.conf
```

### TTY

```c
// auto login on zsh terminal

/bin/login -f root
```

### TTL

Refers to :
<https://forum.openwrt.org/t/working-nftables-rule-for-ttl-in-22-03/144838>

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
// Remove the bracket {} if using only one interface
chain mangle_postrouting_ttl65 {
    type filter hook postrouting priority 300; policy accept;
    oifname { "usb0", "wwan0", "eth1" } counter ip ttl set 65
}

chain mangle_prerouting_ttl65 {
    type filter hook prerouting priority 300; policy accept;
    iifname { "usb0", "wwan0", "eth1" } counter ip ttl set 65
}
```
