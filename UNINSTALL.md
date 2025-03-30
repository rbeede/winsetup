```
winget uninstall "Microsoft OneDrive"
winget uninstall "Solitaire & Casual Games"
winget uninstall "OneNote for Windows 10"
winget uninstall "Microsoft Clipchamp"
winget uninstall "News"
winget uninstall "MSN Weather"
winget uninstall "Xbox"
winget uninstall "Get Help"
winget uninstall "Microsoft Sticky Notes"
winget uninstall "Outlook for Windows"
winget uninstall "Microsoft People"
winget uninstall "Power Automate"
winget uninstall "Snipping Tool"
winget uninstall "Microsoft.DevHome"
winget uninstall "Windows Camera"
winget uninstall "Windows Notepad"
winget uninstall "Game Bar"
winget uninstall "Phone Link"
winget uninstall "Windows Media Player"
winget uninstall "Quick Assist"
winget uninstall "Microsoft Teams"
winget uninstall "Spotify Music"
winget uninstall "Microsoft To Do"

# Copilot disabled
winget uninstall 9nht9rb2f4hd

Get-ChildItem -Path $env:appdata\Microsoft\Windows\SendTo -Exclude "*Desktop*" | Remove-Item -Verbose

# Uninstalls after a reboot
Get-AppxPackage -all Microsoft.Getstarte* | Remove-AppxPackage -All
# Removes from program menu only
Get-AppxPackage *Microsoft.WindowsNotepad* | Remove-AppxPackage
Disable-WindowsOptionalFeature -Online -FeatureName "WindowsMediaPlayer" -NoRestart

```
