Notes for specific differences when configuration a virtual machine Windows OS guest.

1. GPO 	Computer Configuration -> Administrative Templates -> Windows Components -> Windows Update
   * No auto-restart with logged on users for scheduled automatic updates installations
   * Configure Automatic Updates
1. Power Settings
   * Never dim display
1. `powercfg /H OFF`
1. Compact the virtual disk size
```
defrag C: /H /D
defrag C: /H /X
defrag C: /H /L
```
