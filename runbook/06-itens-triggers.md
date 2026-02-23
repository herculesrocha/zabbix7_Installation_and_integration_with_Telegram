# 06 - Itens e Triggers Customizados
## Servidor Up/Down
Trigger:
```php
max(/ZBX-Template-Padrao/zabbix[host,agent,available],{$AGENT.TIMEOUT})=0
or
max(/ZBX-Template-Padrao/agent.ping,3m)=0
or
min(/ZBX-Template-Padrao/proc.num[zabbix_agentd],3m)=0
```
