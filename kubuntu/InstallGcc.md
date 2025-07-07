# Install GCC and G++

This guide explains how to install a specific version of GCC and G++ on Ubuntu using the official toolchain PPA.

---

## Steps

### 1. Update the package list

```bash
sudo apt update
```

### 2. Install required tools

Install `software-properties-common` to manage PPAs:

```bash
sudo apt install software-properties-common
```

### 3. Add the GCC toolchain PPA

This PPA provides access to multiple versions of the GCC compiler:

```bash
sudo add-apt-repository ppa:ubuntu-toolchain-r/test
```

### 4. Update the package list again

```bash
sudo apt update
```

### 5. Install GCC and G++ (e.g., version 14)

```bash
sudo apt install gcc-14 g++-14 -y
```

### 6. Configure default GCC and G++ versions

Use `update-alternatives` to set the installed version as default:

```bash
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-14 14 --slave /usr/bin/g++ g++ /usr/bin/g++-14
```
