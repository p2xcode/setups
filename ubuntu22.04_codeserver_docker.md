# How to build a Linux box with code server and docker

## Install Ubuntu Server 22.04 with no add-on and no snap (just a vanilla server)

- `vi .ssh/config`<br /><br />
    Add the following lines
    ```
        Host
            User patrick    
            HostName <remote-host.fqdn>    
            IdentityFile ~/.ssh/id_rsa
    ```

- `ssh-copy-id -i ~/.ssh/id_rsa.pub user@remote-host.fqdn`
- `ssh remote-host`
- `sudo apt install avahi-daemon`

## Install Code Server
- `curl -fsSL https://code-server.dev/install.sh | sh`
- `sudo systemctl enable —now code-server@$USER`
- `sudo systemctl start code-server@$USER`
- `sed -i.bak 's/auth: password/auth: none/' ~/.config/code-server/config.yaml`
- `sudo systemctl restart code-server@$USER`



ON THE LOCAL MACHINE:
- `ssh -N -L 8080:127.0.0.1:8080 [user]@<remote-host.fqdn>`


## Install Docker

- `sudo apt-get remove docker docker-engine docker.io containerd runc`
- `sudo apt-get update`
- `sudo apt-get install ca-certificates curl gnupg lsb-release`
- `sudo mkdir -p /etc/apt/keyrings`
- `curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg`
- `echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null`
- `sudo apt-get update`
- `sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin`
- `sudo docker run hello-world`
- `sudo usermod -aG docker $USER`
- logout and log back in
