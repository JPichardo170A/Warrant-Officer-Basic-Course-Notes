# 🚀 PowerShell Remote Operations – Pro Edition

*Module 02 — PowerShell | Supplemental*

---

## 🎯 Learning Objectives

- Automate remote reporting and data retrieval
- Validate remote system configurations
- Use `Invoke-Command` for remote operations

---

# 🚀 PowerShell Remote Operations – Pro Edition
Automate reporting, retrieve remote data, and validate services securely via PowerShell remoting.

This notebook is designed to:
- Generate a report file on a remote system
- Pull that report to the local host
- Validate if critical services (like Defender) are running
- Log and export results

## 🌐 Step 1: Set Up Variables

```powershell
$lastname = "Pichardo"
$classnumber = "25-003"
$remoteComputer = "10.50.132.145"
$remoteTxtName = "${lastname}_${classnumber}.txt"
$remoteTxtPath = "C:\\Users\\student\\Documents\\$remoteTxtName"
$localTxtPath  = "C:\\Users\\cvte1\\Documents\\$remoteTxtName"
```

## 📝 Step 2: Create Remote Report File
Generates a .txt file containing process and network info from the remote host.

```powershell
Invoke-Command -ComputerName $remoteComputer -Credential $creds -ScriptBlock {
    param($outputPath)

    try {
        if (-not (Test-Path $outputPath)) {
            New-Item -Path $outputPath -ItemType File -Force | Out-Null
        }

        $timestamp   = Get-Date -Format "yyyy-MM-dd HH:mm:ss"
        $processes   = Get-Process | Select-Object Name, Id, CPU
        $netInfo     = Get-NetIPAddress | Select-Object InterfaceAlias, IPAddress, AddressFamily

        Add-Content -Path $outputPath -Value "==== Report at $timestamp ===="
        Add-Content -Path $outputPath -Value "`n--- Running Processes ---"
        $processes | Out-String | Add-Content -Path $outputPath

        Add-Content -Path $outputPath -Value "`n--- Network Information ---"
        $netInfo | Out-String | Add-Content -Path $outputPath
        Add-Content -Path $outputPath -Value "`n==================================`n"
        Write-Host "✅ Remote report created."
    }
    catch {
        Write-Host "❌ Failed: $($_.Exception.Message)"
    }
} -ArgumentList $remoteTxtPath
```

## 📦 Step 3: Retrieve File to Local System

```powershell
$fileContent = Invoke-Command -ComputerName $remoteComputer -Credential $creds -ScriptBlock {
    param($path)
    Get-Content -Path $path
} -ArgumentList $remoteTxtPath

Set-Content -Path $localTxtPath -Value $fileContent
Write-Host "✅ File pulled to: $localTxtPath"
```

## 🧾 Step 4: Preview Retrieved Report

```powershell
Get-Content -Path $localTxtPath | Out-Host
```

## 🛡️ Step 5: Check Microsoft Defender Status Remotely

```powershell
$remoteService = "WinDefend"

Invoke-Command -ComputerName $remoteComputer -Credential $creds -ScriptBlock {
    param($serviceName)
    $service = Get-Service -Name $serviceName -ErrorAction SilentlyContinue

    if ($null -eq $service) {
        "❌ Service '$serviceName' not found."
    } elseif ($service.Status -eq 'Running') {
        "✅ Microsoft Defender is RUNNING."
    } else {
        "⚠️ Microsoft Defender is NOT running. Status: $($service.Status)"
    }
} -ArgumentList $remoteService
```

## 🔁 Step 6: Enumerate All Running Services (Optional)

```powershell
$runningServices = Invoke-Command -ComputerName $remoteComputer -Credential $creds -ScriptBlock {
    Get-Service | Where-Object { $_.Status -eq 'Running' } | Select-Object Name, DisplayName
}
$runningServices
```

## 📤 Step 7: Export Running Services to CSV

```powershell
$exportPath = "C:\\Users\\cvte1\\Documents\\RemoteServices.csv"
$runningServices | Export-Csv -Path $exportPath -NoTypeInformation
Write-Host "✅ Export complete: $exportPath"
```


---

[⬆️ Back to Module Index](../README.md)
