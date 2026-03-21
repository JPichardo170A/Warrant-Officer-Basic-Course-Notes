# 🧾 Remote System Reporting & Service Check

*Module 02 — PowerShell | Supplemental*

---

## 🎯 Learning Objectives

- Generate process and network reports on remote systems
- Check and validate remote services

---

# 🧾 Remote System Reporting & Service Check – Deluxe Edition
This notebook creates a process & network report on a remote computer, pulls the file locally, checks services, and validates/report results.

## 📄 Step 1: Generate Report File on Remote Computer

```powershell
$lastname = "Pichardo"
$classnumber = "25-003"
$remoteComputer = "10.50.132.145"
$remoteTxtName = "${lastname}_${classnumber}.txt"
$remoteTxtPath = "C:\\Users\\student\\Documents\\$remoteTxtName"

Invoke-Command -ComputerName $remoteComputer -Credential $creds -ScriptBlock {
    param($outputPath)

    if (-not (Test-Path $outputPath)) {
        New-Item -Path $outputPath -ItemType File -Force | Out-Null
    }

    $timestamp = Get-Date -Format "yyyy-MM-dd HH:mm:ss"
    $processes = Get-Process | Select-Object Name, Id, CPU
    $networkInfo = Get-NetIPAddress | Select-Object InterfaceAlias, IPAddress, AddressFamily

    Add-Content -Path $outputPath -Value "==== Report at $timestamp ===="
    Add-Content -Path $outputPath -Value "`n--- Running Processes ---"
    $processes | Out-String | Add-Content -Path $outputPath

    Add-Content -Path $outputPath -Value "`n--- Network Information ---"
    $networkInfo | Out-String | Add-Content -Path $outputPath
    Add-Content -Path $outputPath -Value "`n==================================`n"
    Write-Host "✅ Report created successfully."
} -ArgumentList $remoteTxtPath
```

## 📦 Step 2: Pull Remote File to Local System

```powershell
$localTxtPath = "C:\\Users\\cvte1\\Documents\\$remoteTxtName"

$fileContent = Invoke-Command -ComputerName $remoteComputer -Credential $creds -ScriptBlock {
    param($path)
    Get-Content -Path $path
} -ArgumentList $remoteTxtPath

Set-Content -Path $localTxtPath -Value $fileContent
Write-Host "✅ File successfully pulled to: $localTxtPath"
```

## 🧾 Step 3: Display Retrieved Report

```powershell
Get-Content -Path $localTxtPath
```

## 🛡️ Step 4: Check Microsoft Defender Status

```powershell
$remoteService = "WinDefend"

Invoke-Command -ComputerName $remoteComputer -Credential $creds -ScriptBlock {
    param($serviceName)
    $service = Get-Service -Name $serviceName -ErrorAction SilentlyContinue

    if ($null -eq $service) {
        "❌ Microsoft Defender service ('$serviceName') not found."
    }
    elseif ($service.Status -eq 'Running') {
        "✅ Microsoft Defender is currently RUNNING."
    }
    else {
        "⚠️ Defender is INSTALLED but NOT running. Status: $($service.Status)"
    }
} -ArgumentList $remoteService
```

## 🔍 Step 5: Optional – List All Running Services

```powershell
$runningServices = Invoke-Command -ComputerName $remoteComputer -Credential $creds -ScriptBlock {
    Get-Service | Where-Object { $_.Status -eq 'Running' } | Select-Object Name, DisplayName, Status
}
$runningServices
```

## 💾 Step 6: Export Service List to CSV

```powershell
$csvPath = "C:\\Users\\cvte1\\Documents\\RunningServices.csv"
$runningServices | Export-Csv -Path $csvPath -NoTypeInformation
Write-Host "✅ Export complete: $csvPath"
```


---

[⬆️ Back to Module Index](../README.md)
