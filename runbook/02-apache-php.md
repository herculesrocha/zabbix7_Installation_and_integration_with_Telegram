# 02 - Configuração Apache + PHP

## Paths do Projeto

```sh
mv /usr/local/www/zabbix7 /usr/local/www/zabbix.dominio.com.br/
mv /usr/local/www/zabbix.dominio.com.br/zabbix7 /usr/local/www/zabbix.dominio.com.br/www
```

## Apache

- Criar o VirtualHost do Zabbix 7
```bash
mv /usr/local/etc/apache24/extra/httpd-vhosts.conf /usr/local/etc/apache24/extra/httpd-vhosts.conf.old
vi /usr/local/etc/apache24/extra/httpd-vhosts.conf
```
```php
<VirtualHost *:80>
    ServerName zabbix.dominio.com.br
    Redirect permanent / https://zabbix.dominio.com.br/
    DocumentRoot "/usr/local/www/zabbix.dominio.com.br/www"

    <Directory "/usr/local/www/zabbix.dominio.com.br/www">
        AllowOverride All
        Require all granted
        Options FollowSymLinks
    </Directory>

    <FilesMatch "\.php$">
       	#SetHandler "proxy:unix:/var/run/php-fpm.sock|fcgi://localhost/"
	SetHandler "proxy:unix:/tmp/php-fpm.sock|fcgi://127.0.0.1:9000"
    </FilesMatch>

    ErrorLog "/var/log/zabbix_error.log"
    CustomLog "/var/log/zabbix_access.log" combined
</VirtualHost>

<VirtualHost *:443>
    ServerName zabbix.dominio.com.br
    DocumentRoot "/usr/local/www/zabbix.dominio.com.br/www"

    SSLEngine on
    SSLCertificateFile /usr/local/etc/letsencrypt/live/zabbix.dominio.com.br/cert.pem
    SSLCertificateKeyFile /usr/local/etc/letsencrypt/live/zabbix.dominio.com.br/privkey.pem
    SSLCertificateChainFile /usr/local/etc/letsencrypt/live/zabbix.dominio.com.br/fullchain.pem
    SSLCertificateChainFile /usr/local/etc/letsencrypt/live/zabbix.dominio.com.br/chain.pem

    <Directory "/usr/local/www/zabbix.dominio.com.br/www">
        AllowOverride All
        Require all granted
        Options FollowSymLinks
    </Directory>

    <FilesMatch "\.php$">
        SetHandler "proxy:unix:/tmp/php-fpm.sock|fcgi://127.0.0.1:9000"
    </FilesMatch>

    ErrorLog "/var/log/zabbix_ssl_error.log"
    CustomLog "/var/log/zabbix_ssl_access.log" combined
</VirtualHost>
```

- Ajustar Permissões

chown -R www:www /usr/local/www/ && chmod -R 755 /usr/local/www/

- Ajustar variáveis do PHP
