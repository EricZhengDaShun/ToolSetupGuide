# Install Node.js

Neovim plugins often require Node.js. Here’s how to install it.

### 1 Install Prerequisites

```bash
sudo apt update
sudo apt install -y curl
```

### 2 Download Setup Script

```bash
curl -fsSL https://deb.nodesource.com/setup_22.x | sudo bash -
```

### 3 Install Node.js

```bash
sudo apt install -y nodejs
```

### 4 Verify Installation (Optional)

```bash
node -v
```