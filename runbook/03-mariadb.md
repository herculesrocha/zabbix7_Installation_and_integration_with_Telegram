# 03 - Configuração MariaDB

## Reset Estrutural

```sh
mv /usr/local/etc/my.cnf /usr/local/etc/my.cnf.old
mv /usr/local/etc/mysql/my.cnf /usr/local/etc/mysql/my.cnf.old
mv /var/db/mysql/ /var/db/mysql.old
```
```sh
/usr/local/etc/rc.d/mysql-server restart
/usr/local/etc/rc.d/mysql-server status
```
## Utilizar arquivo mysql-mariadb.my.cnf
```sh
vi /usr/local/etc/mysql/my.cnf
```
## Utilizar arquivo mysql-mariadb.create_bds.sql
```sh
mysql -p
```
```sql
CREATE DATABASE zabbix
  CHARACTER SET utf8mb4
  COLLATE utf8mb4_bin;

GRANT ALL PRIVILEGES ON zabbix.* TO 'zabbix'@'localhost';
FLUSH PRIVILEGES;
EXIT;

CREATE USER `zabbix`@`%`;
FLUSH PRIVILEGES;
SHOW GRANTS FOR `zabbix`@`%`;
GRANT ALTER,ALTER ROUTINE,CREATE,CREATE ROUTINE,CREATE TEMPORARY TABLES,CREATE USER,CREATE VIEW,DELETE,DROP,EVENT,EXECUTE,GRANT OPTION,INDEX,INSERT,LOCK TABLES,PROCESS,REFERENCES,RELOAD,REPLICATION CLIENT,REPLICATION SLAVE,SELECT,SHOW DATABASES,SHOW VIEW,SHUTDOWN,SUPER,TRIGGER,UPDATE ON *.* TO `zabbix`@`%` WITH GRANT OPTION;
FLUSH PRIVILEGES;
SHOW GRANTS FOR `zabbix`@`%`;
SET PASSWORD FOR `zabbix`@`%`=PASSWORD('Senha_ZBX');
FLUSH PRIVILEGES;

FLUSH PRIVILEGES;
SHOW GRANTS FOR `zabbix`@`localhost`;
GRANT ALTER,ALTER ROUTINE,CREATE,CREATE ROUTINE,CREATE TEMPORARY TABLES,CREATE USER,CREATE VIEW,DELETE,DROP,EVENT,EXECUTE,GRANT OPTION,INDEX,INSERT,LOCK TABLES,PROCESS,REFERENCES,RELOAD,REPLICATION CLIENT,REPLICATION SLAVE,SELECT,SHOW DATABASES,SHOW VIEW,SHUTDOWN,SUPER,TRIGGER,UPDATE ON *.* TO `zabbix`@`localhost` WITH GRANT OPTION;
FLUSH PRIVILEGES;
SHOW GRANTS FOR `zabbix`@`localhost`;
SET PASSWORD FOR `zabbix`@`localhost`=PASSWORD('Senha_ZBX');
FLUSH PRIVILEGES;
```
```sh
/usr/local/etc/rc.d/mysql-server restart
/usr/local/etc/rc.d/mysql-server status
```

```sh
mysql -uzabbix -pSenha_ZBX zabbix < /usr/local/share/zabbix7/server/database/mysql/schema.sql
mysql -uzabbix -pSenha_ZBX zabbix < /usr/local/share/zabbix7/server/database/mysql/images.sql
mysql -uzabbix -pSenha_ZBX zabbix < /usr/local/share/zabbix7/server/database/mysql/data.sql
```

### Realizar configuração do banco de dados no Dashboard do Zabbix 7
