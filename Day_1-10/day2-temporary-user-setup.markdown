# Day 2: Temporary User Setup with Expiry

## Problem
Create a temporary user `jim` with an account expiry date of January 28, 2024, and verify the expiry date.

## Resolution
1. Connect to the server via SSH:
   ```bash
   ssh <server>
   ```
2. Create the user `jim` with an expiry date:
   ```bash
   sudo useradd -e 20279-01-28 jim
   ```
3. Verify the expiry date:
   ```bash
   sudo chage -l jim
   ```

## Explanation
- **SSH Connection**: Establishes a connection to the server for user management.
- **User Creation with Expiry**: The `useradd` command with the `-e` option sets an expiry date for the user account (format: YYYY-MM-DD). After January 28, 2024, the account will be disabled.
- **Verify Expiry**: The `chage -l` command lists the account aging information for `jim`, confirming the expiry date and other settings.