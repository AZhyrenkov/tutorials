# NGINX

## Installation

```
sudo apt-get update
sudo apt-get install nginx
```

Check status

`systemctl status nginx`

`top` - displays linux processes (incl user, PID, command, cpu mem usage)

## Allow nginx on firewall

```
sudo ufw status
sudo ufw app list
sudo ufw allow 'Nginx HTTP'
```

## Nginx Configuration

`/etc/nginx/nginx.conf`

To see configuration parameters run `nginx -V`

Nginx runs under `www-data` user by default. 

## Apps Configuration

Each Nginx virtual server should be described by a file in the /etc/nginx/sites-available directory. 
You select which sites you want to enable by making symbolic links to those in the /etc/nginx/sites-enabled directory.

Create new file in /etc/nginx/sites-available/myapp.nginx.conf
Example configuration: https://gist.github.com/postrational/5747293#file-hello-nginxconf
Important is to define hostname, port and proxy_pass either to gunicorn directly via IP and port 
or using linux socket file that gunicorn uses.

To enable site create symlink in sites-enabled:

`ln -s /etc/nginx/sites-available/myapp.nginx.conf /etc/nginx/sites-enabled/myapp.nginx.conf`

## Restart and Reload

`service nginx reload` - checks configuration first before restarting (safer).

`service nginx restart` - stops and starts nginx 

# Further reading

 - http://michal.karzynski.pl/blog/2013/06/09/django-nginx-gunicorn-virtualenv-supervisor/
 - https://www.fullstackpython.com/blog/python-3-django-gunicorn-ubuntu-1604-xenial-xerus.html
