1. Удалите iptables и установите firewalld
> Удалим iptables и установим\запустим firewalid
```sh
sudo apt-get remove iptables
sudo apt-get install firewalld
sudo systemctl enable firewalld.service
sudo systemctl start firewalld.service
```
2. Попробуйте так-же проверить возможность подключения по ssh
> Возможность осталась, по той же причине, что и в первом таске
3. Если её нет то откройте порт
```sh
sudo firewall-cmd --zone=public --add-port=22/tcp --permanent
sudo firewall-cmd --reload
```
4. Выведите список открытых портов с помощью firewall-cmd
```sh
sudo firewall-cmd --list-ports<br />
```
![alt text](https://github.com/kryfaertop/Tasks_241/blob/my-report/9-Firewall/2.png?raw=true)<br />
5. Можно ли там добавить порты по названию сервиса?
>Да, в firewalld можно добавлять порты по названию сервиса. Например, чтобы разрешить доступ к SSH
```sh
sudo firewall-cmd --zone=public --add-service=ssh --permanent
```
6. На вашей Локальной виртуальной машине попробуйте подключиться к серверу samba из предыдущих заданий
> Получилось<br />
![alt text](https://github.com/kryfaertop/Tasks_241/blob/my-report/9-Firewall/2.png?raw=true)<br />
7. Если не получилось то откройте нужные порты
```sh
firewall-cmd --add-port=200/tcp --permanent
```
9. Сделайте так чтобы изменения были постоянными
> Всё сохранится, у чего есть флаг --permanent, если перезагруить
```sh
systemctl restart firewalld
```
