# digitalocean-setup
Guideline (inc script) to setup Digitalocean VPS (Ubuntu)

## Create USER, set FIREWALL, and copy SSH KEY
1. Add user `adduser username`
2. Granting administrative privileges `usermod -aG sudo alina`
3. Setup Firewall:
  a. Checkt firewall app list `ufw app list`
  b. Allow OpenSSH `ufw allow OpenSSH`
  c. Enable firewall `ufw enable`
  d. Check firewall status `ufw status`
4. Copy SSH Auth keys into new username home directory:
  a. Using rsync `rsync --archive --chown=username:username ~/.ssh /home/username`
  b. or Copy it Manually:
    i. Create .ssh directory in the username home `mkdir /home/username/.ssh`
    ii. Copy authorized_keys into username home `cp /root/.ssh/authorized_keys /home/username/.ssh`
    iii. Change .ssh owner `chown -R alina:alina /home/username/.ssh`
