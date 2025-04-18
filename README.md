# 🕵️‍♂️ ProcessHider

**ProcessHider** is a Windows user-mode DLL that hooks the `NtQuerySystemInformation` API to hide a specific process (e.g., `notepad.exe`) from applications like Task Manager or PowerShell.

## ✨ Features

- Hides any specified process from process listings.
- Inject into Task Manager to make it "blind" to your target.
- Simple and lightweight implementation using Microsoft Detours.

## 🛠 How It Works

The DLL hooks the `NtQuerySystemInformation` function and intercepts `SystemProcessInformation` queries. It scans the returned process list and removes entries that match the specified name.

## ⚙️ Usage

1. **Build the DLL** (make sure Detours is compiled and linked).
2. **Specify the process name** to hide by editing:

 ```cpp
#define HIDE_PROCNAME L"notepad.exe" // You can change process name what do you want.
 ```

3. **Inject DLL to Target Process** (e.g., Task Manager):
Use a tool like Process Hacker or a custom injector.
Open Task Manager — the target process should now be hidden.


## ⚠️ Disclaimer

This project is for educational and research purposes only. Do not use it to conceal malicious activity. Use responsibly and within legal boundaries.
