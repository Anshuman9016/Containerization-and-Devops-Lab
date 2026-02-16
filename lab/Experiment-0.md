# Experiment 0 – Installation and Configuration of Windows Subsystem for Linux (WSL)

---

## Aim

To install and configure Windows Subsystem for Linux (WSL) on a Windows machine and set up an Ubuntu Linux distribution for running Linux commands and DevOps tools on Windows.

---

## Theory

Windows Subsystem for Linux (WSL) is a compatibility layer developed by Microsoft that allows users to run a Linux environment directly on Windows without the need for a virtual machine or dual boot system.

WSL enables developers to:

- Run Linux command-line tools directly on Windows  
- Use Linux-based development tools like Git, Docker, Podman, and Vagrant  
- Integrate Linux workflows with Windows applications  

### Versions of WSL

- **WSL 1**: Uses a translation layer between Linux and Windows kernel  
- **WSL 2**: Uses a real Linux kernel with better performance and full system call compatibility  

✅ **WSL 2 is recommended for containerization and DevOps workflows.**

---

## System Requirements

- Windows 10 (Version 2004 or later) or Windows 11  
- Administrator access  
- Virtualization enabled in BIOS  
- Internet connection  

---

# Procedure / Steps to Perform the Experiment

---

## Step 1: Install WSL and Ubuntu Distribution

Open **PowerShell as Administrator** and run:

```powershell
wsl --install -d Ubuntu
```

Example Output:

```powershell
PS C:\WINDOWS\system32> wsl --install -d Ubuntu  
Downloading: Ubuntu  
Installing: Ubuntu  
Distribution successfully installed. It can be launched via 'wsl.exe -d Ubuntu'  
Launching Ubuntu...  
Provisioning the new WSL instance Ubuntu  
This might take a while...  
Create a default Unix user account: mayank  
New password:  
Retype new password:  
passwd: password updated successfully  
```

This command:

- Enables required Windows features  
- Installs WSL  
- Installs Ubuntu as the default Linux distribution  

🔄 Restart the system after installation completes.

---

## Step 2: Verify WSL Installation

After restart, open PowerShell and execute:

```powershell
wsl -l -v
```

Example Output:

```powershell
PS C:\WINDOWS\system32> wsl -l -v  
NAME              STATE           VERSION  
* Ubuntu          Running         2  
  docker-desktop  Running         2  
```

This displays:

- Installed Linux distributions  
- WSL version (WSL 1 or WSL 2)  
- Running status  

---

## Step 3: Check and Change WSL Version

To convert Ubuntu to WSL 2:

```powershell
wsl --set-version Ubuntu 2
```

To convert Ubuntu to WSL 1:

```powershell
wsl --set-version Ubuntu 1
```

To set WSL 2 as default:

```powershell
wsl --set-default-version 2
```

---

## Step 4: Check Installed Linux Distributions

To list all available and installed distributions:

```powershell
wsl --list --all
```

To install another distribution (Example: Debian):

```powershell
wsl --install -d Debian
```

---

## Step 5: Set Default Linux Distribution

To set Ubuntu as default:

```powershell
wsl --set-default Ubuntu
```

To launch Ubuntu:

```powershell
wsl
```

---

## Step 6: Fix WSL 2 Kernel Update Issue

If error appears:

> “WSL 2 requires an update to its kernel”

Run:

```powershell
wsl --set-version Ubuntu 2
```

If still unresolved, install the latest WSL kernel update from Microsoft and restart.

---

## Step 7: Common Errors and Solutions

### Error: ‘wsl’ is not recognized

Run in PowerShell (Admin):

```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

Enable Virtual Machine Platform:

```powershell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

Restart the system.

---

## Step 8: Virtualization Disabled Error (0x80370102)

If virtualization is disabled:

1. Restart PC  
2. Enter BIOS/UEFI (F2 / F10 / DEL / ESC)  
3. Enable Intel VT-x / AMD-V  
4. Save & Restart  

---

## Step 9: Useful WSL Commands

| Command | Description |
|----------|------------|
| `wsl` | Start default Linux |
| `wsl -d Ubuntu` | Start Ubuntu |
| `wsl --terminate Ubuntu` | Stop Ubuntu |
| `wsl --shutdown` | Stop all WSL instances |
| `wsl --unregister Ubuntu` | Remove Ubuntu completely |

---

## Result

Windows Subsystem for Linux (WSL) was successfully installed and configured. Ubuntu Linux distribution was set up and verified with WSL 2, enabling Linux command-line and DevOps tool usage on Windows.

---

## Conclusion

WSL provides a powerful Linux development environment on Windows. It allows seamless execution of Linux tools and is highly suitable for cloud computing, DevOps, and container-based workflows.
