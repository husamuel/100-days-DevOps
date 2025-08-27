# Day 3: Secure Root SSH Access

## Problem
Disable direct SSH root login on all application servers within the Stratos Datacenter to enhance security.

## Resolution
1. Connect to the server via SSH:
   ```bash
   ssh <server>
   ```
2. Edit the SSH configuration file:
   ```bash
   sudo vi /etc/ssh/sshd_config
   ```
3. Modify or add the following line:
   ```
   PermitRootLogin no
   ```
4. Restart the SSH service:
   ```bash
   sudo systemctl restart sshd
   ```

## Explanation
- **SSH Connection**: Connect to the server to modify its SSH configuration.
- **Edit SSH Configuration**: The `/etc/ssh/sshd_config` file controls SSH daemon settings. Setting `PermitRootLogin no` disables direct root login via SSH, forcing users to log in with a non-root account and use `sudo` for privileged actions.
- **Restart SSH Service**: Restarting the `sshd` service applies the configuration changes. This step ensures the new settings take effect without requiring a server reboot.