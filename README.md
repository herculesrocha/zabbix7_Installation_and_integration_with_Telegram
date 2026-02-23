# Runbook Técnico – Zabbix 7 Server no FreeBSD

## 📌 Visão Geral

Este repositório contém um runbook completo, utilizado em um ambiente real, para implantação do Zabbix 7 Server em ambiente FreeBSD, utilizando:

- Apache 2.4
- PHP 8.2 (php-fpm)
- MariaDB 10.6
- SSL via Let's Encrypt
- Integração com Telegram
- Itens e Triggers customizados
- UserParameters avançados

O objetivo é padronizar a implantação, garantir rastreabilidade operacional e demonstrar boas práticas de monitoramento corporativo.

---

## 🖥️ Ambiente

- Sistema Operacional: FreeBSD
- Plataforma de Monitoramento: Zabbix 7
- Banco de Dados: MariaDB 10.6
- Web Server: Apache 2.4
- PHP: 8.2
- Integração: Telegram Bot API

---


# 📚 Menu de Acesso Rápido ao Runbook

## 🔹 1. Instalação Base do Sistema
Preparação do FreeBSD, atualização do sistema, compilação via ports e instalação do Zabbix Server e MariaDB.

➡️ [01 - Instalação Base](runbook/01-instalacao-base.md)

---

## 🔹 2. Configuração Apache + PHP
Estrutura de diretórios, VirtualHost HTTP/HTTPS, permissões, ajustes de PHP e validação de serviços.

➡️ [02 - Apache e PHP](runbook/02-apache-php.md)

---

## 🔹 3. Configuração do MariaDB
Reset estrutural, criação do banco, grants detalhados, importação de schema e validação de logs.

➡️ [03 - MariaDB](runbook/03-mariadb.md)

---

## 🔹 4. Configuração do Zabbix Server
Ativação no rc.conf, ajustes no zabbix_server.conf, restart e validação operacional.

➡️ [04 - Zabbix Server](runbook/04-zabbix-server.md)

---

## 🔹 5. Agente e UserParameters Customizados
Configuração avançada do agente com monitoramento de:

- Apache
- MySQL
- FTP
- Radius
- Replicação
- Rotinas rsync
- Validação de domínio

➡️ [05 - Agente e UserParameters](runbook/05-agente-userparameters.md)

---

## 🔹 6. Itens e Triggers Customizados
Definição técnica de expressões para:

- Status do servidor
- Monitoramento de serviços
- Replicação MySQL
- Controle de severidade
- Lógica antifalso-positivo

➡️ [06 - Itens e Triggers](runbook/06-itens-triggers.md)

---

## 🔹 7. Integração com Telegram
Criação de bot, obtenção de token, configuração de mídia no Zabbix, ações de alerta e templates HTML de notificação.

➡️ [07 - Integração Telegram](runbook/07-telegram.md)

---

## 🔹 8. Validação, Logs e Hardening
Procedimentos de validação final, auditoria de logs e boas práticas de segurança.

➡️ [08 - Validação e Hardening](runbook/08-validacao-e-hardening.md)

---

# 🧠 Escopo Técnico da Arquitetura

Este runbook cobre:

- Compilação via ports no FreeBSD
- Estruturação de ambiente web seguro com SSL
- Banco de dados com privilégios granulares
- Monitoramento de processos críticos
- Validação de replicação
- Alertas baseados em severidade
- Integração com mensageria externa
- Governança operacional documentada
---

## 📄 Licença

Distribuído sob licença MIT.



TESTE

# 📚 Menu de Acesso Rápido ao Runbook

## 🔹 1. Instalação Base do Sistema
➡️ [01 - Instalação Base](runbook/01-instalacao-base.md)
## 🔹 2. Configuração Apache + PHP
➡️ [02 - Apache e PHP](runbook/02-apache-php.md)
## 🔹 3. Configuração do MariaDB
➡️ [03 - MariaDB](runbook/03-mariadb.md)
## 🔹 4. Configuração do Zabbix Server
➡️ [04 - Zabbix Server](runbook/04-zabbix-server.md)
## 🔹 5. Agente e UserParameters Customizados
➡️ [05 - Agente e UserParameters](runbook/05-agente-userparameters.md)
## 🔹 6. Itens e Triggers Customizados
➡️ [06 - Itens e Triggers](runbook/06-itens-triggers.md)
## 🔹 7. Integração com Telegram
➡️ [07 - Integração Telegram](runbook/07-telegram.md)
## 🔹 8. Validação, Logs e Hardening
➡️ [08 - Validação e Hardening](runbook/08-validacao-e-hardening.md)
