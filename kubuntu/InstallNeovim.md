# Install Neovim

This guide explains how to **manually install a specific version of Neovim** on Kubuntu.

---

## 1. Install Required Tools

- Install Node.js

---

## 2. Download Neovim

Get the latest pre-built Neovim package:

```bash
curl -LO https://github.com/neovim/neovim/releases/latest/download/nvim-linux-x86_64.tar.gz
```

---

## 3. Remove Old Version

If you have a previous installation under `/opt/nvim`, remove it:

```bash
sudo rm -rf /opt/nvim
```

---

## 4. Install New Version

Extract the downloaded archive to `/opt`:

```bash
sudo tar -C /opt -xzf nvim-linux-x86_64.tar.gz
```

---

## 5. Configure Environment

### 5.1 Add Neovim to PATH

Edit your shell configuration file:

```bash
vi ~/.bashrc
```

Add the following line at the end:

```bash
export PATH="$PATH:/opt/nvim-linux-x86_64/bin"
```

Reload the shell configuration:

```bash
source ~/.bashrc
```

### 5.2 Clipboard Support

Depending on your display server, install the appropriate package:

- **Xorg session**:

  ```bash
  sudo apt install -y xsel xclip
  ```

- **Wayland session**:

  ```bash
  sudo apt install -y wl-clipboard
  ```

---

## Done! You can now run Neovim using:

```bash
nvim
```
