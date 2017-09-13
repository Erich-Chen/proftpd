# proftpd
Guideline to Set up Proftpd FTP server on Ubuntu Server LTS 16.04.3
* TO BE UPDATED

## Install
```
sudo apt update && sudo apt upgrade -yy
sudo apt install -y proftpd openssl
```

## Basic configuration
```
sudo cp /etc/proftpd/proftpd.conf /etc/proftpd/proftpd.conf.bak
sudo vim /etc/proftpd/proftpd.conf
```



## Enalbe TLS
```
sudo vim /etc/proftpd/proftpd.conf
sudo nano /etc/proftpd/tls.conf
sudo openssl req -x509 -newkey rsa:1024 -keyout /etc/ssl/private/proftpd.key -out /etc/ssl/certs/proftpd.crt -nodes -days 3650
sudo nano /etc/proftpd/tls.conf
sudo chmod 0600 /etc/ssl/private/proftpd.key
sudo nano /etc/proftpd/tls.conf
```

## Add New FTP user
I would rather add system user without login shell. It is easy to control user access with normal linux way.   
```

```
