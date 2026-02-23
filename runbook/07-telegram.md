# 07 - Integração com Telegram

## Criar Bot

### Criar bot e obter o token
- Token
### Criar grupo para receber notificações e obter o id
- ID do Grupo

---

## Configuração no Zabbix

Alertas > Tipos de mídia > Telegram

Parâmetros:
```php
alert_message = {ALERT.MESSAGE}
alert_subject = {ALERT.SUBJECT}
api_chat_id = -ID_Grupo
api_token = Token
```
---
## Habilitar mídia no usuário responsável pelas notificações:
Usuários > Usuários
Configuração: 
Tipo: Telegram
Enviar para: -ID_Grupo
Quando ativo: 1-7,00:00-24:00
Severidade: Alta, Desastre

## Criar Ação

Severidade >= Alta

Operação:
Enviar para usuário configurado
Tipo de mídia: Telegram

---

## Modelos de Mensagem

Mensagem de Incidente e Recuperação conforme estrutura HTML definida.
