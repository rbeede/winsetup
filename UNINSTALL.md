```
winget uninstall --disable-interactivity --accept-source-agreements --all "Microsoft OneDrive"
winget uninstall --disable-interactivity --accept-source-agreements --all "Solitaire & Casual Games"
winget uninstall --disable-interactivity --accept-source-agreements --all "OneNote for Windows 10"
winget uninstall --disable-interactivity --accept-source-agreements --all "Microsoft Clipchamp"
winget uninstall --disable-interactivity --accept-source-agreements --all "News"
winget uninstall --disable-interactivity --accept-source-agreements --all "MSN Weather"
winget uninstall --disable-interactivity --accept-source-agreements --all "Xbox"
winget uninstall --disable-interactivity --accept-source-agreements --all "Get Help"
winget uninstall --disable-interactivity --accept-source-agreements --all "Microsoft Sticky Notes"
winget uninstall --disable-interactivity --accept-source-agreements --all "Outlook for Windows"
winget uninstall --disable-interactivity --accept-source-agreements --all "Microsoft People"
winget uninstall --disable-interactivity --accept-source-agreements --all "Power Automate"
winget uninstall --disable-interactivity --accept-source-agreements --all "Snipping Tool"
winget uninstall --disable-interactivity --accept-source-agreements --all "Microsoft.DevHome"
winget uninstall --disable-interactivity --accept-source-agreements --all "Windows Camera"
winget uninstall --disable-interactivity --accept-source-agreements --all "Windows Notepad"
winget uninstall --disable-interactivity --accept-source-agreements --all "Game Bar"
winget uninstall --disable-interactivity --accept-source-agreements --all "Phone Link"
winget uninstall --disable-interactivity --accept-source-agreements --all "Windows Media Player"
winget uninstall --disable-interactivity --accept-source-agreements --all "Quick Assist"
winget uninstall --disable-interactivity --accept-source-agreements --all "Microsoft Teams"
winget uninstall --disable-interactivity --accept-source-agreements --all "Spotify Music"
winget uninstall --disable-interactivity --accept-source-agreements --all "Microsoft To Do"

# Copilot disabled
winget uninstall --disable-interactivity --accept-source-agreements --all 9nht9rb2f4hd

Get-ChildItem -Path $env:appdata\Microsoft\Windows\SendTo -Exclude "*Desktop*" | Remove-Item -Verbose

# Uninstalls after a reboot
Get-AppxPackage -all Microsoft.Getstarte* | Remove-AppxPackage -All
# Removes from program menu only
Get-AppxPackage *Microsoft.WindowsNotepad* | Remove-AppxPackage
Disable-WindowsOptionalFeature -Online -FeatureName "WindowsMediaPlayer" -NoRestart

```
