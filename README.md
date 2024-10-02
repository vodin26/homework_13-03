### Задание 1

Скриншот-1 к заданию 1:

![Скриншот-1](img/pic_1.png)

Скриншот-2 к заданию 1:

![1727853570591](images/README/1727853570591.png)

Скриншот-3 к заданию 1:

![1727853598099](images/README/1727853598099.png)

```
CREATE USER 'sys_temp'@'localhost' IDENTIFIED BY '12345'; 
SELECT * FROM mysql.user;
GRANT ALL PRIVILEGES ON *.* TO 'sys_temp'@'localhost' WITH GRANT OPTION;
SHOW GRANTS FOR 'sys_temp'@'localhost';
ALTER USER 'sys_temp'@'localhost' IDENTIFIED WITH mysql_native_password BY '12345'; 
```

### Задание 2
