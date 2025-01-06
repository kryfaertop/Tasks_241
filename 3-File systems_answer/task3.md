1. Выведите содержимое fstab. Что хранится в fstab?
>Файл /etc/fstab используется для автоматического монтирования файловых систем при загрузке системы. Он содержит информацию о доступных файловых системах и их параметрах монтирования<br />
>![alt text](https://github.com/kryfaertop/Tasks_241/blob/my-report/3-File%20systems_answer/screenshot/5.png?raw=true)<br />
2. Добавьте в виртуальную машину ещё один диск<br />
>![alt text](https://github.com/kryfaertop/Tasks_241/blob/my-report/3-File%20systems_answer/screenshot/6.png?raw=true)<br />
3. Узнайте как ситема видит ваш диск - выведите информацию о блочных устройствах<br />
>![alt text](https://github.com/kryfaertop/Tasks_241/blob/my-report/3-File%20systems_answer/screenshot/7.png?raw=true)<br />
4. С помощью полученной информации создайте на диске таблицу разделов и фаловую систему ext4
>sudo fdisk /dev/sdb
>Затем используйте команды n для создания нового раздела, следуйте инструкциям для создания окончательного раздела.<br /> 
>![alt text](https://github.com/kryfaertop/Tasks_241/blob/my-report/3-File%20systems_answer/screenshot/8.png?raw=true)<br />
>sudo mkfs.ext4 /dev/sdb<br />
>![alt text](https://github.com/kryfaertop/Tasks_241/blob/my-report/3-File%20systems_answer/screenshot/9.png?raw=true)<br />
5. Примонитруте диск в каталог /mnt
>sudo mount /dev/sdb1 /mnt
6. Зайдите в каталог и создайте там файлы<br />
>![alt text](https://github.com/kryfaertop/Tasks_241/blob/my-report/3-File%20systems_answer/screenshot/10.png?raw=true)<br />
7. Отмонтируйте диск и проверье остались ли файлы<br />
>![alt text](https://github.com/kryfaertop/Tasks_241/blob/my-report/3-File%20systems_answer/screenshot/11.png?raw=true)<br />
8. Сделайте так чтобы диск автоматически подключался при загрузке систем ( добавьте информацию о нём с fstab)
>Нам нужно получить UUID диска: blkid /dev/sdb2<br />
>Тепереь запише в файл: UUID=[uuid] /mnt ext4 defaults 0 2
9. Проверьте корретность записанных в fstab данных перед перезагрузкой<br />
> можно проверить командой: mount -a<br />
>если не появляется ошибка - всё хорошо
10. Перезагрущите систему и убедитесь что диск был подключён к системе
> reboot now
>
