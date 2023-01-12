Order a VPS from OVH
Optionnaly assign a DNS entry to the VPS IP Address

Open an ssh session to remote vps server
`ssh ubuntu@remote-host.fqdn` 

Add user
`sudo adduser patrick`
`sudo usermod -aG sudo,users username`

Test sudo access
`su - username`
`sudo ls -la /root`

Exit remote machine:
`exit`
`exit`

On local machine: 
`ssh-keygen -t rsa -b 4096 -f .ssh/username@remote-host.fqdn`
`ssh-copy-id -i ~/.ssh/id_rsa.pub user@remote-host.fqdn`

Test access:
`ssh -i .ssh/username@remote-host.fqdn username@remote-host.fqdn`

Disable ssh root access on remote machine:
`sudo vi /etc/ssh/sshd_config`
># Authentication: 
>LoginGraceTime 120
>PermitRootLogin no
>StrictModes yes

`sudo systemctl restart sshd`

Install Failban
`sudo apt install fail2ban`


Disable password auth on ssh for username users but one