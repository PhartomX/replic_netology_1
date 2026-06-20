 Домашнее задание к занятию "`Репликация и масштабирование. Часть 1`" - `Алексей Сидоров`
---

### Задание 1.

На лекции рассматривались режимы репликации master-slave, master-master, опишите их различия.

Основным отличием режима репликации master-slave от master-master является то, что в режиме master-slave со вспомогательного сервера(slave) данные только считываются, в то время как в режиме master-master чтение и запись можно производить со всех серверов в этом режиме. 

---

### Задание 2. 

Выполните конфигурацию master-slave репликации, примером можно пользоваться из лекции.

`Файл Docker Compose:`

[master-slave.yml](https://github.com/PhartomX/replic_netology_1/blob/main/master-slave.yml)


`master.cnf`
```
[mysqld]
server-id=1
log-bin = mysql-bin
binlog_format=ROW
```

`slave.cnf`
```
[mysqld]
server-id=2
read_only = 1
```
![img1](https://github.com/PhartomX/replic_netology_1/blob/main/img/img1.png)



---

### Задание 3*

Выполните конфигурацию master-master репликации. Произведите проверку.

![img3](https://github.com/PhartomX/replic_netology_1/blob/main/img/img3.png)