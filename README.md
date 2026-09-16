# How to Create a PowerShell Script Shortcut on the Windows Desktop

🇫🇷 [Version française](README_FRENCH.md)

## PowerShell 7 and Windows PowerShell 5.1

Windows includes **Windows PowerShell 5.1** by default.  
**PowerShell 7** is a newer version that must be installed separately.

Both versions can run `.ps1` scripts, but they use different executable names.

---

## 1. PowerShell 7 vs. Windows PowerShell 5.1

### PowerShell 7

**Modern version**

Executable:

```text
pwsh.exe
```

PowerShell 7 must be installed separately. It is the newer, cross-platform version of PowerShell.

### Windows PowerShell 5.1

**Built into Windows**

Executable:

```text
powershell.exe
```

This version is normally available by default on Windows and does not require a separate installation.

---

## 2. Check Which PowerShell Version You Are Using

Open PowerShell or Windows Terminal and run:

```powershell
$PSVersionTable.PSVersion
```

If the **Major** version is `7`, you are using **PowerShell 7**.

If the **Major** version is `5`, you are using **Windows PowerShell 5.1**.

---

## 3. Create the Desktop Shortcut

The procedure is the same for both PowerShell versions.

### Step 1

Right-click on the Windows desktop.

Select:

**New → Shortcut**

### Step 2

In the **Type the location of the item** field, enter the command corresponding to the PowerShell version you want to use.

### Step 3

Click **Next**.

### Step 4

Enter a name for the shortcut.

For example:

```text
Run My PowerShell Script
```

Click **Finish**.

You can now double-click the shortcut to execute your script.

---

## 4. PowerShell 7 Shortcut

If PowerShell 7 is installed, use:

```text
pwsh.exe -NoProfile -ExecutionPolicy Bypass -File "C:\Scripts\MyScript.ps1"
```

### Command explanation

| Command | Description |
|---|---|
| `pwsh.exe` | Starts PowerShell 7. |
| `-NoProfile` | Prevents PowerShell from loading the user's PowerShell profile. |
| `-ExecutionPolicy Bypass` | Bypasses execution policy restrictions for this process. |
| `-File` | Tells PowerShell to execute a script file. |
| `"C:\Scripts\MyScript.ps1"` | The path to the PowerShell script. |

---

## 5. Windows PowerShell 5.1 Shortcut

If you are using the version included with Windows, use:

```text
powershell.exe -NoProfile -ExecutionPolicy Bypass -File "C:\Scripts\MyScript.ps1"
```

### Command explanation

| Command | Description |
|---|---|
| `powershell.exe` | Starts Windows PowerShell 5.1. |
| `-NoProfile` | Prevents PowerShell from loading the user's PowerShell profile. |
| `-ExecutionPolicy Bypass` | Bypasses execution policy restrictions for this process. |
| `-File` | Tells PowerShell to execute a script file. |
| `"C:\Scripts\MyScript.ps1"` | The path to the PowerShell script. |

### The main difference

The two commands are almost identical.

The main difference is the executable:

```text
pwsh.exe
```

for **PowerShell 7**

and:

```text
powershell.exe
```

for **Windows PowerShell 5.1**.

The parameters `-NoProfile`, `-ExecutionPolicy Bypass`, and `-File` can be used with both versions.

---

## 6. Keep the PowerShell Window Open

By default, the PowerShell window may close when the script finishes.

If you want to keep the window open, add:

```text
-NoExit
```

### PowerShell 7

```text
pwsh.exe -NoProfile -ExecutionPolicy Bypass -NoExit -File "C:\Scripts\MyScript.ps1"
```

### Windows PowerShell 5.1

```text
powershell.exe -NoProfile -ExecutionPolicy Bypass -NoExit -File "C:\Scripts\MyScript.ps1"
```

`-NoExit` tells PowerShell to remain open after the script has finished.

This can be useful when you want to see messages displayed by the script or inspect errors.

---

## 7. Set the Working Directory

In the shortcut properties, you can also specify a working directory in the **Start in** field.

For example:

```text
C:\Scripts
```

This defines the working directory used by the script.

This can be useful when your script uses relative paths, for example:

```powershell
.\data.txt
```

---

## 8. Complete Example

Suppose your script is located at:

```text
C:\Users\John\Desktop\Scripts\Backup.ps1
```

### PowerShell 7

```text
pwsh.exe -NoProfile -ExecutionPolicy Bypass -File "C:\Users\John\Desktop\Scripts\Backup.ps1"
```

### Windows PowerShell 5.1

```text
powershell.exe -NoProfile -ExecutionPolicy Bypass -File "C:\Users\John\Desktop\Scripts\Backup.ps1"
```

You can place this shortcut on your desktop and simply **double-click it to run the script**.

---

## 9. About `-ExecutionPolicy Bypass`

The option:

```text
-ExecutionPolicy Bypass
```

tells PowerShell not to enforce execution policy restrictions for the PowerShell process launched by this command.

It **does not permanently change** the Windows or PowerShell execution policy.

However, you should only use it with scripts that you trust.

---

# Summary

### PowerShell 7

```text
pwsh.exe -NoProfile -ExecutionPolicy Bypass -File "PATH_TO_YOUR_SCRIPT.ps1"
```

### Windows PowerShell 5.1

```text
powershell.exe -NoProfile -ExecutionPolicy Bypass -File "PATH_TO_YOUR_SCRIPT.ps1"
```

The main difference is:

**PowerShell 7 → `pwsh.exe`**

**Windows PowerShell 5.1 → `powershell.exe`**
