# digitalocean-setup
Guideline (inc script) to setup Digitalocean VPS (Ubuntu)

## First login using Root user: Create USER, set FIREWALL, and copy SSH KEY
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

## First login using NewUser: UPDATE, UPGRADE, AUTOCLEAN, AUTOREMOVE
1. Update `sudo apt update`
2. Upgrade `sudo apt upgrade`
3. Auto Clean `sudo apt autoclean`
4. Auto Remove `sudo apt autoremove`
5. Auto Remove (purge) `sudo apt autoremove --purge`
6. Re-Update `sudo apt update`
7. Re-Upgrade `sudo apt upgrade`

## Install NGINX and allow Firewall for HTTP HTTPS
1. Install NGINX, follow: [https://nginx.org/en/linux_packages.html#Ubuntu](https://nginx.org/en/linux_packages.html#Ubuntu)
2. Start NGINX `sudo service nginx restart`
2. Allow HTTP and HTTPS:  
  a. `sudo ufw allow http`  
  b. `sudo ufw allow https`  
  c. `sudo ufw reload`

## Install NVM and Install NodeJs
1. Install NVM, follow: [https://github.com/nvm-sh/nvm](https://github.com/nvm-sh/nvm)
2. Check NVM version `nvm --version`
3. Install NODE.JS `nvm install --lts`
4. Check NodeJs version `node --version`
5. Check NPM version `npm --version`

## Install Git
1. Add PPA to get the latest stable upstream Git version `add-apt-repository ppa:git-core/ppa`
1. APT Update `sudo apt update`
3. Install Git `sudo apt install git`

## Install HAProxy
1. Add PPA to get the specific version (latest LTS) `sudo add-apt-repository ppa:vbernat/haproxy-2.2`
1. APT Update `sudo apt update`
3. Install HAProxy `sudo apt install haproxy`

## Install Pritunl-Client
1. [Install Pritunl Server](https://pritunl.com/) first
1. Make sure `cat /etc/apt/sources.list.d/pritunl.list` is same with value on the pritunl server doc above
2. `sudo apt install apt-transport-https dirmngr`
3. `sudo apt update`
4. `sudo apt install pritunl-client`
   If facing error, then:
5. `sudo dpkg -i --force-overwrite /var/cache/apt/archives/pritunl-client_1.2.2799.2-0ubuntu1~bionic_amd64.deb`
6. `sudo apt install pritunl-client -f`
