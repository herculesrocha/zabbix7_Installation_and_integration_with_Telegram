# 05 - Configuração do Agente e UserParameters

Alguns exemplos para adicionar no agente:

```php
##ZBX - Status - Apache
UserParameter=apache.status,/bin/sh -c 'pgrep -x httpd | wc -l'

##ZBX - Status - FTP
UserParameter=proftp.status,sockstat -4l | grep proftpd | wc -l

##ZBX - Status - Radius
UserParameter=freeradius.status,sockstat -4l | grep radiusd | wc -l

##ZBX - Status - MySQL
UserParameter=mysql.status,pgrep -x mariadbd | wc -l

##ZBX - Status - MySQL Replicacao
UserParameter=UserParameter=mysql_replicacao.status,/bin/sh -c '/usr/local/bin/mysql -uzabbix -pSenha_ZBX -N -s -e "SHOW SLAVE STATUS\G" 2>/dev/null | /usr/bin/awk -F": " "tolower(\$1)==\"slave_io_running\"{io=(toupper(\$2)==\"YES\"||toupper(\$2)==\"ON\")} tolower(\$1)==\"slave_sql_running\"{sql=(toupper(\$2)==\"YES\"||toupper(\$2)==\"ON\")} END{print (io&&sql)?1:0}"'

##ZBX - Status - MySQL Replicacao Atraso
UserParameter=mysql_replicacao_atraso.status,/bin/sh -c '/usr/local/bin/mysql -uroot -psiemens -N -s -e "SHOW SLAVE STATUS\G" 2>/dev/null | /usr/bin/awk -F": " "tolower(\$1)==\"seconds_behind_master\"{print (\$2==\"NULL\"||\$2==\"\"?999999:\$2); found=1} END{if(!found) print 999999}"'

##ZBX - Status - Rsync
UserParameter=rsync.status,find /usr/local/www/intranet.dominio.com.br/logs -type f -mmin -60 | xargs tail -1 | grep total | wc -l

##Status - Dominio (https://intranet.dominio.com.br)
UserParameter=dominio.status,/usr/local/bin/php /usr/local/www/intranet.dominio.com.br/www/scripts/zabbix/statusDominio.php
```
