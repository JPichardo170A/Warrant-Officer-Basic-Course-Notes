# 💥 Day 2 – Pipeline, Functions, File IO & Modules

*Module 02 — PowerShell | Day 2*

---

## 🎯 Learning Objectives

- Understand PowerShell pipes and operators
- Create functions and use parameters
- Work with file I/O operations
- Use and manage PowerShell modules

---

# PowerShell Day 2 💥
## The Pipeline, Functions, File IO, and PowerShell Modules

## 🎯 Terminal Learning Objectives
- Understand PowerShell Pipes and Operators
- Create Functions and Use Parameters
- Perform File IO
- Work with PowerShell Modules
- Demonstrate Object Manipulation & Output Formatting

## 🔹 The Pipeline
Pipelines in PowerShell allow the output of one command to be used as the input to another. Unlike traditional command-line tools that pass strings, PowerShell passes full **objects** through the pipeline.

```powershell
Get-Command -Verb format
Get-Service | Format-Table Name, Status
Get-ChildItem | Format-Table Name
Get-Service | Format-List
```

## 🧮 Comparison Operators

```powershell
'192.168.1.1' -eq '192.168.1.1'
'PowerShell' -like '*shell'
'Text1' -ne 'Text2'
$pattern = 'MO(\d{3})'
'Here is the serial number: MO5364' -match $pattern
```

```powershell
$IPs = '10.50.25.255', '10.35.192.253', '192.168.1.5', '10.50.22.95'
$IPs -contains '10.50.22.95'
```

## 🔧 Functions in PowerShell

```powershell
function processes {
    Get-Process
}
processes
```

```powershell
function network {
    Get-NetTCPConnection |
    Where-Object {$_.State -eq 'Listen'} |
    Select-Object LocalAddress, LocalPort, RemoteAddress, RemotePort, State, OwningProcess
}
network
```

```powershell
# Function with Parameters
function UserInfo {
    param (
        [string]$Username,
        [switch]$IncludeDetails
    )
    if ($IncludeDetails) {
        Write-Host "Getting detailed info for $Username"
        Get-LocalUser | Where-Object { $_.Name -eq $Username } |
        Select-Object Name, Enabled, PasswordRequired, SID
    } else {
        Write-Host "Getting basic info for $Username"
        Get-LocalUser | Where-Object { $_.Name -eq $Username } |
        Select-Object Name, Enabled
    }
}
UserInfo -Username Administrator -IncludeDetails
```

## 📁 File I/O in PowerShell

```powershell
# Out-File
Get-LocalUser | Out-File -FilePath .\user.txt
# Get-Content
Get-Content -Path .\user.txt
```

```powershell
# Add-Content
$User = (Get-LocalUser).Name
Add-Content -Path .\testfile.txt -Value $User
Get-Content .\testfile.txt
```

```powershell
# Set-Content
Set-Content -Path .\testfile.txt -Value (Get-LocalGroup).Name
Get-Content -Path .\testfile.txt
```

### 📤 Export/Import CSV

```powershell
Get-Process -Name svchost | Export-Csv -Path .\svchost.csv -NoTypeInformation
Import-Csv -Path .\svchost.csv
```

### 📦 Convert Logs to JSON

```powershell
$events = Get-WinEvent -LogName Security -MaxEvents 10
$eventsJSON = $events | ConvertTo-Json -Depth 5
$eventsJSON | Out-File -FilePath .\events.json
Get-Content .\events.json
```

## 📦 PowerShell Modules

```powershell
Get-Module
Get-Command Install-Module, Install-PSResource
```

### 🌐 NetTCPIP Module Example

```powershell
Get-Command -Module NetTCPIP
Get-NetIPAddress | Select-Object -First 5 -Property IPAddress, InterfaceIndex
```

### 🌍 DnsClient Module Example

```powershell
Get-DnsClient | Select-Object InterfaceAlias, InterfaceIndex
Get-DnsClientServerAddress | Select-Object InterfaceAlias, ServerAddresses
```

### 🛠️ RSAT (Remote Server Admin Tools)

```powershell
Get-WindowsCapability -Name RSAT* -Online | Add-WindowsCapability -Online
```

### 🔐 AD Module Examples (In Remote Session)

```powershell
Enter-PSSession -ComputerName 10.50.22.95 -Credential $creds
Get-ADUser -Filter * | Select-Object Name, SID -First 5
Get-ADGroup -Filter * | Select-Object Name, SID -First 5
Get-ADComputer -Filter * | Select-Object Name -First 5 | Format-Table
Get-ADDomain | Select-Object Name, DNSRoot, Forest, DomainSID | Format-List
```

## ✅ Summary
- PowerShell Pipelines & Formatting
- Comparison Operators
- Functions & Parameters
- File IO: Out-File, Get-Content, Set-Content, CSV/JSON
- PowerShell Modules (NetTCPIP, DnsClient, RSAT)

🚀 Ready to proceed to **Day 2 Practical Exercises**!


---

[⬆️ Back to Module Index](../README.md)
