# Day 8: Install Ansible

## Problem
Install Ansible version 4.10.0 on a Jump Host using `pip3`, ensuring it is accessible to all system users, turning the Jump Host into an Ansible Controller.

## Resolution
1. Install Ansible using `pip3`:
   ```bash
   sudo pip3 install ansible==4.10.0
   ```

## Explanation
- **Install Ansible**: The `sudo pip3 install ansible==4.10.0` command installs Ansible version 4.10.0 system-wide, making it accessible to all users. Using `sudo` ensures the installation is in a global directory (e.g., `/usr/local/bin`), and specifying the version ensures compatibility with the required setup.