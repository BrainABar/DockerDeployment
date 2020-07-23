# DockerDeployment
# Accessing Linode Ubuntu Server with Linode-CLI and set up SSH
```
    # Get the linode-cli
    > mkdir linode-cli
    > python3 -m pip install virtualenvironment
    > python3 -m virtualenv venv
    > source venv/bin/active
    > python -m pip install linode-cli --upgrade
    > linode-cli configure
    > linode-cli ssh root@<Server_Name>
    > apt update && apt upgrade
    > hostnamectl set-hostname personal-server
    > nano /etc/hosts # add server-ip and hostname under localhost
    > adduser admin
    > adduser admin sudo
    > exit
    > linode-cli ssh admin@<Server_Name>
    > mkdir .ssh

    Open a new local terminal and create an ssh key on local machine:
    > ssh-keygen
    > linode-cli linodes list # get servers ip
    > scp ~/.ssh/<filename>.pub admin@<ip-address>:~/.ssh/authorized_keys

    On server terminal:
    > sudo chmod 700 ~/.ssh/
    > sudo chmod 600 ~/.ssh/*
    > sudo nano /etc/ssh/sshd_config # Set PermitRootLogin to no and PasswordAuthentication no
    > sudo systemctl restart sshd

    # Configure Default firewall
    > sudo apt install ufw
    > sudo ufw default allow outgoing
    > sudo ufw default deny incoming
    > sudo ufw allow ssh # enable to allow ssh connections
    > sudo ufw enable
```

Process to Deploy to Linode server with Traefic reverse proxy:

Docker-compose files will hold various configurations for Traefik:

For local/testing:

For production:

