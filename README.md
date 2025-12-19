# xsukax Useful Commands

This command lists all subdirectories in the current directory in a clean, readable, and numbered format, making it easier to quickly see and reference folder names. It works by scanning only the current directory level (without going into subfolders), selecting directories only, and excluding the special entry that represents the current directory itself. The output is then cleaned to remove the technical path prefix so that only the folder names remain, and finally each directory is automatically numbered in order with consistent formatting. Overall, the command is useful for organizing, reviewing, or documenting directory structures in a simple and beginner-friendly way while keeping the output neat and human-readable.

`find . -maxdepth 1 -type d ! -name '.' | sed 's|^\./||' | nl -w2 -s'. '`

---
The following Windows PowerShell command downloads and installs the latest version of the Windows Package Manager (winget) from the official GitHub repository. It first uses `Invoke-WebRequest` to fetch the latest `Microsoft.DesktopAppInstaller_8wekyb3d8bbwe.msixbundle` file from the specified URL, saving it to the system's temporary directory (`$env:TEMP`). After the file is downloaded, the `Add-AppxPackage` command is used to install the MSIX bundle from the temporary location, allowing the user to get the latest version of the Windows Package Manager (winget) tool for managing apps and packages on Windows systems. This command is useful for quickly installing or updating winget without needing to visit the official site manually.

`Invoke-WebRequest -Uri https://github.com/microsoft/winget-cli/releases/latest/download/Microsoft.DesktopAppInstaller_8wekyb3d8bbwe.msixbundle -OutFile $env:TEMP\AppInstaller.msixbundle; Add-AppxPackage -Path $env:TEMP\AppInstaller.msixbundle`

---
