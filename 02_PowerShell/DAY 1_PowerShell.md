# 🧠 Day 1 – PowerShell Fundamentals

*Module 02 — PowerShell | Day 1*

---

## 🎯 Learning Objectives

- Understand PowerShell editions and platforms
- Use `Get-Command`, `Get-Help`, and `Get-Member` effectively
- Learn how PowerShell handles objects
- Navigate the shell, drives, and file system providers
- Work with variables, logic, and formatting
- Use the PowerShell pipeline to pass objects
- Understand and apply comparison and logical operators

---

# 🧠 Day 1 – PowerShell Fundamentals
### Your journey into shell scripting and system automation begins here!

## 🎯 Terminal Learning Objectives
- Understand PowerShell editions and platforms
- Use Get-Command, Get-Help, and Get-Member effectively
- Learn how PowerShell handles objects
- Navigate the shell, drives, and file system providers
- Work with variables, logic, and formatting
- Use the PowerShell pipeline to pass objects
- Understand and apply comparison and logical operators

## 🧱 What is PowerShell?
PowerShell is a cross-platform shell and scripting language that is object-based, not just text-based like traditional shells.

It’s built on .NET and lets you manage computers from the command line with consistent syntax and structured output.

> **“Everything is an object”** – This is the PowerShell mindset.

### 🔍 Editions Overview:
- **Windows PowerShell** (5.1): Legacy, only on Windows, built on full .NET Framework.
- **PowerShell Core** (6.x+): Cross-platform (Windows, Linux, macOS), built on .NET Core and .NET 5/6+.

✅ We will use PowerShell **7+** (pwsh) for all labs, which is the latest and most versatile edition.

### 🧪 Check your version and edition:

```powershell
$PSVersionTable
```

> If `$PSVersionTable.PSEdition` is `Core`, you’re on modern PowerShell.
> If it says `Desktop`, you’re running Windows PowerShell 5.1.

### 🧠 Tip: You can run `powershell` or `pwsh` side-by-side.
Use `pwsh` for modern scripting, cross-platform development, and security-focused workflows.

## 🧪 Cmdlets, Aliases, and Discoverability Tools
PowerShell is designed to be self-discoverable — no man pages or Googling required for the basics!

**Cmdlet syntax:**
`Verb-Noun` — for example: `Get-Process`, `Set-Item`, `Remove-Item`

**🔄 Aliases** are shortcuts to cmdlets (like `ls`, `dir`, `cat`, etc.).
They're great for quick typing but should be avoided in scripts.

```powershell
# Examples of aliases
Get-Alias dir
Get-Alias ls
Get-Alias cat
Get-Alias gc  # shortcut for Get-Content
```

### 🔍 Get-Command: Find anything
This cmdlet will list or search for ANY command: alias, function, script, application, or cmdlet.

```powershell
Get-Command -Name Get-Process
Get-Command -Noun Item
Get-Command -Verb Get
Get-Command -CommandType Cmdlet | Sort-Object Name | Out-GridView
```

### 📚 Get-Help: Learn any cmdlet
`Get-Help` is your built-in manual for all things PowerShell.

Update it once, then use it forever:

```powershell
Update-Help -Force
```

```powershell
# Get basic help
Get-Help Get-Process

# Show examples
Get-Help Get-Process -Examples

# Full help
Get-Help Get-Process -Detailed
```

### 🔍 Get-Member: Inspect output objects
PowerShell sends **objects**, not plain text. Use `Get-Member` to understand them.

```powershell
Get-Process | Get-Member
```

> 🧠 Use `Select-Object`, `Format-Table`, and `Format-List` once you know what properties are available!

## 📁 Providers and Drives in PowerShell
PowerShell treats different data stores like drives — not just your file system.

This means you can `cd` into the registry, aliases, certificates, environment variables, and more!

### 🔎 Get-PSProvider
This command lists all available **providers**, which map to logical data structures.

```powershell
Get-PSProvider
```

**Common Providers:**
- `FileSystem` → C:\, D:\, etc.
- `Registry` → HKLM:, HKCU:
- `Environment` → Env:
- `Certificate` → Cert:
- `Alias` → Alias:

### 💽 Get-PSDrive
`Get-PSDrive` shows all active logical drives across providers.

```powershell
Get-PSDrive
```

### 🧭 Navigation Examples

```powershell
# Change location into environment variables
Set-Location Env:

# List all variables
Get-ChildItem

# Back to file system
Set-Location C:\
```

### 🔧 Custom PSDrives
You can create a **named shortcut** to any folder using `New-PSDrive`.

```powershell
New-PSDrive -Name Scripts -PSProvider FileSystem -Root "C:\Users\Public\Documents\Scripts" -Persist
Set-Location Scripts:
```

> 🧠 Pro Tip: Use `Push-Location` and `Pop-Location` to temporarily jump between paths like a stack.

## 🧮 PowerShell Variables and Operators
Everything in PowerShell can be stored in a variable — including objects, arrays, script blocks, and more.

### 🔢 Declaring Variables
Use the dollar sign (`$`) to assign values.

```powershell
$name = "Admin"
$port = 443
$iplist = @('10.0.0.1', '10.0.0.2')
$iplist
```

### 🧠 Data Types (optional but powerful):

```powershell
[string]$user = "jdoe"
[int]$age = 33
[datetime]$today = Get-Date
$today.DayOfWeek
```

## 🧮 Comparison Operators
| Operator | Purpose         |
|----------|------------------|
| `-eq`    | Equals           |
| `-ne`    | Not equals       |
| `-lt`    | Less than        |
| `-gt`    | Greater than     |
| `-like`  | Wildcard match   |
| `-match` | Regex match      |

```powershell
'PowerShell' -eq 'powershell'         # False (case-sensitive by default)
'PowerShell' -ieq 'powershell'        # True (case-insensitive variant)
'BlueTeam42' -like '*42'              # True
'RedTeam42' -match '\\d+$'           # True if ends with number
```

## 🔗 Logical Operators
| Operator | Meaning     |
|----------|-------------|
| `-and`   | Both true    |
| `-or`    | Either true  |
| `!`      | Not / invert |

```powershell
$a = 5
$b = 10
($a -lt 10 -and $b -gt 5)   # True
($a -eq 5 -or $b -eq 3)     # True
!( $b -eq 3 )               # True
```

> ✅ PowerShell uses **scriptblock syntax**: use `{}` to wrap code in loops or logic blocks.

## ⛓️ The PowerShell Pipeline
The pipeline (`|`) allows you to send the **output of one command as input to the next**.

Unlike Bash, PowerShell pipes **objects**, not just text.

```powershell
# Example: Pipe Get-Process into Where-Object
Get-Process | Where-Object { $_.CPU -gt 10 } | Select-Object Name, CPU
```

## 🎛️ Output Formatting
PowerShell provides several format cmdlets to control **how** data is displayed, but formatting happens **after** logic and filtering.

**🔹 Format-Table**: Great for horizontal data
**🔹 Format-List**: Use when objects have many properties

```powershell
Get-Service | Format-Table Name, Status, DisplayName -AutoSize
```

```powershell
Get-Process powershell | Format-List *
```

> 🧠 Only use **Format-Table/List** at the END of the pipeline. They convert objects to display strings!

## ✅ Summary: What You Learned Today
- PowerShell Editions & `$PSVersionTable`
- Cmdlets, Aliases, and Self-Discovery (`Get-Help`, `Get-Command`, `Get-Member`)
- Providers like `Env:`, `HKLM:`, `Cert:`
- Working with variables and data types
- Logical and comparison operators
- The PowerShell pipeline and formatting output

🧪 **You’re ready for Day 1 Lab & Practical Exercises**!

Keep practicing with:
- `Get-Help *`
- `Get-Command -Verb Get`
- `Get-Process | Get-Member`


---

[⬆️ Back to Module Index](../README.md)
