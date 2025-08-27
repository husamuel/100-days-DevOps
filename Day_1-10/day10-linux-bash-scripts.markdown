# Day 10: Linux Bash Scripts

## Problem
Create a script `news_backup.sh` to archive the `/var/www/html/news` directory, save it as a zip file in `/backup/`, and copy it to the backup server (`stbkp01`).

## Resolution
1. Create the script directory:
   ```bash
   sudo mkdir -p /scripts
   ```
2. Create and edit the backup script:
   ```bash
   sudo vi /scripts/news_backup.sh
   ```
   Script content:
   ```bash
   #!/bin/bash
   # Compacta o diretório de notícias
   zip -r /backup/xfusioncorp_news.zip /var/www/html/news

   # Copia o backup para o servidor de backup
   scp /backup/xfusioncorp_news.zip clint@stbkp01:/backup
   ```
3. Make the script executable:
   ```bash
   sudo chmod +x /scripts/news_backup.sh
   ```
4. Set up SSH key for password-less access:
   ```bash
   ssh-keygen
   ssh-copy-id clint@stbkp01
   ```
5. Run the script:
   ```bash
   /scripts/news_backup.sh
   ```
6. Verify the backup on the backup server:
   ```bash
   ssh clint@stbkp01
   ls -la /backup/
   ```

## Explanation
- **Create Script Directory**: The `mkdir -p /scripts` command creates a directory for the script.
- **Create Script**: The `news_backup.sh` script uses `zip -r` to recursively archive the `/var/www/html/news` directory into `/backup/xfusioncorp_news.zip` and `scp` to copy it to the backup server.
- **Set Permissions**: The `chmod +x` command makes the script executable.
- **SSH Key Setup**: Generating an SSH key and copying it to `stbkp01` enables password-less `scp` transfers.
- **Run and Verify**: Running the script creates and transfers the backup, and verifying on the backup server confirms the file's presence.