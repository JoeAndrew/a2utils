Debian style apache2/nginx configurator for Gentoo
==================================================

### Gentoo install

Clone joe-overlay from https://github.com/JoeAndrew/joe-overlay
```bash
$ emerge a2utils
```

### Manual Installation on non Gentoo System

$ git clone https://github.com/JoeAndrew/a2utils.git

$ cd a2utils

For Apache create a file wiht this:

```bash
cat << EOF >> install
#!/bin/sh

mkdir -p /etc/apache2/sites-{available,enabled}
cp a2* /usr/sbin
chmod +x /usr/sbin/a2*
echo "Include /etc/apache2/sites-enabled/" >>/etc/apache2/httpd.conf
EOF
```
or for Nginx this:

```bash
cat << EOF >> install
#!/bin/sh

mkdir -p /etc/nginx/sites-{available,enabled}
cp n2* /usr/sbin
chmod +x /usr/sbin/n2*
echo "Include /etc/nginx/sites-enabled/" >>/etc/nginx/nginx.conf
EOF
```

$ sudo sh install

Done

## Usage

### a(n)2en(dis)site

For the scripts to work, you first need to create your virtual host in the /etc/apache2/sites-available folder.
The a2ensite script is run with only 1 argument: the name of the virtual-host file. It then links the file to the sites-enabled folder, checks for any syntax errors and restarts your apache.

The a2dissite script disables the virtualhost by removing the link in the sites-enabled folder and restarts apache.
