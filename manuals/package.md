# Installed Packages

### Argon

Refer to :
<https://github.com/jerrykuku/luci-theme-argon>

```c
// Install Pre-requisite
opkg install luci-compat luci-lib-ipkg

// Download the package
wget --no-check-certificate https://github.com/jerrykuku/luci-theme-argon/releases/download/v2.3.1/luci-theme-argon_2.3.1_all.ipk

// Install the package
opkg install luci-theme-argon*.ipk
```

### Openclash

Refer to :
<https://github.com/vernesong/OpenClash>

```c
// Install Pre-requisite

// Note : if you don't know what your firewall is, just run both command is fine
// iptables
opkg install coreutils-nohup bash iptables dnsmasq-full curl ca-certificates ipset ip-full iptables-mod-tproxy iptables-mod-extra libcap libcap-bin ruby ruby-yaml kmod-tun kmod-inet-diag unzip luci-compat luci luci-base
// nftables
opkg install coreutils-nohup bash dnsmasq-full curl ca-certificates ipset ip-full libcap libcap-bin ruby ruby-yaml kmod-tun kmod-inet-diag unzip kmod-nft-tproxy luci-compat luci luci-base

// Install the dnsmasq-full
opkg install dnsmasq-full

// If failed to install the dnsmasq-full
// Remove the dnsmasq, then install the dnsmasq-full
opkg remove dnsmasq

// Downloading the package
wget --no-check-certificate https://github.com/vernesong/OpenClash/releases/download/v0.46.003-beta/luci-app-openclash_0.46.003-beta_all.ipk

// Installing the package
opkg install luci-app-openclash*.ipk
```

### Passwall

It still private repo that build by radenku, will refer to the official as soon as i can

```c
// Add radenku's repository
// Please read customfeeds

// Installing the package
opkg install luci-app-passwall

// Installing the protocol
opkg install v2ray-extra v2ray-geoip v2ray-geosite v2ray-ctl xray-geodata
```

### TTYd (Terminal on LuCI)

```c
// Note : the configuration for auto root login is on literature

// Installing the package
opkg install luci-app-ttyd
```

### USB Tether

Refer to : <https://openwrt.org/docs/guide-user/network/wan/smartphone.usb.tethering>

```c
// A common protocol for Android based devices for tethering via USB is RNDIS
opkg install kmod-usb-net-rndis

// if you don't have a `usb0` interface come up or device keeps disconnecting
opkg install kmod-usb-net-cdc-ncm kmod-usb-net-cdc-eem kmod-usb-net-cdc-ether kmod-usb-net-cdc-subset

// For Huawei Devices
opkg install kmod-usb-net-huawei-cdc-ncm

// Extra steps depending on USB type and drivers for your router
opkg install kmod-nls-base kmod-usb-core kmod-usb-net kmod-usb-net-cdc-ether kmod-usb2

// For iOS Device
opkg install kmod-usb-net-ipheth usbmuxd libimobiledevice usbutils
// Call usbmuxd
usbmuxd -v
// Add usbmuxd to autostart
sed -i -e "\$i usbmuxd" /etc/rc.local
```

### Atheros 9xxx Wireless Module

```c
// Installing essentials for Atheros 9xxx Chipset Module
opkg install ath9k-htc-firmware btrfs-progs hostapd hostapd-utils kmod-ath kmod-ath9k kmod-ath9k-common kmod-ath9k-htc kmod-cfg80211 kmod-crypto-acompress kmod-crypto-crc32c kmod-crypto-hash kmod-fs-btrfs kmod-mac80211 wireless-tools wpa-cli wpa-supplicant
```
