+++
date = '2025-11-05T21:57:40-08:00'
draft = false
title = 'Powershell Quick Start'
+++

# Getting Started with PowerShell: A Complete Beginner’s Guide

PowerShell is a powerful automation and scripting language designed for system administrators, IT professionals, and developers who want to manage, configure, and automate systems efficiently. Whether you’re on Windows, macOS, or Linux, PowerShell provides a unified environment for handling repetitive tasks and managing infrastructure at scale.

---

## ⚙️ Understanding PowerShell Versions

Before diving into scripting, it’s essential to understand the difference between **Windows PowerShell** and **PowerShell (Core)**.

### **1. Windows PowerShell**
- **Built-in:** Comes pre-installed on Windows systems (Windows 7 and later).  
- **Framework:** Built on the **.NET Framework** (Windows-only).  
- **Compatibility:** Ideal for managing Windows environments such as Active Directory and Windows Server.  
- **Version:** The final version is **5.1**, and it’s no longer actively developed.  
- **Platform:** Windows only.  

### **2. PowerShell (Core)**
- **Open-source:** Actively developed by Microsoft on GitHub.  
- **Framework:** Built on **.NET (formerly .NET Core)**, making it cross-platform.  
- **Compatibility:** Runs on Windows, macOS, and Linux.  
- **Version:** The current version is **PowerShell 7+**.  
- **Performance:** Faster, more lightweight, and modern.  

| Feature | Windows PowerShell | PowerShell (Core / 7+) |
|----------|--------------------|-------------------------|
| Framework | .NET Framework | .NET (Core / .NET 5+) |
| Platform | Windows-only | Cross-platform |
| Open Source | ❌ No | ✅ Yes |
| Development | ❌ Discontinued | ✅ Active |

### ✅ Recommendation
Start with **PowerShell 7+**, the actively developed and cross-platform version.

You can download it directly from [PowerShell GitHub Releases](https://github.com/PowerShell/PowerShell).

---

## 🧩 Installing PowerShell 7+ with WinGet

Windows’ package manager **WinGet** makes installing PowerShell easy.

### **Step 1: Search for PowerShell**
```powershell
winget search PowerShell
```

### **Step 2: Install PowerShell 7**
```powershell
winget install --id Microsoft.PowerShell --source winget
```

### **Step 3: Verify Installation**
```powershell
pwsh --version
```
The command `pwsh` starts PowerShell 7+. You should see an output like `7.4.x`.

### **Step 4: Start PowerShell 7**
You can launch PowerShell 7 by:
- Typing `pwsh` in Command Prompt or Run (Win + R).
- Searching for **PowerShell 7 (x64)** in the Start Menu.

### **Step 5: Confirm You’re Running PowerShell 7**
Inside the shell, check:
```powershell
$PSVersionTable
```
Look for:
- `PSEdition` → `Core`
- `PSVersion` → `7.x.x`

---

## 🧭 PowerShell Basics for Beginners

PowerShell is both a **command-line shell** and a **scripting language**. Here are the most useful basics to get you started.

---

### **1. Navigation Commands**
| Action | Command | Shortcut |
|--------|----------|-----------|
| List files | `Get-ChildItem` | `ls`, `dir` |
| Change directory | `Set-Location <path>` | `cd` |
| Show current directory | `Get-Location` | `pwd` |

---

### **2. File and Folder Operations**
```powershell
New-Item -Path "example.txt" -ItemType File
New-Item -Path "NewFolder" -ItemType Directory
Copy-Item -Path "source.txt" -Destination "backup\source.txt"
Move-Item -Path "example.txt" -Destination "archive\"
Remove-Item -Path "oldfile.txt"
```

---

### **3. Viewing and Filtering Data**
```powershell
Get-Content example.txt
Get-ChildItem | Where-Object { $_.Extension -eq ".txt" }
Get-ChildItem | Sort-Object Length
```

---

### **4. Working with Variables**
```powershell
$greeting = "Hello, PowerShell!"
Write-Output $greeting
Get-Variable
```

---

### **5. Working with Commands**
PowerShell commands are called **cmdlets** (verb-noun format).

```powershell
Get-Help Get-ChildItem
Update-Help
Get-Command -Verb Get
Get-Command -Noun Item
```

---

### **6. Processes and Services**
```powershell
Get-Process
Stop-Process -Name notepad
Get-Service
Start-Service -Name "wuauserv"
Stop-Service -Name "wuauserv"
```

---

### **7. Basic Scripting**
Save scripts with a `.ps1` extension:
```powershell
# hello.ps1
$name = Read-Host "Enter your name"
Write-Output "Hello, $name!"
```

Run it:
```powershell
.\hello.ps1
```

---

### **8. Permissions and Execution Policy**
Check or change script permissions:
```powershell
Get-ExecutionPolicy
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
```

---

### **9. Exploring Objects**
PowerShell outputs **objects**, not plain text.
```powershell
Get-Process | Select-Object -First 1 | Format-List *
Get-Process | Select-Object Name, Id, CPU
```

---

### **10. Practice Ideas**
- Automate file backups.
- Clean up folders.
- Monitor system performance.
- Query system info using `Get-ComputerInfo`.

---

## 🚀 PowerShell Learning Roadmap

A structured journey from beginner to advanced user.

---

### **Phase 1: Mastering the Basics**
**Goals:**
- Understand cmdlets and the pipeline.
- Get comfortable with PowerShell objects.

**Actions:**
```powershell
Get-Process | Where-Object { $_.CPU -gt 10 } | Sort-Object CPU -Descending
Get-Service | Get-Member
Get-Process | Format-Table -Property Name, CPU
```

---

### **Phase 2: Scripting and Automation**
**Goals:**
- Write reusable scripts.
- Learn control structures and error handling.

**Examples:**
```powershell
$names = @("Alice", "Bob", "Charlie")
foreach ($name in $names) { Write-Output "Hello, $name!" }

try {
    Get-Item "nonexistentfile.txt"
} catch {
    Write-Output "Error: $($_.Exception.Message)"
}
```

---

### **Phase 3: Managing Systems**
**Goals:**
- Automate system administration tasks.

**Examples:**
```powershell
Get-ComputerInfo
Get-ADUser -Filter *       # Active Directory
Get-Service | Stop-Service # Stop all services (be careful!)
```

---

### **Phase 4: Advanced PowerShell**
**Goals:**
- Create reusable functions and modules.
- Work remotely and integrate APIs.

**Examples:**
```powershell
function Get-Greeting {
    param ($Name)
    "Hello, $Name!"
}
Get-Greeting -Name "Alice"

Invoke-RestMethod -Uri "https://api.example.com/data"
```

---

### **Phase 5: Real-World Projects**
**Ideas:**
- **Automate Backups:** Copy files incrementally to a backup folder.  
- **System Health Monitor:** Log CPU and memory usage.  
- **Database Maintenance:** Automate SQL Server backups.  
- **Configuration Management:** Use PowerShell Desired State Configuration (DSC).

---

## 📚 Recommended Resources

### **Official Documentation**
- [Microsoft PowerShell Docs](https://learn.microsoft.com/powershell/)

### **Books**
- *Learn PowerShell in a Month of Lunches* by Don Jones & Jeffrey Hicks.

### **Online Courses**
- Pluralsight  
- LinkedIn Learning  
- YouTube Tutorials  

---

## 🏁 Final Thoughts

PowerShell is not just another command shell—it’s a **complete automation framework**.  
By learning its syntax, understanding objects, and building scripts, you can save hours of manual work and streamline system administration.

Start small. Automate something you do often—like backups or cleanup tasks—and expand from there.  
Once you grasp the fundamentals, you’ll find that PowerShell can handle nearly any task in your IT workflow.
