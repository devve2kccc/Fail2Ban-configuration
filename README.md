# Fail2Ban
Fail2Ban helps you to keep your SSH server primarily protected from brute force and ddos ​​attacks. But it can also be used on http servers, webmail, and more.

#### Example:
If you set the maximum number of attempts to be 3. If a certain IP exceeds these login attempts, fail2ban causes the ip to automatically be BAN by iptables.

## Installation

```bash
#### Debian/Ubuntu
apt-get update
apt-get install fail2ban

#### Fedora
dnf update
dnf install fail2ban

#### Centos
yum update && yum install epel-release
yum install fail2ban
```

## Configuration
#### jail.conf will be the file where you want to change some settings !!
```bash
# To change the settings, I advise you to rename the file from .conf to .local
cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local

# Open jail.local with any editor
nano /etc/fail2ban/jail.local

# Whitelist IP: you must put your IP in the fail2ban whitelist, to be immune to your actions.
Search for "ignoreip" and uncomment (remove #)
ignoreip = 127.0.0.1/8 "PUT YOUR IP"
ignoreip = 127.0.0.1/8 143.23.134.54 

# Edit:
bantime = 3600 (I like to put 3600s)
findtime = 600 (I like leave 600s)
maxretry = 4

# Go to [sshd] and put this config
[sshd]

enabled  = true
port     = your ssh port (default: 22)
filter   = sshd
logpath  = /var/log/auth.log
maxretry = 3
```

## this is a simple configuration!

# Enable your fail2ban

```bash
#### Debian/Ubuntu
# it starts automatically after installation, but you can restart it using
systemctl restart fail2ban

#### Fedora
systemctl start fail2ban
systemctl enable fail2ban

#### Centos
systemctl start fail2ban
systemctl enable fail2ban
```

### See more about fail2ban on [Fail2Ban](https://www.fail2ban.org/)

## Thanks

Donate: [Paypal](paypal.me/devve2k)
