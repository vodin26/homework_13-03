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
WITH PaymentMonthly AS (
    SELECT 
        DATE_FORMAT(rental_date, '%Y-%m') as payment_month, 
        SUM(amount) as total_payment 
    FROM rental r
    JOIN payment p ON r.rental_id = p.rental_id
    GROUP BY payment_month
),
RankedPayments AS (
    SELECT 
        payment_month,
        total_payment,
        ROW_NUMBER() OVER (ORDER BY total_payment DESC) as rn
    FROM PaymentMonthly 
)
SELECT 
    payment_month,
    total_payment,
    COUNT(DISTINCT r.rental_id) AS number_of_rentals
FROM RankedPayments rp
JOIN rental r ON rp.payment_month = DATE_FORMAT(r.return_date, '%Y-%m')
WHERE rp.rn = 1 
GROUP BY payment_month;
```
