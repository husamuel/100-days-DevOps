# Day 9: MariaDB Troubleshooting

## Problem
The MariaDB service on the database server is not running, causing the Nautilus application to be down. Troubleshoot and resolve the issue.

## Resolution
1. Attempt to start MariaDB:
   ```bash
   systemctl start mariadb
   ```
2. Check the service status:
   ```bash
   systemctl status mariadb
   ```
3. Check permissions on the MySQL data directory:
   ```bash
   ls -ld /var/lib/mysql
   ```
4. Review the MariaDB log for errors:
   ```bash
   cat /var/log/mariadb/mariadb.log | tail -30
   ```
5. Fix permissions on the PID file directory:
   ```bash
   chown -R mysql:mysql /run/mariadb
   chmod 755 /run/mariadb
   ```
6. Restart MariaDB:
   ```bash
   systemctl start mariadb
   ```
7. Verify the service status:
   ```bash
   systemctl status mariadb
   ```

## Explanation
- **Initial Start Attempt**: The `systemctl start mariadb` command attempts to start the MariaDB service but fails with an exit status of 1, indicating a configuration or permission issue.
- **Check Permissions**: The `ls -ld /var/lib/mysql` command confirms that the MySQL data directory has correct permissions (`drwxr-xr-x mysql`).
- **Log Analysis**: The log (`/var/log/mariadb/mariadb.log`) reveals a permission error preventing MariaDB from creating its PID file in `/run/mariadb`.
- **Fix Permissions**: The `chown -R mysql:mysql /run/mariadb` and `chmod 755 /run/mariadb` commands correct the ownership and permissions of the PID file directory.
- **Restart and Verify**: Restarting MariaDB and checking its status confirms the service is now running correctly.