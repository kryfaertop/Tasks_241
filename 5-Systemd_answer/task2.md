1. Создайте скрипт который создаёт папку заполняет её файлами ( имена 1-4 ) и записывает в них информацию
о текущей дате, версии ядра, имени компьютера и списе всех файлов в домашнем каталоге пользователя от которого выполняется скрипт( не забудьте сдлеать проверку на существование файлов и папок)
```bash
#!/bin/bash
folder="my_folder"
if [ ! -d "$HOME/$folder" ]; then
mkdir "$HOME/$folder"
echo "Папка '$folder' создана."
else
echo "Папка '$folder_name' уже существует."
fi
for i in {1..4}; do
file_name="$HOME/$folder_name/file$i.txt"
if [ ! -f "$file_name" ]; then
{
echo "Дата: $(date)"
echo "Версия ядра: $(uname -r)"
echo "Имя компьютера: $(hostname)"
echo "Список файлов в домашнем каталоге:"
ls "$HOME"
} > "$file_name"
echo "Файл '$file_name' создан и заполнен."
else
echo "Файл '$file_name' уже существует."
fi
done

```
2. Создайте юнит который будет вызывать этот скрипт при запуске. Проверьте
```bash
[Unit]
Description=test
After=network.target

[Service]
Type=oneshot
ExecStart=/path/to/your/script.sh
RemainAfterExit=yes

[Install]
WantedBy=multi-user.target
```
3. Создайте таймер который будет вызывать выполнение одноимённого systemd юнита каждые 5 минут.
```bash
[Unit]
Description=Таймер для выполнения скрипта каждые 5 минут
Requires=myunit.service

[Timer]
Unit=myunit.service
OnUnitActiveSec=5m

[Install]
WantedBy=timers.target
```
4. От какого пользователя вызыаются юниты поумолчанию?
>Юниты в systemd по умолчанию вызываются от имени пользователя, который вошёл в систему. При первом входе пользователя запускается процесс systemd --user, который управляет пользовательскими службами и задачами. 
5. Создайте пользователя от имени которого будет выполняться ваш скрипт.
```bash
sudo adduser myuser
```
6. Дополните юнит информацией о пользователе от которого должен выплняться скрипт.
```bash
sudo nano /etc/systemd/system/my_script.service
```
7. Дополните ваш скрипт так, что бы он независимо от местоположения всега выполнялся в домашней папке того кто его вызывает.
>   Дополнил
