# xsukax Useful Commands

This command lists all subdirectories in the current directory in a clean, readable, and numbered format, making it easier to quickly see and reference folder names. It works by scanning only the current directory level (without going into subfolders), selecting directories only, and excluding the special entry that represents the current directory itself. The output is then cleaned to remove the technical path prefix so that only the folder names remain, and finally each directory is automatically numbered in order with consistent formatting. Overall, the command is useful for organizing, reviewing, or documenting directory structures in a simple and beginner-friendly way while keeping the output neat and human-readable.

```
find . -maxdepth 1 -type d ! -name '.' | sed 's|^\./||' | nl -w2 -s'. '
```

---
The following Windows PowerShell command downloads and installs the latest version of the Windows Package Manager (winget) from the official GitHub repository. It first uses `Invoke-WebRequest` to fetch the latest `Microsoft.DesktopAppInstaller_8wekyb3d8bbwe.msixbundle` file from the specified URL, saving it to the system's temporary directory (`$env:TEMP`). After the file is downloaded, the `Add-AppxPackage` command is used to install the MSIX bundle from the temporary location, allowing the user to get the latest version of the Windows Package Manager (winget) tool for managing apps and packages on Windows systems. This command is useful for quickly installing or updating winget without needing to visit the official site manually.

```
Invoke-WebRequest -Uri https://github.com/microsoft/winget-cli/releases/latest/download/Microsoft.DesktopAppInstaller_8wekyb3d8bbwe.msixbundle -OutFile $env:TEMP\AppInstaller.msixbundle; Add-AppxPackage -Path $env:TEMP\AppInstaller.msixbundle
```

---
This Bash script lists the distinct users who currently have active SSH connections on the system. The lsof -i tcp -n command displays all open TCP network connections without attempting DNS resolution, grep '\<ssh\>' filters that list to only entries related to the SSH service, and awk '{print $3}' extracts the third column, which corresponds to the username owning each connection. Finally, sort | uniq orders the usernames and removes duplicates, producing a clean list of unique users with active SSH sessions.

```
#!/bin/bash
lsof -i tcp -n | grep '\<ssh\>' | awk '{print $3}' | sort | uniq
```

---
This Bash script interactively creates a restricted user account and locks down its environment. It prompts for a username, then uses `useradd` to create the account with a home directory under `/home`, assigns the restricted shell (`rbash`), and sets a password. After switching to the user’s home directory, it appends `PATH=""` to `.profile` to prevent the user from executing commands outside explicitly allowed paths. Finally, it tightens permissions by making the home directory read-and-execute only and setting key shell configuration files (`.bash_logout`, `.bashrc`, and `.profile`) to read-only, limiting the user’s ability to modify their environment or escape the restricted shell.

```
#!/bin/bash

echo -n "Enter username: "
read usernamee;

cd /tmp/
useradd $usernamee -m -d /home/$usernamee -s /bin/rbash
passwd $usernamee
cd /home/$usernamee/
echo 'PATH=""' >> /home/$usernamee/.profile
chmod 555 /home/$usernamee/
chmod 444 .bash_logout .bashrc .profile
```

---
These commands show how to import and export a MySQL database using the command line. The import command uses the `mysql` client to connect to a specified database as a given user, prompts for the password, and then reads SQL statements from `file.sql`, applying them to `database_name`. The export command uses `mysqldump` to connect to the same database and write its entire structure and data as SQL statements into `file.sql`, creating a backup that can later be restored using the import command.

Import:
```
mysql -u username -p database_name < file.sql
```
Export:
```
mysqldump -u username -p database_name > file.sql
```

---
