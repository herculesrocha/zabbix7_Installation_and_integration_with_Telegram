# 01 - Instalação Base do Sistema

## Atualização do Sistema

```bash
pkg update -f
pkg upgrade -f
```
### Remoção de Pacotes Antigos

Remover versões antigas do MariaDB e Zabbix antes da nova instalação.

### Instalação de Dependências
```bash
pkg install -y php82-curl
```
### Compilação do Zabbix 7 via Ports
```bash
cd /usr/ports/net-mgmt/zabbix7-server/
make config
```
Marcar:

MDB6 - MariaDB 10.6 support
```bash
make BATCH=yes DISABLE_VULNERABILITIES=yes ALLOW_UNSUPPORTED_SYSTEM=yes FORCE_PKG_REGISTER=yes MAKE_JOBS_UNSAFE=yes install clean
```
Instalação do MariaDB 10.6
```bash
cd /usr/ports/databases/mariadb106-server/
make BATCH=yes DISABLE_VULNERABILITIES=yes ALLOW_UNSUPPORTED_SYSTEM=yes FORCE_PKG_REGISTER=yes MAKE_JOBS_UNSAFE=yes install clean

