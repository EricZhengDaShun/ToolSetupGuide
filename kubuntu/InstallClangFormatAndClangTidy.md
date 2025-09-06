# Install LLVM

This guide explains how to manually install a specific version of LLVM on Kubuntu.

---

## Download LLVM

Visit the official LLVM release page:

```
https://github.com/llvm/llvm-project/releases
```

Download the desired version (e.g., LLVM 21.1.0):

```bash
wget https://github.com/llvm/llvm-project/releases/download/llvmorg-21.1.0/LLVM-21.1.0-Linux-X64.tar.xz
```

---

## Extract the Package

```bash
tar Jxvf LLVM-21.1.0-Linux-X64.tar.xz
```

---

## Move to /opt Directory

```bash
sudo mv LLVM-21.1.0-Linux-X64 /opt/
```

---

## Create Symbolic Links

```bash
sudo ln -sf /opt/LLVM-21.1.0-Linux-X64/bin/* /usr/bin/
```

---

## Verify Installation (Optional)

```bash
clangd --version
```

```bash
clang-tidy --version
```

```bash
clang-format --version
```
