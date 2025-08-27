# Day 6: Create a Cron Job

## Problem
Install the `cronie` package on all Nautilus app servers, start the `crond` service, and add a cron job as the root user to run `echo hello > /tmp/cron_text` every 5 minutes.

## Resolution
1. Install the `cronie` package:
   ```bash
   yum install -y cronie
   ```
2. Enable and start the `crond` service:
   ```bash
   systemctl enable crond
   systemctl start crond
   ```
3. Add the cron job:
   ```bash
   echo "*/5 * * * * echo hello > /tmp/cron_text" >> /var/spool/cron/root
   ```
4. Restart the `crond` service:
   ```bash
   systemctl restart crond
   ```

## Explanation
- **Install Cronie**: The `cronie` package provides the cron daemon for scheduling tasks.
- **Enable and Start Crond**: `systemctl enable crond` ensures the service starts on boot, and `systemctl start crond` starts it immediately.
- **Add Cron Job**: Appending the cron job to `/var/spool/cron/root` schedules `echo hello > /tmp/cron_text` to run every 5 minutes (`*/5 * * * *`) as the root user.
- **Restart Crond**: Restarting the `crond` service ensures the new cron job is loaded and active.