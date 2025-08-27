# Day 7: Linux SSH Authentication

## Problem
Set up password-less SSH access from the `thor` user on a jump host to three app servers (`tony@stapp01`, `steve@stapp02`, `banner@stapp03`).

## Resolution
1. Check for existing SSH keys:
   ```bash
   ls ~/.ssh/
   ```
2. Generate a new SSH key pair:
   ```bash
   ssh-keygen -t rsa -N "" -f ~/.ssh/id_rsa
   ```
3. Copy the public key to the app servers:
   ```bash
   ssh-copy-id tony@stapp01
   ssh-copy-id steve@stapp02
   ssh-copy-id banner@stapp03
   ```

## Explanation
- **Check SSH Keys**: The `ls ~/.ssh/` command checks if an SSH key pair already exists for the `thor` user.
- **Generate SSH Key**: The `ssh-keygen` command creates a new RSA key pair without a passphrase (`-N ""`) and saves it to `~/.ssh/id_rsa`.
- **Copy Public Key**: The `ssh-copy-id` command copies the public key to the specified users on the app servers, enabling password-less SSH access by adding the key to `~/.ssh/authorized_keys` on each server.