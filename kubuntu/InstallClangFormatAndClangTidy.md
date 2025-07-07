# Install LLVM

This guide explains how to manually install a specific version of LLVM on Kubuntu.

---

## Download LLVM

Visit the official LLVM release page:

```
https://github.com/llvm/llvm-project/releases
```

Download the desired version (e.g., LLVM 20.1.7):

```bash
wget https://github.com/llvm/llvm-project/releases/download/llvmorg-20.1.7/LLVM-20.1.7-Linux-X64.tar.xz
```

---

## Extract the Package

```bash
tar Jxvf LLVM-20.1.7-Linux-X64.tar.xz
```

---

## Move to /opt Directory

```bash
sudo mv LLVM-20.1.7-Linux-X64 /opt/
```

---

## Create Symbolic Links

```bash
sudo ln -sf /opt/LLVM-20.1.7-Linux-X64/bin/* /usr/bin/
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
