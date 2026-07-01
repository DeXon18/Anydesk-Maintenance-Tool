# macOS usage guide

This guide explains how to run the AnyDesk maintenance script on macOS.

The script is intended for authorized troubleshooting and maintenance tasks only. It does not reset licenses, usage restrictions, access controls or audit data.

## Requirements

- macOS.
- AnyDesk installed.
- Administrator permissions.
- Terminal.

## Script location

The macOS script is located at:

```txt
scripts/macos/anydesk-maintenance.sh
```

## Method 1: run manually

1. Download or clone this repository.
2. Go to:

```txt
scripts/macos/
```

3. Make the script executable:

```bash
chmod +x anydesk-maintenance.sh
```

4. Run with sudo:

```bash
sudo ./anydesk-maintenance.sh
```

5. Wait until the script finishes.
6. Review the output.

## Method 2: run from terminal (one-liner)

Open terminal and run:

```bash
curl -fsSL https://raw.githubusercontent.com/DeXon18/Anydesk-Maintenance-Tool/main/scripts/macos/anydesk-maintenance.sh -o anydesk-maintenance.sh
chmod +x anydesk-maintenance.sh
sudo ./anydesk-maintenance.sh
```

## What the script does

The script performs the following actions:

1. Stops the AnyDesk service if it is running.
2. Closes stuck `AnyDesk` processes.
3. Creates a temporary backup of selected user configuration files.
4. Removes non-critical user thumbnails and trace files.
5. Restores the backed-up user configuration.
6. Starts the AnyDesk service again.

## What the script does not do

The script does not:
- Reset or bypass the AnyDesk license.
- Unlock paid features.
- Remove commercial-use restrictions.
- Hide usage history.
- Disable audit or traceability mechanisms.
- Circumvent access controls.

## Safety notes

Only run this script on systems where you have explicit administrative permission.

Review the script before running it, especially if it was downloaded from the internet.

## Recommended support workflow

1. Confirm that AnyDesk is installed.
2. Confirm that the user has administrator permissions.
3. Run the script as administrator.
4. Check whether AnyDesk opens correctly.

## Related files

```txt
README.md
SECURITY.md
CHANGELOG.md
scripts/macos/anydesk-maintenance.sh
```
