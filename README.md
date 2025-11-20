# cleardns

A shell script to remove specified DNS servers from active network connections on macOS.

## Description

`cleardns` scans all active network services and removes the specified DNS servers from their DNS configuration. Other DNS servers remain unchanged.

## Requirements

- macOS
- Administrator privileges (may be required when running the script)

## Usage

```bash
./cleardns
```

The script will:
1. List all active network services
2. Check each service for the target DNS servers
3. Remove them if found, keeping other DNS servers intact
4. Display the results

## How It Works

The script uses macOS's `networksetup` command to:
- Get all network services: `networksetup -listallnetworkservices`
- Get current DNS servers: `networksetup -getdnsservers <service>`
- Update DNS servers: `networksetup -setdnsservers <service> <dns1> <dns2> ...`

## Target DNS Servers

To modify the target DNS servers, edit the `DNS_TO_REMOVE` array in the script.

## Notes

- The script requires administrator privileges to modify network settings
- If only the target DNS servers are configured, all DNS servers will be removed
- The script only processes active network services

