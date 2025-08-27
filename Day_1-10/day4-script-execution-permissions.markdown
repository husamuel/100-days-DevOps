# Day 4: Script Execution Permissions

## Problem
Grant executable permissions to the `/tmp/xfusioncorp.sh` script on App Server 1, ensuring all users can execute it.

## Resolution
1. Grant executable permissions:
   ```bash
   chmod a+x /tmp/xfusioncorp.sh
   ```
2. Verify the permissions:
   ```bash
   ls -l /tmp/xfusioncorp.sh
   ```

## Explanation
- **Set Permissions**: The `chmod a+x` command adds executable (`x`) permissions for all users (owner, group, and others) to the script `/tmp/xfusioncorp.sh`. This allows any user on the system to run the script.
- **Verify Permissions**: The `ls -l` command displays the file's permissions, confirming that the executable bit is set for all users (e.g., `-rwxr-xr-x`).