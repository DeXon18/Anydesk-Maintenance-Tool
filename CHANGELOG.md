# Changelog

All notable changes to this project will be documented in this file.

This project follows a simple versioning format:

```txt
MAJOR.MINOR.PATCH
```

## [Unreleased]

### Planned

- Add Linux maintenance script.
- Add Linux usage documentation.
- Add troubleshooting guide.
- Add issue templates.
- Add pull request template.

## [0.1.0] - 2026-06-30

### Added

- Initial Windows maintenance script.
- Administrator permission check.
- AnyDesk service stop and start flow.
- Detection and termination of stuck AnyDesk processes.
- Temporary user configuration backup.
- Safe cleanup for user thumbnails and trace files.
- User configuration restore after cleanup.
- Execution logging.
- Final log copy to:

```txt
%TEMP%\AnyDesk_Maintenance_last.log
```

- Temporary working directory cleanup after execution.

### Security

- Added explicit scope limitation for authorized maintenance use only.
- Avoided license, device identity, access control, audit and traceability modifications.
- Avoided generic temporary folder cleanup outside the script working directory.

### Notes

- Windows support is available.
- Linux support is planned.
- macOS support is not included.
