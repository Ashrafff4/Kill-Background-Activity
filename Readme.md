# Close All Apps Utility

A lightweight Windows script that instantly closes active background applications and clears recent desktop windows while keeping core system processes intact.

---

## Important Notice Before Use

> **Save your work first!**  
> This script forcefully terminates active applications. Any unsaved progress in text editors (e.g., Notepad, Microsoft Word), code editors, or documents will be lost upon execution.

---

## Overview

The Close All Apps Utility is designed for quick desktop cleanup and memory optimization. Executing this script closes open application windows and File Explorer instances without requiring a system restart.

### Key Characteristics
- Fast Execution: Runs instantly using native Windows components.
- Lightweight: Consumes zero persistent background resources.
- Specific Termination: Closes active desktop applications while leaving Task Manager (`Taskmgr`) and Windows Shell (`explorer.exe`) running.

---

## Target Command

The utility executes the following PowerShell command:

```cmd
powershell -windowstyle hidden -command "(New-Object -ComObject Shell.Application).Windows() | ForEach-Object { $_.Quit() }; Get-Process \vert{} Where-Object { ($_.MainWindowTitle -or $_.ProcessName -eq 'Taskmgr') -and$_.ProcessName -ne 'explorer' } | Stop-Process -Force"