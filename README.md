# Домашнее задание к занятию "`Система мониторинга Zabbix`" - `Сулименков Алексей`

---

### Задание 1

####  Установите Zabbix Server с веб-интерфейсом.

Прикрепите в файл README.md скриншот авторизации в админке.
![Авторизация](https://github.com/biparasite/10-01HW/blob/main/zabbix_login.png)

Приложите в файл README.md текст использованных команд в GitHub.

```
 wget https://repo.zabbix.com/zabbix/6.0/debian-arm64/pool/main/z/zabbix-release/zabbix-release_latest+debian12_all.deb
 dpkg -i zabbix-release_latest+debian12_all.deb
 apt update
 apt install zabbix-server-pgsql zabbix-frontend-php php8.2-pgsql zabbix-apache-conf zabbix-sql-scripts
 sudo -u postgres createuser --pwprompt zabbix
 sudo -u postgres createdb -O zabbix zabbix
 zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix
 sed -i -e 's/\#\ DBPassword=/DBPassword=test/' /etc/zabbix/zabbix_server.conf 
 systemctl restart zabbix-server zabbix-agent apache2
 systemctl enable zabbix-server zabbix-agent apache2
```
---

### Задание 2

####

---
