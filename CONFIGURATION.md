### Privacy Settings

```

```

### Desktop

- Hide recycle bin from desktop
- Enlarge desktop icon size
- Desktop background
- Set user profile picture

### Taskbar

- Pin Chrome to taskbar
- Hide taskbar Search
- Show UTC clock as secondary clock


### Application Specific Settings

#### Notepad++

- Compare
- JSON Tools
- XML Tools
- View menu -> Zoom
- 120 col bar Margins/Border/Edge
- Backup - disable session

#### Google Chrome

- Disable auto-fill of passwords
  * chrome://password-manager/settings
- AdBlock Plus
- BitWarden
- Default browser

#### 7-Zip

- Associate with system
- Grid rows
- Cut down right click context

#### Explorer

- Turn off Group By
- Expand the ribbon bar

- Add local printer


### Power Settings

```
powercfg /setactive 8c5e7fda-e8bf-4a96-9a85-a6e23a8c635c
```

- Screensaver is disabled by default
- High performance power scheme should set no sleep on AC by default


### Disable Restore Points

```
Disable-ComputerRestore -Drive "C:\"
vssadmin delete shadows /all
```


### Configure Windows firewall

Block all incoming by default

```
netsh advfirewall set All firewallpolicy blockinboundalways,allowoutbound
```