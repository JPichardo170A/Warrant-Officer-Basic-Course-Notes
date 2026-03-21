# 💡 Day 3 – Aliases, Profiles, Formatting, WMI, CIM & JEA

*Module 02 — PowerShell | Day 3*

---

## 🎯 Learning Objectives

- Understand PowerShell aliases
- Understand PowerShell profiles
- Format output with `Format-Table` and `Format-List`
- Use script constructs (loops, conditionals)
- Query system info with WMI and CIM
- Understand Just Enough Administration (JEA)

---

# PowerShell Day 3 💡
## Aliases, Profiles, Output Formatting, Script Constructs, WMI, CIM, JEA, and Remote Execution

## 🎯 Terminal Learning Objectives
- Understand PowerShell Aliases
- Understand PowerShell Profiles
- Format and filter output
- Write PowerShell script constructs (if/switch/loop)
- Use WMI and CIM to get system info
- Use `Invoke-Command` for remote execution
- Understand Just Enough Administration (JEA)

## 🔀 Aliases in PowerShell
PowerShell includes aliases for many cmdlets and allows users to create their own. These are session-scoped unless added to a profile.

```powershell
# Resolve built-in aliases
$alias:dir
$alias:ls

# List all aliases for Get-ChildItem
Get-Alias -Definition Get-ChildItem
```

```powershell
# Create a custom alias
Set-Alias edit notepad.exe

# Remove it manually (or let it die with the session)
Remove-Item alias:edit
```

## 🧳 PowerShell Profiles
Profiles let you store startup scripts, aliases, or functions that load every time a PowerShell session starts.

**Types of profiles and their load order:**
- AllUsersAllHosts
- AllUsersCurrentHost
- CurrentUserAllHosts
- CurrentUserCurrentHost

If the same alias is defined in two profiles, the **later one overrides** the earlier due to load order.

```powershell
# View the path to your current profile
$Profile

# View all profile paths
$Profile | Select *
```

```powershell
# View contents of your profile if it exists
if (Test-Path $Profile) {
    Get-Content $Profile
} else {
    "Profile not found."
}
```

## 🎛️ Output Formatting in PowerShell

### 🔽 Sort-Object
Sorts data by specified property values.

```powershell
Get-ChildItem | Sort-Object
Get-ChildItem | Sort-Object -Property Length -Descending
Get-NetTCPConnection | Select-Object RemoteAddress, RemotePort, State |
Sort-Object -Property RemoteAddress -Descending | Select-Object -First 10
```

⚠️ **Efficiency Tip**: Filter Left, Sort Right!
`Where-Object` first, `Sort-Object` last for best performance.

### 🎯 Select-Object
Used to limit output columns or rows, like `head`, `tail`, or `awk` in Unix.

```powershell
Get-Process | Select-Object -Property Name, ID -First 5
Get-Process | Select-Object -Property Name, ID -Last 5
Get-Process | Select-Object -ExpandProperty Name -First 5
```

### 🔍 Where-Object
Used for filtering based on one or more conditions.
Supports both short syntax and script blocks.

```powershell
# Single condition
Get-Service | Where-Object Status -eq 'Running' | Select-Object -First 5
Get-Service | Where-Object { $_.Status -eq 'Running' } | Select-Object -First 5

# Multiple conditions
Get-Service | Where-Object { $_.Status -eq 'Running' -and $_.Name -like 'WIN*' }
```

### 🧱 Group-Object
Group output based on properties to analyze structure.

```powershell
# Group by file extension
Get-ChildItem -Path C:\Windows\System32 |
Group-Object -Property Extension |
Sort-Object -Property Count -Descending |
Select-Object -First 5
```

## 🧠 Script Constructs

### 🔍 If / ElseIf / Else

```powershell
$ipAddressString = "172.64.0.100"
$ipAddress = [System.Net.IPAddress]::Parse($ipAddressString)

if ($ipAddress.AddressFamily -eq 'InterNetwork' -and (
    ($ipAddress.IPAddressToString -ge '192.168.0.0' -and $ipAddress.IPAddressToString -le '192.168.255.255')))
{ Write-Output "$ipAddressString is private" }
elseif ($ipAddress.AddressFamily -eq 'InterNetwork')
{ Write-Output "$ipAddressString is public" }
else { Write-Output "Invalid IP" }
```

### 🔘 Switch Statement

```powershell
$ip = '172.64.0.100'
Switch -Wildcard ($ip) {
  '192.168.*' { "LAN" }
  '10.15.*'   { "Branch" }
  '172.64.*'  { "DMZ" }
  Default     { "Unknown network" }
}
```

### 🔁 While Loop

```powershell
$processToMonitor = "msedge"
while ($true) {
  if (Get-Process -Name $processToMonitor -ErrorAction SilentlyContinue) {
    Write-Host "⚠️ $processToMonitor is running"
  }
  Start-Sleep -Seconds 5
}
```

### 🔁 Do While Loop

```powershell
$proc = "msedge"
Do {
  if (Get-Process -Name $proc -ErrorAction SilentlyContinue) {
    Write-Host "🔍 $proc is active"
  } else {
    Write-Host "$proc is not running"
  }
  Start-Sleep -Seconds 5
} While ($true)
```

### ⛔ Do Until Loop

```powershell
$proc = "msedge"
Do {
  $running = Get-Process -Name $proc -ErrorAction SilentlyContinue
  if ($running) {
    Write-Host "Still running... monitoring"
  }
  Start-Sleep -Seconds 10
} Until (-not $running)
```

### 🔁 Foreach vs ForEach-Object

```powershell
# Collection version
$users = Get-LocalUser
foreach ($u in $users) {
  if ($u.Name -like '*Admin*') {
    "$($u.Name) is enabled: $($u.Enabled)"
  }
}
```

```powershell
# Pipeline version
Get-LocalUser | ForEach-Object {
  if ($_.Name -like '*Admin*') {
    "$($_.Name) is enabled: $($_.Enabled)"
  }
}
```

## 🖥️ WMI & CIM (System Information Queries)

```powershell
Get-CimClass -Namespace root\CIMv2 | Select-String 'network'
```

```powershell
Get-CimInstance Win32_NetworkAdapterConfiguration |
Select-Object DNSHostName, InterfaceIndex, IPAddress, IPSubnet | Format-List
```

```powershell
Get-CimInstance Win32_Process |
Where-Object Name -eq 'pwsh.exe' |
Select-Object Name, ProcessID, ParentProcessID
```

## 🔐 Just Enough Administration (JEA)

RBAC-like control for PowerShell remoting.
- Least privilege
- Local-only virtual accounts
- Does not expose user credentials

🔗 Learn more at [Microsoft JEA](https://learn.microsoft.com/en-us/powershell/scripting/learn/remoting/jea/overview)

## 📤 Invoke-Command: Remote Scripting

```powershell
Invoke-Command -ComputerName 10.50.22.95 -Credential $Creds -ScriptBlock {
  Get-Process | Where-Object {$_.Path -like 'C:\\Windows\\System32\\*'} |
  Select-Object Name, ID, Path
} | Select-Object -First 5
```

```powershell
Invoke-Command -ComputerName 10.50.22.95 -Credential $Creds -ScriptBlock {
  Get-Process | Where-Object {$_.Path -like 'C:\\Windows\\System32\\*'} |
  Select-Object Name, ID, Path -First 10
} | Out-File -FilePath C:\Users\Public\RemoteProcesses.txt
```

```powershell
Invoke-Command -ComputerName 10.50.22.95 -Credential $Creds -ScriptBlock {
  $Content = 'cmd.exe /c ping -n 1 10.50.35.169'
  Set-Content -Path "C:\Users\Administrator\Desktop\pingme.ps1" -Value $Content
  powershell.exe "C:\Users\Administrator\Desktop\pingme.ps1"
}
```

## ✅ Summary
- Aliases & Profiles
- Output Filtering & Grouping
- Control Structures
- WMI & CIM Access
- Just Enough Admin (JEA)
- Remote Scripting with `Invoke-Command`

🚀 Ready for Day 3 Practical Challenges!


---

[⬆️ Back to Module Index](../README.md)
