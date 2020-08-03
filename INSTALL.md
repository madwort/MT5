# Install notes

## Ubuntu 18

Based on https://www.digitalocean.com/community/tutorials/how-to-set-up-a-node-js-application-for-production-on-ubuntu-18-04

```bash
$ sudo npm install pm2@latest -g
$ cd ~/MT5-kaizo-snare
$ pm2 start server.js
$ pm2 startup systemd

```

### Apache2

```bash
$ sudo a2enmod proxy proxy_http
# create vhost file
$ sudo service apache2 restart
```

Vhost file like:

```
<VirtualHost *:80>
 ServerName hostname.com
 
 ProxyRequests On
 ProxyPass / http://localhost:3000/
 ProxyPassReverse / http://localhost:3000/
</VirtualHost>
```
