# letsenc

# crontab
```
1 1 * * 1 cd /home/ubuntu/; ./letsencrypt.sh ./letsencrypt.conf >> /home/ubuntu/lets.log 2>&1; sudo service nginx reload
```

# nginx
```
server{
    ...
    listen      443 default_server ssl;
    ssl_certificate /home/ubuntu/wxbtml.chained.crt;
    ssl_certificate_key /home/ubuntu/wxbtml.key;
    ...
}

location /.well-known/ {
        alias /home/ubuntu/flask/examples/minitwit/www/.well-known/;
    }
```

# permission
```
sudo chown -R www-data:www-data  .well-known/
```

# apache
```
a2enmod ssl
apachectl configtest
```
