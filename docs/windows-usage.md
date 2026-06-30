# Windows usage guide

This guide explains how to run the AnyDesk maintenance script on Windows.

The script is intended for authorized troubleshooting and maintenance tasks only. It does not reset AnyDesk IDs, licenses, usage restrictions, access controls or audit data.

## Requirements

- Windows 10 or Windows 11.
- AnyDesk installed.
- Administrator permissions.
- PowerShell or Command Prompt.
- Access to the AnyDesk Windows service.

## Script location

The Windows script is located at:

```txt
scripts/windows/anydesk-maintenance.bat
```

## Method 1: run manually

1. Download or clone this repository.
2. Go to:

```txt
scripts/windows/
```

3. Right-click:

```txt
anydesk-maintenance.bat
```

4. Select:

```txt
Run as administrator
```

5. Wait until the script finishes.
6. Review the final message and log path.

## Method 2: run from PowerShell

Open PowerShell as administrator and run:

```powershell
Invoke-WebRequest -Uri "https://raw.githubusercontent.com/YOUR_USER/anydesk-maintenance-toolkit/main/scripts/windows/anydesk-maintenance.bat" -OutFile "$env:TEMP\anydesk-maintenance.bat"
Start-Process "$env:TEMP\anydesk-maintenance.bat" -Verb RunAs
```

Replace `YOUR_USER` with your GitHub username or organization.

## What the script does

The script performs the following actions:

1. Checks for administrator permissions.
2. Locates the AnyDesk service.
3. Stops the AnyDesk service if it is running.
4. Closes stuck `AnyDesk.exe` processes.
5. Creates a temporary backup of selected user configuration files.
6. Removes non-critical user thumbnails and trace files.
7. Restores the backed-up user configuration.
8. Starts the AnyDesk service again.
9. Opens AnyDesk if the executable is found.
10. Saves an execution log.

## What the script does not do

The script does not:

- Reset the AnyDesk ID.
- Reset or bypass the AnyDesk license.
- Unlock paid features.
- Remove commercial-use restrictions.
- Modify device identity.
- Hide usage history.
- Disable audit or traceability mechanisms.
- Circumvent access controls.

## Log file

The latest execution log is saved to:

```txt
%TEMP%\AnyDesk_Maintenance_last.log
```

The temporary working directory is deleted after execution.

## Expected output

If everything works correctly, the script will show:

```txt
Maintenance completed successfully.
Log saved to: "%TEMP%\AnyDesk_Maintenance_last.log"
```

## Common errors

### This script must be run as administrator

Cause:

```txt
The script was started without elevated permissions.
```

Fix:

```txt
Right-click the script and select "Run as administrator".
```

Or run PowerShell as administrator before launching it.

### AnyDesk service does not exist

Cause:

```txt
AnyDesk is not installed, or the Windows service is missing.
```

Fix:

```txt
Reinstall AnyDesk or verify that the service exists in services.msc.
```

### Timeout while waiting for AnyDesk service to stop

Cause:

```txt
The AnyDesk service did not stop within the configured timeout.
```

Fix:

```txt
Restart the computer and run the script again.
```

If the issue persists, check Windows Event Viewer.

### AnyDesk.exe was not found in the expected paths

Cause:

```txt
AnyDesk is installed in a custom location, or the executable is missing.
```

Expected paths:

```txt
%ProgramFiles%\AnyDesk\AnyDesk.exe
%ProgramFiles(x86)%\AnyDesk\AnyDesk.exe
```

Fix:

```txt
Check the AnyDesk installation path and update the script variables if needed.
```

## Safety notes

Only run this script on systems where you have explicit administrative permission.

Review the script before running it, especially if it was downloaded from the internet.

Do not share logs publicly if they include usernames, local paths, device names or organization-specific information.

## Recommended support workflow

1. Confirm that AnyDesk is installed.
2. Confirm that the user has administrator permissions.
3. Run the script as administrator.
4. Check whether AnyDesk opens correctly.
5. Review the log if the script reports an error.
6. Escalate only if the service, executable or permissions are damaged.

## Related files

```txt
README.md
SECURITY.md
CHANGELOG.md
scripts/windows/anydesk-maintenance.bat
```
