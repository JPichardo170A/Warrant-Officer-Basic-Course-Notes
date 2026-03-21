# 🛡️ PowerShell Remoting Investigation – Deluxe Edition

*Module 02 — PowerShell | Supplemental*

---

## 🎯 Learning Objectives

- Investigate malicious PowerShell activity remotely
- Retrieve ScriptBlock logs (Event ID 4104)
- Analyze suspicious processes and connections

---

# 🛡️ PowerShell Remoting Investigation – Deluxe Edition
Investigate malicious PowerShell activity remotely using script block logs, base64 decoding, and IOC pattern matching.

## 🔍 Step 1: Retrieve ScriptBlock Logs (Event ID 4104)

```powershell
Invoke-Command -ComputerName 10.50.132.145 -Credential $Creds -ScriptBlock {
    Get-WinEvent -LogName "Microsoft-Windows-Powershell/Operational" |
    Where-Object { $_.Id -eq 4104 } |
    Select-Object TimeCreated, Message -First 20
}
```

## 🧬 Step 2: Filter Logs for EncodedCommand Usage

```powershell
$encodedLogs = Invoke-Command -ComputerName 10.50.132.145 -Credential $Creds -ScriptBlock {
    Get-WinEvent -LogName "Microsoft-Windows-Powershell/Operational" |
    Where-Object { $_.Id -eq 4104 -and $_.Message -match "EncodedCommand" } |
    Select-Object TimeCreated, Message
}
$encodedLogs
```

## 🔓 Step 3: Extract Base64 Strings from Message Bodies

```powershell
$base64Strings = @()
foreach ($entry in $encodedLogs) {
    if ($entry.Message -match "EncodedCommand\s+[\w\d+/=]+") {
        $match = [regex]::Match($entry.Message, "(?<=EncodedCommand\s+)[\w\d+/=]+")
        if ($match.Success) {
            $base64Strings += $match.Value
        }
    }
}
$base64Strings
```

## 🧬 Step 4: Decode Extracted Base64 Strings

```powershell
$decodedStrings = @()
foreach ($b64 in $base64Strings) {
    try {
        $bytes = [Convert]::FromBase64String($b64)
        $decoded = [System.Text.Encoding]::UTF8.GetString($bytes)
        $decodedStrings += $decoded
    }
    catch {
        $decodedStrings += "⚠️ Failed to decode: $b64"
    }
}
$decodedStrings
```

## ⚠️ Step 5: Flag Suspicious Activity in Decoded Payloads

```powershell
$suspiciousKeywords = "Invoke-WebRequest", "DownloadString", "IEX", "Net.WebClient", "FromBase64String"

foreach ($script in $decodedStrings) {
    foreach ($word in $suspiciousKeywords) {
        if ($script -match $word) {
            Write-Host "⚠️ Match found: $word in script:`n$script`n"
        }
    }
}
```

## 💾 Step 6: Export Matching Logs to CSV

```powershell
$encodedLogs | Export-Csv -Path "C:\\Logs\\EncodedCommands.csv" -NoTypeInformation
Write-Host "✅ Log export complete: C:\\Logs\\EncodedCommands.csv"
```


---

[⬆️ Back to Module Index](../README.md)
