1. Raid массивы, что такое и какие бывают
>RAID массивы позволяют объеденять несколько дисков в один, для повышения их производительности и т.д. 
>Основные типы RAID-массивов:<br />
>- RAID 0: Объединяет два или более диска для увеличения скорости чтения и записи данных. Не обеспечивает отказоустойчивости, потеря одного диска приводит к утрате всех данных.<br />
>- RAID 1: Создает полную копию данных на двух дисках. Однако эффективная емкость массива составляет только половину от общего объема.<br />
>- RAID 5: Использует три или более дисков. Данные распределяются по всем дискам с использованием четности, что позволяет восстанавливать данные в случае выхода из строя одного диска.<br />
>- RAID 6: Похож на RAID 5, но  позволяет выдерживать выход из строя двух дисков одновременно56.<br />
>- RAID 10: Комбинирует преимущества RAID 0 и RAID 1, обеспечивая как высокую скорость, так и отказоустойчивость. Для его реализации необходимо минимум четыре диска.<br />
2. Добавьте в виртуальную машину 2 диска отформатируйте их в ext4<br />
>![alt text](https://github.com/kryfaertop/Tasks_241/blob/my-report/3-File%20systems_answer/screenshot/16.png?raw=true)<br />
```bash
mkfs.ext4 /dev/sdb2
mkfs.ext4 /dev/sdc1
```
3. Создайте из них raid 0 массив<br />
>![alt text](https://github.com/kryfaertop/Tasks_241/blob/my-report/3-File%20systems_answer/screenshot/17.png?raw=true)<br />
4. Проверье всё ли работает<br />
>![alt text](https://github.com/kryfaertop/Tasks_241/blob/my-report/3-File%20systems_answer/screenshot/18.png?raw=true)<br />
>Всё записалось, значит работает
5. Удалите raid0 и создайте raid1<br />
>![alt text](https://github.com/kryfaertop/Tasks_241/blob/my-report/3-File%20systems_answer/screenshot/19.png?raw=true)<br />
>![alt text](https://github.com/kryfaertop/Tasks_241/blob/my-report/3-File%20systems_answer/screenshot/20.png?raw=true)<br />
6. В чём между ними разница?<br />
>![alt text](https://github.com/kryfaertop/Tasks_241/blob/my-report/3-File%20systems_answer/screenshot/21.png?raw=true)<br />
7. Есть ли файловые системы которые поддерживают raid массивы без стороненго ПО
>Да, есть:<br />
>![alt text](https://github.com/kryfaertop/Tasks_241/blob/my-report/3-File%20systems_answer/screenshot/22.png?raw=true)<br />
8. Можно ли создать raid массив во время установки системы?
>Да, можно
