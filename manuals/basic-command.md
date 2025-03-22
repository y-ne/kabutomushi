# Basic Command on OpenWRT

### Package Manager related

```bash
// Update the package mirror
opkg update

// install package
opkg install <package-name>

// uninstall package
opkg remove <package-name>
```

### Restart Firewall4

```bash
// same function, choose one
fw4 reload
service firewall reload
/etc/init.d/firewall reload
```

### Sending AT commands via serial to a modem

```bash
picocom --echo -b 9600 /dev/ttyUSB0
```
