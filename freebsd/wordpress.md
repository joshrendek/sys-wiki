# Packages

```
pkg install php56 php56-mysql php56-curl php56-hash  \
php56-zlib php56-mysql php56-curl apache24 mod_php56 vim \
mariadb55-server htop php56-opcache php56-curl php56-calendar \
php56-gd php56-ftp php56-json php56-openssl php56-readline \
php56-recode php56-soap php56-sockets php56-wddx php56-xmlreader \
php56-xmlwriter php56-zip php56-xsl php56-zlib php56-ctype


cd /usr/local/www/apache24/data
wget https://wordpress.org/latest.tar.gz
tar --strip-components=1 -xzvf latest.tar.gz
rm -rf wordpress index.html
```

Add to the end of /usr/local/etc/apache24/httpd.conf

```
Include etc/apache24/Includes/*.conf
AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps
```

Add `index.php` to `DirectoryIndex` list.

Reload apache:

```
apachectl reload
```
