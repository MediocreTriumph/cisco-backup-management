# Cisco Backup Management

This repository contains scripts for managing Cisco device configuration backups. It automatically organizes backups into device-specific folders, generates diffs between consecutive configurations, and maintains a specified number of backups per device.

## Features

- Automatically organizes configuration files into device-specific folders
- Generates readable diffs between consecutive configuration versions
- Maintains a specified number of recent backups (default: 5)
- Creates detailed logs of all operations
- Handles file validation and error checking
- Includes test script for generating sample configurations

## Scripts

- `backup_manager.py`: Main script for managing backups and generating diffs
- `test_generator.ps1`: PowerShell script for generating test configurations

## Usage

1. Update the `parent_folder` variable in `backup_manager.py` to point to your TFTP backup folder
2. Optionally adjust `max_backups` to change how many backups to keep per device
3. Run the script:
   ```bash
   python backup_manager.py
   ```

### Test Script

To test the backup manager with sample configurations:

1. Update the `testFolder` variable in `test_generator.ps1` to match your desired test location
2. Run the PowerShell script:
   ```powershell
   .\test_generator.ps1
   ```

## Requirements

- Python 3.6+
- PowerShell 5.0+ (for test script only)

## File Structure

The script expects configuration files to be named in the format:
```
devicename-confg_YYYYMMDD_HHMMSS
```

It will organize them into a structure like:
```
parent_folder/
├── devicename1/
│   ├── devicename1-confg_20240101_120000
│   ├── devicename1-confg_20240102_120000
│   └── 20240101_120000_20240102_120000-diff.txt
└── devicename2/
    ├── devicename2-confg_20240101_120000
    └── ...
```