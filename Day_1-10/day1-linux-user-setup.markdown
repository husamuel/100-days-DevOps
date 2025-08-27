# Day 1: Linux User Setup with Non-Interactive Shell

## Problem
The task is to create a user named `john` on a Linux server with a non-interactive shell to prevent login capabilities.

## Resolution
1. Connect to the server via SSH:
   ```bash
   ssh <server>
   ```
2. Create the user `john` with a non-interactive shell:
   ```bash
   sudo useradd -s /sbin/nologin john
   ```

## Explanation
- **SSH Connection**: The first step involves connecting to the server using SSH to perform administrative tasks.
- **User Creation**: The `useradd` command creates a new user. The `-s /sbin/nologin` option sets the user's shell to `/sbin/nologin`, which prevents the user from logging in interactively. This is useful for service accounts or users intended for specific non-interactive tasks.