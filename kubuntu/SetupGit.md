# Setup Git

---

## Configure Git Author Info

- **Set User Name**  
  Replace `"your.name"` with your actual name:

  ```bash
  git config --global user.name "your.name"
  ```

- **Set User Email**  
  Replace `"your.email"` with your actual email:

  ```bash
  git config --global user.email "your.email"
  ```

---

## Configure Git for VSCode

### Use VSCode as Git Difftool

1. **Set VSCode as the default difftool:**

   ```bash
   git config --global diff.tool vscode
   ```

2. **Configure difftool launch command:**

   ```bash
   git config --global difftool.vscode.cmd "code --wait -n --diff \$LOCAL \$REMOTE"
   ```

### Use VSCode as Git Commit Editor

Set VSCode as your default editor for writing commit messages:

```bash
git config --global core.editor "code --wait -n"
```
