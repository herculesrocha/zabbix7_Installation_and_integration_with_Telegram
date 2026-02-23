# 04 - Configuração do Zabbix Server

## rc.conf

```sh
vi /etc/rc.conf
zabbix_server_enable="YES"
```
```sh
vi /usr/local/etc/zabbix7/zabbix_server.conf
DBPassword=Senha_ZBX
```

```sh
/usr/local/etc/rc.d/zabbix_server restart
/usr/local/etc/rc.d/zabbix_server status

/usr/local/etc/rc.d/zabbix_agentd restart
/usr/local/etc/rc.d/zabbix_agentd status

service php_fpm restart && service apache24 restart
```
