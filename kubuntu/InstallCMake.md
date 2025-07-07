# Install CMake

This guide explains how to install a specific version of CMake manually on Kubuntu.

---

## Download CMake

Visit the official CMake release page:

```
https://github.com/Kitware/CMake/releases
```

Download the desired version (e.g., 3.30.9):

```bash
wget https://github.com/Kitware/CMake/releases/download/v3.30.9/cmake-3.30.9-linux-x86_64.tar.gz
```

---

## Extract the Archive

```bash
tar -zxvf cmake-3.30.9-linux-x86_64.tar.gz
```

---

## Move to /opt Directory

```bash
sudo mv cmake-3.30.9-linux-x86_64 /opt/
```

---

## Create Symbolic Links

```bash
sudo ln -sf /opt/cmake-3.30.9-linux-x86_64/bin/* /usr/bin/
```

---

## Verify Installation

(Optional) Check the installed version:

```bash
cmake --version
```
