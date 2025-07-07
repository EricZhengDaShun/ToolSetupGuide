# Install Ninja

This guide explains how to manually install the Ninja build system on Kubuntu.

**Reference:**
https://github.com/ninja-build/ninja

---

## Installation Steps

- **Recommended Version:** v1.13.0

### 1. Download the Installer

   - Visit the Ninja releases page.(https://github.com/ninja-build/ninja/releases) and download `ninja-linux.zip`, or use the following command:

      ```bash
      wget https://github.com/ninja-build/ninja/releases/download/v1.13.0/ninja-linux.zip
      ```

---

### 2. Extract the Archive

```bash
unzip ninja-linux.zip
```

---

### 3. Move the Binary to `/usr/local/bin`

```bash
sudo mv ninja /usr/local/bin/
```

---

### 4. Make the Binary Executable

```bash
sudo chmod +x /usr/local/bin/ninja
```

---

### 5. (Optional) Verify the Installation

```bash
ninja --version
```
