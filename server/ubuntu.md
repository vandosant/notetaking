### Updates
- `apt-get upgrade`

### User mgmt
`adduser admin`
`usermod -aG sudo admin`

### Server setup - Node
- https://github.com/nodesource/distributions#deb
- e.g. `curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash`
- `sudo apt-get install -y nodejs`
#### Ensure permissions
- `npm config get prefix`
  - /usr/local is what you want!, not /usr
  - https://docs.npmjs.com/getting-started/fixing-npm-permissions

### Server setup - Git
- `cd /var/www`
- `sudo mkdir /var/www`
- `git clone ...`
Permissions issues?
- `sudo chown -R $USER:$USER /var/www`

