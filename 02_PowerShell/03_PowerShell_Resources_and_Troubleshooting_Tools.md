# ⚙️ PowerShell Resources & Troubleshooting Tools

*Module 02 — PowerShell | Supplemental*

---

## 🎯 Learning Objectives

- Use event log analysis for process tracking
- Apply troubleshooting commands and techniques
- Reference environment IPs and resources

---

# ⚙️ PowerShell Resources & Troubleshooting Tools
Interactive notebook of tips, commands, and real-world techniques for PowerShell automation and monitoring.

## 🌐 Reference Environment IPs
- **Marking Page**: [Tech College Site](https://cted.cybbh.io/tech-college/cttsb/PROG/prog/index.html)
- **CTFD Portal** (PowerShell challenge box): `10.50.139.229`
- **Student Exercise VM**: `10.50.132.145`
- **Admin / Domain Controller**: `10.50.170.252`

## 🛡️ Event Log Analysis (4688 – New Process Created)
Use this to look for executable launches tracked in Windows Security Log:

```powershell
(Get-WinEvent -LogName Security -FilterXPath "*[System[(EventID=4688)]]" -MaxEvents 40).Message
```

## 🧬 Cmdlet Aliases and Reverse Lookup
Use `Get-Alias -Definition` to find what aliases map to a specific cmdlet.

```powershell
Get-Alias -Definition Get-Process
Get-Alias -Definition Get-ChildItem
Get-Alias -Definition Get-Command
```

## ✍️ Creating or Inspecting Your PowerShell Profile
Useful to customize your startup behavior.

Check profile path & create a simple one-liner profile:

```powershell
$PROFILE | Select-Object *

New-Item -Type File -Value "Get-Process" -Name "profile.ps1" -Path "C:\\Program Files\\PowerShell\\7"
```

## 📊 Sorting Objects in PowerShell
Default sort vs custom property sort with descending flag.

```powershell
# Default sort (unspecified)
Get-ChildItem | Sort-Object

# Sort by file size descending
Get-ChildItem | Sort-Object -Property Length -Descending
```

## 🌐 Sort and Filter TCP Connections by IP
Use this to find active remote sessions or identify unusual traffic.

```powershell
# Top 10 Remote IPs sorted descending
Get-NetTCPConnection |
Select-Object RemoteAddress, RemotePort, State |
Sort-Object -Property RemoteAddress -Descending |
Select-Object -First 10
```

```powershell
# Same, but sorted ascending
Get-NetTCPConnection |
Select-Object RemoteAddress, RemotePort, State |
Sort-Object -Property RemoteAddress |
Select-Object -First 10
```

## 🔍 Identify Process from Port (Ex: Port 8080)
Map a specific port back to a process ID, then resolve its name:

```powershell
$pid = Get-NetTCPConnection -LocalPort 8080 | Select-Object -ExpandProperty OwningProcess
Get-Process -Id $pid
```


---

[⬆️ Back to Module Index](../README.md)
