# Setup VSCode

Basic configuration steps for optimizing your Visual Studio Code environment.

---

## Open Settings

Navigate to:

```
File -> Preferences -> Settings
```

---

## 1. Start with a New Untitled File

Set the following in the settings:

```
workbench.startupEditor
```

Change the value to:

```
newUntitledFile
```

---

## 2. Set Font Size

Adjust the editor font size:

```
editor.fontSize
```

Example:

```
20
```

---

## 3. Set Font Family to SauceCodePro NF

Configure your font family:

```
editor.fontFamily
```

Recommended value:

```
'SauceCodePro NFM', 'SauceCodePro NF', 'SauceCodePro Nerd Font'
```

---

## 4. Disable Restore of Last Opened Files

To prevent reopening previous files on startup:

```
window.restoreWindows
```

Set to:

```
none
```

---

## 5. Add Trusted Workspace Folder

1. Open the Command Palette: `Ctrl + Shift + P`
2. Type and select:

```
Workspace: Manage Workspace Trust
```

3. Add paths you want to mark as trusted.

---

## 6. Set Default Path for "Open Folder"

Search for `dialog default` in the settings panel  
and configure the default path for folder selection.

---

## 7. Always Open Files in a New Window

```
window.openFilesInNewWindow
```

Set the value to:

```
on
```

---

## 8. Suggested C++ development extensions

- Clang-Format
- clangd
- CMake IntelliSence
- CMake Tools
- CodeLLDB

---

## 9. Suggested Python development extensions

- Pylance
- Python
- Python Debugger
- Python Environments

---