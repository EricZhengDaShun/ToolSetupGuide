# Install Neovim

This guide explains how to **manually install a specific version of Neovim** on Kubuntu.

---

## 1. Install Required Tools

Update package index and install common dependencies:

```bash
sudo apt update
sudo apt install -y curl git ripgrep lldb ninja-build
```

---

## 2. Install Node.js

Neovim plugins often require Node.js. Here’s how to install it.

### 2.1 Install Prerequisites

```bash
sudo apt update
sudo apt install -y curl
```

### 2.2 Download Setup Script

```bash
curl -fsSL https://deb.nodesource.com/setup_22.x | sudo bash -
```

### 2.3 Install Node.js

```bash
sudo apt install -y nodejs
```

### 2.4 Verify Installation (Optional)

```bash
node -v
```

---

## 3. Download Neovim

Get the latest pre-built Neovim package:

```bash
curl -LO https://github.com/neovim/neovim/releases/latest/download/nvim-linux-x86_64.tar.gz
```

---

## 4. Remove Old Version

If you have a previous installation under `/opt/nvim`, remove it:

```bash
sudo rm -rf /opt/nvim
```

---

## 5. Install New Version

Extract the downloaded archive to `/opt`:

```bash
sudo tar -C /opt -xzf nvim-linux-x86_64.tar.gz
```

---

## 6. Configure Environment

### 6.1 Add Neovim to PATH

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

### 6.2 Clipboard Support

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
