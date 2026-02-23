# 06 - Itens e Triggers Customizados
## Exemplos de Monitoramentos

## Servidor Up/Down
Trigger:
```php
max(/ZBX-Template-Padrao/zabbix[host,agent,available],{$AGENT.TIMEOUT})=0
or
max(/ZBX-Template-Padrao/agent.ping,3m)=0
or
min(/ZBX-Template-Padrao/proc.num[zabbix_agentd],3m)=0
```

## Apache
Trigger:
```php
min(/ZBX-Template-Padrao/apache.status,3m)=0
and max(/ZBX-Template-Padrao/agent.ping,3m)=1
```
## MySQL
Trigger:
```php
min(/ZBX-Template-Padrao/mysql.status,3m)=0
and max(/ZBX-Template-Padrao/agent.ping,3m)=1
```
## FTP
Trigger:
```php
min(/ZBX-Template-Padrao/proftp.status,3m)=0
and max(/ZBX-Template-Padrao/agent.ping,3m)=1
```
## MySQL Replicacao
Trigger:
```php
max(/ZBX-Template-Padrao/agent.ping,3m)=0
or (
  max(/ZBX-Template-Padrao/agent.ping,3m)=1
  and (
    min(/ZBX-Template-Padrao/mysql_replicacao.status,3m)=0
    or max(/ZBX-Template-Padrao/mysql_replicacao_atraso.status,3m)>3000
```
