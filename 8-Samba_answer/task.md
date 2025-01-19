1. Установите пакет samba
```bash
apt-get install samba
apt-get install samba samba-client
```
2. ЧТо такое побщая папка, зачем оно может быть нужно?
>Общая папка — это специальная папка, которая предоставляет пользователям возможность совместного доступа к файлам и данным. Например, они могут быть использованы в различных операционных системах и приложениях, включая Windows, Linux
3. Создайте общую папку без пароля с правами только на чтение файлов
>Создадим папку и настроим ей доступ:
```bash
mkdir -p /srv/samba/public
chmod 777 /srv/samba/public
```
>В данном конфиге:
```bash
sudo nano /etc/samba/smb.conf
```
>![alt text](https://github.com/kryfaertop/Tasks_241/blob/my-report/8-Samba_answer/screenshots/5.png?raw=true)<br />
>![alt text](https://github.com/kryfaertop/Tasks_241/blob/my-report/8-Samba_answer/screenshots/1.png?raw=true)<br />
4. Создайте общую папку с паролем с правами на чтение и запись
>Создадим папку и настроим ей доступ:
```bash
mkdir -p /srv/samba/secured
chmod 770 /srv/samba/secured
```
>Настроим нового пользователя:
```bash
useradd smbuser
smbpasswd -a 1234
chown  smbuser:smbuser /srv/samba/secured
```
>В данном конфиге:
```bash
sudo nano /etc/samba/smb.conf
```
>![alt text](https://github.com/kryfaertop/Tasks_241/blob/my-report/8-Samba_answer/screenshots/6.png?raw=true)<br />
>![alt text](https://github.com/kryfaertop/Tasks_241/blob/my-report/8-Samba_answer/screenshots/2.png?raw=true)<br />
5. Создайте общую папку с доступом для какой-то группы с полными правами
>Создадим папку и настроим ей доступ:
```bash
mkdir -p /srv/samba/group
groupadd smbgroup
chown :smbgroup /srv/samba/group
chmod 770 /srv/samba/group
```
>В данном конфиге:
```bash
sudo nano /etc/samba/smb.conf
```
>![alt text](https://github.com/kryfaertop/Tasks_241/blob/my-report/8-Samba_answer/screenshots/7.png?raw=true)<br />
>![alt text](https://github.com/kryfaertop/Tasks_241/blob/my-report/8-Samba_answer/screenshots/3.png?raw=true)<br />
>По аналогии с добавлением в группу суперпользователя:
```bash
usermod -aG smbgroup smbuser
```
6. Создайте общую папку в которой у одной группы будет полный доступ, а у другой только доступ на чтение.
Третья группа не должна иметь к ней доступа
>Создадим папку и настроим ей доступ:
```bash
groupadd read_access
mkdir -p /srv/samba/mixed
chmod 770 /srv/samba/group
chown root:smbgroup /srv/samba/group
```
>В данном конфиге:
```bash
sudo nano /etc/samba/smb.conf
```
>![alt text](https://github.com/kryfaertop/Tasks_241/blob/my-report/8-Samba_answer/screenshots/8.png?raw=true)<br />
>![alt text](https://github.com/kryfaertop/Tasks_241/blob/my-report/8-Samba_answer/screenshots/4.png?raw=true)<br />
> Добавляем нескольких пользователей и добавляем их в группы с разными правами доступа:
```bash
useradd -m user1
useradd -m user2
usermod -aG smbgroup user1
usermod -aG read_access user2
smbpasswd -a user1
smbpasswd -a user2
```
>если ошибок нет - всё работает
