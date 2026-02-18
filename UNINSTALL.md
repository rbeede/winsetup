```
winget uninstall --disable-interactivity "Microsoft OneDrive"
winget uninstall --disable-interactivity "Solitaire & Casual Games"
winget uninstall --disable-interactivity "OneNote for Windows 10"
winget uninstall --disable-interactivity "Microsoft Clipchamp"
winget uninstall --disable-interactivity "News"
winget uninstall --disable-interactivity "MSN Weather"
winget uninstall --disable-interactivity "Xbox"
winget uninstall --disable-interactivity "Get Help"
winget uninstall --disable-interactivity "Microsoft Sticky Notes"
winget uninstall --disable-interactivity "Outlook for Windows"
winget uninstall --disable-interactivity "Microsoft People"
winget uninstall --disable-interactivity "Power Automate"
winget uninstall --disable-interactivity "Snipping Tool"
winget uninstall --disable-interactivity "Microsoft.DevHome"
winget uninstall --disable-interactivity "Windows Camera"
winget uninstall --disable-interactivity "Windows Notepad"
winget uninstall --disable-interactivity "Game Bar"
winget uninstall --disable-interactivity "Phone Link"
winget uninstall --disable-interactivity "Windows Media Player"
winget uninstall --disable-interactivity "Quick Assist"
winget uninstall --disable-interactivity "Microsoft Teams"
winget uninstall --disable-interactivity "Spotify Music"
winget uninstall --disable-interactivity "Microsoft To Do"

# Copilot disabled
winget uninstall --disable-interactivity 9nht9rb2f4hd

Get-ChildItem -Path $env:appdata\Microsoft\Windows\SendTo -Exclude "*Desktop*" | Remove-Item -Verbose

# Uninstalls after a reboot
Get-AppxPackage -all Microsoft.Getstarte* | Remove-AppxPackage -All
# Removes from program menu only
Get-AppxPackage *Microsoft.WindowsNotepad* | Remove-AppxPackage
Disable-WindowsOptionalFeature -Online -FeatureName "WindowsMediaPlayer" -NoRestart

```
