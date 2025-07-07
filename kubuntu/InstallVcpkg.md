# Install Vcpkg

This guide explains how to install and set up `vcpkg`, a C++ package manager, on Kubuntu.

---


## Installation Steps

### 1. Install Required Tools

Update your package list and install dependencies:

```bash
sudo apt update
sudo apt install curl zip unzip tar
```

---

### 2. Clone the vcpkg Repository

Clone `vcpkg` into your preferred directory:

```bash
git clone https://github.com/microsoft/vcpkg.git
```

---

### 3. Build the vcpkg Executable

Navigate into the vcpkg directory and run the bootstrap script:

```bash
cd vcpkg
./bootstrap-vcpkg.sh
```

---

### 4. Set Environment Variable

Add vcpkg to your PATH by modifying `.bashrc`:

```bash
echo 'export VCPKG_ROOT="$HOME/vcpkg"' >> ~/.bashrc
```

```bash
echo 'export PATH="$VCPKG_ROOT:$PATH"' >> ~/.bashrc
```

Apply the change immediately:

```bash
source ~/.bashrc
```

---

### 5. (Optional) Verify the Installation

Check the vcpkg version to confirm it's working:

```bash
vcpkg --version
```
