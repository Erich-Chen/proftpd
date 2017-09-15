# proftpd
Guideline to Set up Proftpd FTP server on Ubuntu Server LTS 16.04.3
* TO BE UPDATED

## Install
```
sudo apt update && sudo apt upgrade -yy
sudo apt install -y proftpd openssl
# Choose "Stand alone" when promoted during installation

```

## Basic configuration
```
sudo cp /etc/proftpd/proftpd.conf /etc/proftpd/proftpd.conf.bak
sudo vim /etc/proftpd/proftpd.conf
```
Update Below Lines:  
```
ServerName   "Domain_or_IPAddress"        # Edit this line
DefaultRoot   ~                           # uncomment this line
Include      /etc/proftpd/tls.conf        # uncomment this line
```

## Enalbe TLS
You may find below guideline in the file `/etc/proftpd/tls.conf`
```
sudo openssl req -x509 -newkey rsa:1024 -keyout /etc/ssl/private/proftpd.key -out /etc/ssl/certs/proftpd.crt -nodes -days 3650
sudo chmod 0600 /etc/ssl/private/proftpd.key
```

## Add New FTP user
I would rather add system user without login shell. It is easy to control user access with normal linux way.   
```
read -p "Enter username: " username
sudo useradd -b "/home/ftp" -G "ftpusers" -N -m -s "/bin/false" $username
sudo passwd $username
```
