# 📘 PowerShell Module Notes – Expanded Edition

*Module 02 — PowerShell | Supplemental*

---

## 🎯 Learning Objectives

- Review core PowerShell concepts in an all-in-one reference
- Understand cmdlet syntax and case sensitivity
- Work with providers, drives, and navigation
- Apply operators and pipeline techniques

---

# 📘 PowerShell Module Notes – Expanded Interactive Edition
An all-in-one PowerShell learning notebook to explore the language, tools, tips, and common use cases interactively.

## 🤖 What is PowerShell?
**PowerShell** is a cross-platform command-line shell and scripting language.

It was first introduced by Microsoft in 2006 as *Windows PowerShell*, built on the .NET Framework. Since PowerShell 6, it became cross-platform using .NET Core (now .NET 7+).

### 🧰 Used for:
- Automating system administration tasks
- Managing remote systems
- Interfacing with REST APIs, JSON, XML, WMI, CIM
- Scripting deployment pipelines

## 🆚 Case Sensitivity and Correct Cmdlet Usage
PowerShell is **case-insensitive**, so `Get-Process` = `get-process` = `GET-PROCESS`

However, **cmdlet spelling matters**: `Get-processess` ❌ is invalid.

Try both and see what happens:

```powershell
# ❌ Misspelled cmdlet
Get-processess
```

```powershell
# ✅ Correct usage
Get-Process
```

## ⚙️ Cmdlet Anatomy: Verb-Noun Standard
PowerShell cmdlets follow the `Verb-Noun` naming convention. Examples:
- `Get-Process`
- `Set-ExecutionPolicy`
- `Start-Service`
- `Stop-Service`

Each cmdlet can accept parameters. Example:

```powershell
Get-Process -Name notepad
Start-Service -Name "Spooler"
```

## 🧭 Discover Commands with Get-Command & Get-Help

```powershell
# 🔍 Find all cmdlets starting with Get
Get-Command -Verb Get

# 📚 Get help on a cmdlet with examples
Get-Help Get-Process -Examples
```

## ✍️ Writing and Running a Simple Script (.ps1)
You can write multi-line scripts and save them with the `.ps1` extension. Here’s an example:

```powershell
$script = @'
$user = [System.Environment]::UserName
$date = Get-Date -Format "yyyy-MM-dd HH:mm"
Write-Output "Hello $user! Today is $date."
'@

$script | Set-Content -Path "$env:TEMP\hello.ps1"
& "$env:TEMP\hello.ps1"
```

## ⏱️ Productivity Tips in Console
Use keyboard shortcuts to speed up scripting:
- `Shift + Home` → Select to beginning of line
- `Ctrl + Home` → Top of console
- `Ctrl + End` → Bottom of script
- `Ctrl + C` → Interrupt command

## 🧪 Bonus: Aliases
PowerShell has aliases for common cmdlets. These are shorter, faster versions:
- `ls` = `Get-ChildItem`
- `cat` = `Get-Content`
- `gps` = `Get-Process`

List all aliases:

```powershell
Get-Alias | Sort-Object Name
```

## ⚙️ Optional: Profiles
You can customize your PowerShell experience by editing your `$PROFILE` script. This runs every time a session starts.

To view or edit it:

```powershell
notepad $PROFILE
```


---

[⬆️ Back to Module Index](../README.md)
