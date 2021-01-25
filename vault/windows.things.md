---
id: 8bd875ac-64e8-4967-85db-84f633ce2656
title: Windows Things
desc: ''
updated: 1611578865255
created: 1611517126737
---

## Trouble installing apps from Microsoft Store?

Method 1: Run the SFC

Open PowerShell as administrator

```bash
sfc /scannow
```

Method 2: Open PowerShell as administrator

```bash
Get-AppXPackage | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}
```
