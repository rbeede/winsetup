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

# Long filename support (MAX_PATH)
New-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\FileSystem" -Name "LongPathsEnabled" -Value 1 -PropertyType DWORD -Force

# I do not need OneDrive as a default, stop nagging me Microsoft Office
# Group Policy: Prevent the usage of OneDrive for file storage
REG ADD "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\OneDrive" /v "DisableFileSyncNGSC" /t REG_DWORD /f /d 1

# Conflicts with VMs
REG ADD "HKEY_CURRENT_USER\Software\Microsoft\Clipboard" /v "EnableClipboardHistory" /t REG_DWORD /f /d 0

# Disable pop-up Logitech Options+ software
REG DELETE HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Run /v "Logitech Download Assistant" /f

# Better time zone management between Windows / Linux
REG ADD HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\TimeZoneInformation /v "RealTimeIsUniversal" /t REG_DWORD /f /d 1

# Hide recycle bin icon on desktop
REG ADD HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\HideDesktopIcons\NewStartPanel /v "{645FF040-5081-101B-9F08-00AA002F954E}" /t REG_DWORD /f /d 1


# Bitlocker Enhanced PINs
REG ADD "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\FVE" /v "UseEnhancedPin" /t REG_DWORD /f /d 1
REG ADD "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\FVE" /v "UseTPMPIN" /t REG_DWORD /f /d 1
REG ADD "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\FVE" /v "UseAdvancedStartup" /t REG_DWORD /f /d 1
# Disable less secure options
REG ADD "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\FVE" /v "EnableBDEWithNoTPM" /t REG_DWORD /f /d 0
REG ADD "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\FVE" /v "UseTPM" /t REG_DWORD /f /d 0
REG ADD "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\FVE" /v "UseTPMKey" /t REG_DWORD /f /d 0
REG ADD "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\FVE" /v "UseTPMKeyPIN" /t REG_DWORD /f /d 0
 ```


### Desktop

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
- Manually set (cannot regedit) to open txt files

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

###### Update: Block all incoming by default

Using the blockinboundalways (Block all incoming connections, including those in the list of allowed apps) setting breaks IPv6 due to bugs in Microsoft Windows dating back years and versions. Even on a dominately IPv4 network the OS may try to use a local IPv6 address for your local DNS resolver. This results in failed connections. Currently you must not use this setting and manually curate (as it changes over time) the firewall ingress list. See also <a href="https://www.rodneybeede.com/computer%20problems/windows_firewall_-_block_all_incoming_connections_-_breaks_ipv6.html">https://www.rodneybeede.com/computer%20problems/windows_firewall_-_block_all_incoming_connections_-_breaks_ipv6.html</a>.

```
:: Not safe due to breaking DNS and IPv6
:: netsh advfirewall set All firewallpolicy blockinboundalways,allowoutbound
```

```

```
