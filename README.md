# Домашнее задание к занятию "`Система мониторинга Zabbix`" - `Сулименков Алексей`

---

### Задание 1

####  Установите Zabbix Server с веб-интерфейсом.

1. Прикрепите в файл README.md скриншот авторизации в админке.
![Авторизация](https://github.com/biparasite/10-01HW/blob/main/zabbix_login.png)

2. Приложите в файл README.md текст использованных команд в GitHub.

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

#### Установите Zabbix Agent на два хоста.

1. Приложите в файл README.md скриншот раздела Configuration > Hosts, где видно, что агенты подключены к серверу
![ZBZ_A](https://github.com/biparasite/10-01HW/blob/main/10-1HW.02.png)


2. Приложите в файл README.md скриншот лога zabbix agent, где видно, что он работает с сервером
![ZBZ_Ag](https://github.com/biparasite/10-01HW/blob/main/10-1HW.02.1.png)

3. Приложите в файл README.md скриншот раздела Monitoring > Latest data для обоих хостов, где видны поступающие от агентов данные.

![ZBZ_Age](https://github.com/biparasite/10-01HW/blob/main/10-1HW.02.2.png)


4. Приложите в файл README.md текст использованных команд в GitHub

```
 wget https://repo.zabbix.com/zabbix/6.0/debian-arm64/pool/main/z/zabbix-release/zabbix-release_latest+debian12_all.deb
 dpkg -i zabbix-release_latest+debian12_all.deb
 apt update
 apt install zabbix-agent -y
 sed -i 's/Server=127.0.0.1/Server=192.168.200.105'/g' /etc/zabbix/zabbix_agentd.conf
 systemctl restart zabbix-agent
 systemctl enable zabbix-agent
```
---
