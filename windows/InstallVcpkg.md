# Vcpkg Manual Installation Guide

## Recommendation

To avoid conflicts with environment variables, it is recommended to remove the pre-installed vcpkg bundled with Visual Studio before proceeding with a manual installation.

Reference:  
https://learn.microsoft.com/zh-tw/vcpkg/get_started/get-started?pivots=shell-powershell

---

## Installation Steps

1. Clone the vcpkg repository to your preferred directory:
   ```
   git clone https://github.com/microsoft/vcpkg.git
   ```

2. Run the bootstrap script to build the vcpkg executable:
   ```
   cd vcpkg
   .\bootstrap-vcpkg.bat
   ```
3. Set the VCPKG_ROOT environment variable to the path of your vcpkg directory.

4. Add %VCPKG_ROOT% to your system PATH to make vcpkg accessible from any terminal.

5. (Optional) Verify the installation by checking the vcpkg version:
   ```
   vcpkg --version
   ```