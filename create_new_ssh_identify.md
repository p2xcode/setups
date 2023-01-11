# Create new identify with a new SSH Key Pair

`ssh-keygen -t rsa -b 4096 -f ~/.ssh/user@fqdn.host.name`
`vi ~/.ssh/config`
Host *
    IdentityFile ~/.ssh/username@remote-host.fqdn

`ssh-copy-id -i ~/.ssh/user@fqdn.host.name user@fqdn.host.name`
