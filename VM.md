Notes for specific differences when configuration a virtual machine Windows OS guest.

1. GPO 	Computer Configuration -> Administrative Templates -> Windows Components -> Windows Update
   * No auto-restart with logged on users for scheduled automatic updates installations
   * Configure Automatic Updates
1. Power Settings
   * Never dim display
1. `powercfg /H OFF`
1. Compact the virtual disk size
```
sdelete64.exe -z C:

defrag C: /H /D
defrag C: /H /X
defrag C: /H /L
```
   - Remove any existing snapshots
   - Undoing BitLocker temporarily allows a VMWare Workstation guest with vTPM (and forced VMware Encryption) to successfully VMware "compact"
   - `manage-bde -off C:`
   - Power off VM, do VMware disk compact
   - Power back on VM
   - `manage-bde -on C: -usedspaceonly`
     - If the encryption auto-started at boot you may need to do -off again then this command
     - `for /l %i in () do @(manage-bde -status c: & timeout /t 5)`
