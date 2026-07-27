Run as Administrator

```
winget install --exact --id 7zip.7zip --accept-package-agreements --accept-source-agreements --silent --scope machine
winget install --exact --id Duplicati.Duplicati --accept-package-agreements --accept-source-agreements --silent --scope machine
winget install --exact --id Flameshot.Flameshot --accept-package-agreements --accept-source-agreements --silent --scope machine
winget install --exact --id Google.Chrome --accept-package-agreements --accept-source-agreements --silent --scope machine
winget install --exact --id Microsoft.PowerToys --accept-package-agreements --accept-source-agreements --silent --scope machine
winget install --exact --id Microsoft.WindowsTerminal --accept-package-agreements --accept-source-agreements --silent --scope machine
winget install --exact --id Mozilla.Firefox --accept-package-agreements --accept-source-agreements --silent --scope machine
winget install --exact --id Notepad++.Notepad++ --accept-package-agreements --accept-source-agreements --silent --scope machine
winget install --exact --id VideoLAN.VLC --accept-package-agreements --accept-source-agreements --silent --scope machine
winget install --exact --id WinDirStat.WinDirStat --accept-package-agreements --accept-source-agreements --silent --scope machine

winget install --exact --id BurntSushi.ripgrep.GNU --accept-package-agreements --accept-source-agreements --silent --scope machine
winget install --exact --id Microsoft.Coreutils --accept-package-agreements --accept-source-agreements --silent --scope machine
winget install --exact --id aria2.aria2 --accept-package-agreements --accept-source-agreements --silent --scope machine
winget install --exact --id jqlang.jq --accept-package-agreements --accept-source-agreements --silent --scope machine

@REM Has http2 support, but requires overriding Microsoft's built-in curl.exe version on PATH
winget install --exact --id cURL.cURL --accept-package-agreements --accept-source-agreements --silent --scope machine
@REM Do not use setx as it truncates at 1024 characters
set "KEY=HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Environment"
for /f "tokens=2,*" %A in ('reg query "%KEY%" /v Path ^| findstr /i "REG_"') do @set "SYSPATH=%B"
echo %SYSPATH%
reg add "%KEY%" /v Path /t REG_EXPAND_SZ /d "C:\Program Files\WinGet\Links;%SYSPATH%" /f
reg query "%KEY%"
echo PATH change will not be applied until logout or reboot

winget install --exact --id Microsoft.Office --accept-package-agreements --accept-source-agreements --silent --scope machine
```
