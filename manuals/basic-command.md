# Basic Command on OpenWRT

### Package Manager related

```c
// Update the package mirror
opkg update

// install package
opkg install <package-name>

// uninstall package
opkg remove <package-name>
```

### Restart Firewall4

```c
// same function, choose one
fw4 reload
service firewall reload
/etc/init.d/firewall reload
```
