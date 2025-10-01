# Windows System Configuration Guide

## Python Environment Management
### Display Python Versions
```powershell
py -0
```

### Locate Virtual Environments
#### PowerShell
```powershell
Get-ChildItem -Recurse -Filter "pyvenv.cfg" -ErrorAction SilentlyContinue -Path C:\ | Select-Object FullName
```
#### CMD
```cmd
dir C:\pyvenv.cfg /s /b
```

## Storage Management
### List Top 20 Directories by Size
```powershell
Get-ChildItem -Directory | Select-Object Name,@{N='Size(GB)';E={((Get-ChildItem $_.FullName -Recurse -File -ErrorAction SilentlyContinue | Measure-Object -Property Length -Sum).Sum / 1GB)}} | Sort-Object 'Size(GB)' -Descending | ForEach-Object { [PSCustomObject]@{ Name = $_.Name; 'Size(GB)' = '{0:N2}' -f $_.'Size(GB)' }} | Select-Object -First 20
```

## System Health Diagnostics
### Battery Status
Generate battery health report:
```powershell
powercfg /batteryreport /output "$env:USERPROFILE\Desktop\battery-report.html"
```
Note: Report will be saved to Desktop

### Storage Health
Check disk status:
```powershell
Get-PhysicalDisk | Format-Table FriendlyName, MediaType, Size, HealthStatus -AutoSize
```
Alternative WMI method:
```powershell
wmic diskdrive get Model,SerialNumber,Status,MediaType
```

### Storage Performance
Check disk reliability:
```powershell
Get-PhysicalDisk | Get-StorageReliabilityCounter
```

### Performance Monitoring
Check top CPU processes:
```powershell
Get-Process | Sort-Object CPU -Descending | Select-Object -First 10 Name,CPU,WorkingSet
```
Check memory status:
```powershell
Get-CimInstance Win32_OperatingSystem | Select-Object TotalVisibleMemorySize,FreePhysicalMemory
```
