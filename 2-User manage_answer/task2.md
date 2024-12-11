1. Запретите пользователю user1 из предыдщуего задания выполнять вход в систему
>![alt text](https://github.com/kryfaertop/Tasks_241/blob/my-report/2-User%20manage_answer/screenshot/9.png?raw=true)<br />
>
2. Как вы это сделали?
>![alt text](https://github.com/kryfaertop/Tasks_241/blob/my-report/2-User%20manage_answer/screenshot/10.png?raw=true)<br />
>
3. Какие ещё способы это сделать вы знаете?
> 1) Изменение оболочки пользователя
>sudo chsh -s /usr/sbin/nologin user1
> 2) Изменение файла /etc/passwd
>sudo nano /etc/passwd
>Найдите строку, начинающуюся с user1, и измените последнюю часть (оболочку) на /usr/sbin/nologin. Например:
>user1:x:1001:1001::/home/user1:/usr/sbin/nologin
> 3) Удаление пароля пользователя
>Удаление пароля пользователя также предотвратит вход, так как пользователь не сможет аутентифицироваться.
>sudo passwd -l user1
>
4. Можно ли создать пользователей с одинаковыми username?
>Имена пользователей и их идентификаторы (UID) должны быть уникальными в пределах системы для упрощения управления пользователями и их правами.
