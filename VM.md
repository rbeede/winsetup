Notes for specific differences when configuration a virtual machine Windows OS guest.

GPO 	Computer Configuration -> Administrative Templates -> Windows Components -> Windows Update
* No auto-restart with logged on users for scheduled automatic updates installations
* Configure Automatic Updates

Power Settings
* Never dim display

`powercfg /H OFF`

Prepare for disk compact for VMWare

```
defrag C: /H /D
defrag C: /H /X
```

clean power off

Compact/Shrink the disk
