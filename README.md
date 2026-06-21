 Домашнее задание к занятию "`Репликация и масштабирование. Часть 1`" - `Алексей Сидоров`
---

### Задание 1.

На лекции рассматривались режимы репликации master-slave, master-master, опишите их различия.

Основным отличием режима репликации master-slave от master-master является то, что в режиме master-slave со вспомогательного сервера(slave) данные только считываются, в то время как в режиме master-master чтение и запись можно производить со всех серверов в этом режиме. 

---

### Задание 2. 

Выполните конфигурацию master-slave репликации, примером можно пользоваться из лекции.

`Создал два контейнера с mysql через Docker Compose:`

[master-slave.yml](https://github.com/PhartomX/replic_netology_1/blob/main/master-slave.yml)


`Файлы конфигурации:`

master.cnf
```
[mysqld]
server-id=1
log-bin = mysql-bin
binlog_format=ROW
```

slave.cnf
```
[mysqld]
server-id=2
read_only = 1
```

![img2](https://github.com/PhartomX/replic_netology_1/blob/main/img/img2.png)

![img3](https://github.com/PhartomX/replic_netology_1/blob/main/img/img3.png)

`Статус реплики:`

![img1](https://github.com/PhartomX/replic_netology_1/blob/main/img/img1.png)



---

### Задание 3*

Выполните конфигурацию master-master репликации. Произведите проверку.

`Создал два контейнера с mysql через Docker Compose:`

[master-master.yml](https://github.com/PhartomX/replic_netology_1/blob/main/master-master.yml)

`Файлы конфигурации:`

master1.cnf
```
[mysqld]
server-id=1
log-bin = mysql-bin
binlog_format=ROW
```

master2.cnf
```
[mysqld]
server-id=2
binlog_format=ROW
log-bin = mysql-bin
```

![img4](https://github.com/PhartomX/replic_netology_1/blob/main/img/img4.png)

![img5](https://github.com/PhartomX/replic_netology_1/blob/main/img/img5.png)


`Статус реплики:`

![img6](https://github.com/PhartomX/replic_netology_1/blob/main/img/img6.png)

![img7](https://github.com/PhartomX/replic_netology_1/blob/main/img/img7.png)

`Результат проверки – при в несении изменений на любом из серверов, данные изменяются на другом:` 

![img8](https://github.com/PhartomX/replic_netology_1/blob/main/img/img8.png)
