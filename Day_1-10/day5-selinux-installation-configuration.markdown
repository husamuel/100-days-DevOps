# Day 5: SELinux Installation and Configuration

## Problem
On App Server 1 in the Stratos Datacenter, install required SELinux packages and permanently disable SELinux without requiring an immediate reboot.

## Resolution
1. Check the operating system:
   ```bash
   cat /etc/*release
   ```
2. Install SELinux packages:
   ```bash
   sudo yum install -y selinux-policy selinux-policy-targeted policycoreutils
   ```
3. Edit the SELinux configuration file:
   ```bash
   sudo vi /etc/selinux/config
   ```
   Change the line:
   ```
   SELINUX=enforcing
   ```
   to:
   ```
   SELINUX=disabled
   ```

## Explanation
- **Check OS**: The `cat /etc/*release` command identifies the operating system (e.g., CentOS, RHEL) to ensure compatibility with the `yum` package manager.
- **Install SELinux Packages**: The `yum install` command installs `selinux-policy` (base SELinux rules), `selinux-policy-targeted` (targeted policy for high-risk services), and `policycoreutils` (SELinux management tools).
- **Disable SELinux**: Editing `/etc/selinux/config` to set `SELINUX=disabled` ensures SELinux is disabled on the next boot. No immediate reboot is needed, as specified, with the change taking effect after the planned maintenance reboot.