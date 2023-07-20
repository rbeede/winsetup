```
winget uninstall "3D Viewer"
winget uninstall "Paint 3D"
winget uninstall "Feedback Hub"
winget uninstall "Groove Music"
winget uninstall "Mail and Calendar"
winget uninstall "Microsoft OneDrive"
winget uninstall "Microsoft Solitaire Collection"
winget uninstall "Mixed Reality Portal"
winget uninstall "Movies & TV"
# not the same as Office Pro
winget uninstall Office
winget uninstall OneNote
winget uninstall Skype
winget uninstall "Sticky Notes"
winget uninstall "MSN Weather"
winget uninstall "Microsoft Tips"
winget uninstall "Windows Voice Recorder"
winget uninstall "Snip & Sketch"
winget uninstall "Xbox"
winget uninstall "Xbox TCUI"
winget uninstall "Xbox Game Bar Plugin"
winget uninstall "Xbox Game Bar"       
winget uninstall "Xbox Identity Provider"
winget uninstall "Xbox Game Speech Window"
winget uninstall "Spotify Music"
winget uninstall "Windows Maps"
winget uninstall "Windows Alarms & Clock"
winget uninstall "Microsoft Pay"
winget uninstall Cortana

# uninstalls after reboot

# Windows Fax and Scan
Remove-WindowsCapability -Name "Print.Fax.Scan~~~~0.0.1.0" -Online
Remove-WindowsCapability -Name "Microsoft.Windows.Notepad~~~~0.0.1.0" -Online
Remove-WindowsCapability -Name "Microsoft.Windows.WordPad~~~~0.0.1.0" -Online

# optionalfeatures
Disable-WindowsOptionalFeature -FeatureName Internet-Explorer-Optional-amd64 –Online -NoRestart
Disable-WindowsOptionalFeature -Online -FeatureName "WindowsMediaPlayer" -NoRestart
dism /online /Disable-Feature /FeatureName:WorkFolders-Client /Quiet /NoRestart
dism /online /Disable-Feature /FeatureName:Printing-XPSServices-Features /Quiet /NoRestart
dism /online /Disable-Feature /FeatureName:MicrosoftWindowsPowerShellV2 /Quiet /NoRestart
dism /online /Disable-Feature /FeatureName:MicrosoftWindowsPowerShellV2Root /Quiet /NoRestart

Remove-Printer -Name "Microsoft XPS Document Writer"
Remove-Printer -Name "Fax"

Get-ChildItem -Path $env:appdata\Microsoft\Windows\SendTo -Exclude "*Desktop*" | Remove-Item -Verbose
```
