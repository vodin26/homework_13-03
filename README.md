## Домашнее задание к занятию «SQL. Часть 2» "Воронин Владислав"


### Задание 1

```mysql
SELECT s.last_name AS staff_last_name, s.first_name AS staff_first_name, ci.City, COUNT(c.customer_id) AS customer_count 
FROM staff s
JOIN store st ON s.staff_id = st.manager_staff_id
JOIN address a ON st.store_id = a.address_id
JOIN city ci ON a.city_id = ci.city_id
JOIN customer c ON st.store_id = c.store_id  
GROUP BY s.last_name, s.first_name, ci.City 
HAVING COUNT(c.customer_id) > 300;
```

### Задание 2

```mysql
SELECT COUNT(*) AS films_longer_than_average 
FROM film 
WHERE length > (SELECT AVG(length) FROM film);
```

### Задание 3

```mysql

```
