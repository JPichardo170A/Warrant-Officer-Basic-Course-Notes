# 📄 System Process & Network Report – Expanded Edition

*Module 02 — PowerShell | Supplemental*

---

## 🎯 Learning Objectives

- Collect system data (processes, network connections)
- Generate formatted reports
- Automate system monitoring tasks

---

# 📄 PowerShell System Report Notebook – Expanded Edition
This notebook collects system data like running processes and TCP network connections, summarizes them, writes to both `.txt` and `.csv` files, and allows inline preview.

## 🔧 Step 1: Set Up Paths and Variables

```powershell
$reportPath = "$env:USERPROFILE\Desktop\System_Report.txt"
$csvFolder = "$env:USERPROFILE\Desktop\SystemCSV"

if (-not (Test-Path $reportPath)) {
    New-Item -Path $reportPath -ItemType File -Force | Out-Null
}
if (-not (Test-Path $csvFolder)) {
    New-Item -Path $csvFolder -ItemType Directory | Out-Null
}
```

## 🕒 Step 2: Add Header Info

```powershell
$timestamp = Get-Date -Format "yyyy-MM-dd HH:mm:ss"
$hostname = $env:COMPUTERNAME
$username = $env:USERNAME

Add-Content -Path $reportPath -Value "==== System Report ($timestamp) ===="
Add-Content -Path $reportPath -Value "Host: $hostname"
Add-Content -Path $reportPath -Value "User: $username`n"
```

## 📊 Step 3: Process Report with Count

```powershell
$procList = Get-Process | Select-Object Name, Id, CPU
$procCount = $procList.Count
Add-Content -Path $reportPath -Value "Total Running Processes: $procCount`n"
$procList | Out-String | Add-Content -Path $reportPath

$procList | Export-Csv -Path "$csvFolder\processes.csv" -NoTypeInformation
```

## 🌐 Step 4: TCP Connection Report + Summary

```powershell
$tcpList = Get-NetTCPConnection | Select-Object LocalAddress, LocalPort, RemoteAddress, RemotePort, State
Add-Content -Path $reportPath -Value "`n==== TCP Connections ===="
$tcpList | Out-String | Add-Content -Path $reportPath
$tcpList | Export-Csv -Path "$csvFolder\connections.csv" -NoTypeInformation
```

## 📈 Step 5: Summary of TCP States

```powershell
$stateSummary = Get-NetTCPConnection |
    Group-Object State |
    Select-Object Name, Count

Add-Content -Path $reportPath -Value "`n==== TCP State Counts ===="
$stateSummary | Format-Table | Out-String | Add-Content -Path $reportPath
```

## 📬 Step 6: Finish Report

```powershell
Add-Content -Path $reportPath -Value "`n====== END OF REPORT ======`n"
Write-Host "✅ Report written to: $reportPath"
```

## 🔎 Step 7: Optional – Preview Report Inline

```powershell
Get-Content -Path $reportPath | Out-Host
```


---

[⬆️ Back to Module Index](../README.md)
