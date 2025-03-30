### Registry

```
REG ADD HKCU\Software\Policies\Microsoft\Windows\WindowsCopilot /v "TurnOffWindowsCopilot" /t REG_DWORD /f /d 1

REG ADD HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\Personalization /v "NoLockScreen" /t REG_DWORD /f /d 1

REG ADD "HKCU\Control Panel\Keyboard" /v PrintScreenKeyForSnippingEnabled /t REG_DWORD /d 0 /f

# Privacy
REG ADD HKCU\Software\Microsoft\Windows\CurrentVersion\AdvertisingInfo /v "Enabled" /t REG_DWORD /f /d 0
REG ADD "HKCU\Control Panel\International\User Profile" /v "HttpAcceptLanguageOptOut" /t REG_DWORD /f /d 1
REG ADD "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v "Start_TrackProgs" /t REG_DWORD /f /d 0

REG ADD "HKCU\Software\Microsoft\Windows\CurrentVersion\ContentDeliveryManager" /v "SubscribedContent-338393Enabled" /t REG_DWORD /f /d 0
REG ADD "HKCU\Software\Microsoft\Windows\CurrentVersion\ContentDeliveryManager" /v "SubscribedContent-353694Enabled" /t REG_DWORD /f /d 0
REG ADD "HKCU\Software\Microsoft\Windows\CurrentVersion\ContentDeliveryManager" /v "SubscribedContent-353696Enabled" /t REG_DWORD /f /d 0

New-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\FileSystem" -Name "LongPathsEnabled" -Value 1 -PropertyType DWORD -Force

# I do not need OneDrive as a default, stop nagging me Microsoft Office
# Group Policy: Prevent the usage of OneDrive for file storage
REG ADD "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\OneDrive" /v "DisableFileSyncNGSC" /t REG_DWORD /f /d 1

# Conflicts with VMs
REG ADD "HKEY_CURRENT_USER\Software\Microsoft\Clipboard" /v "EnableClipboardHistory" /t REG_DWORD /f /d 0

# Disable pop-up Logitech Options+ software
REG DELETE HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Run /v "Logitech Download Assistant"
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
