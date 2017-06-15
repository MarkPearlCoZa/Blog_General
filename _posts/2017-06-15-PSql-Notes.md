---
layout: post
title: PSql Notes
tags: Postgres
category: Tech
---

### Returning a fixed value list

~~~
select * from  
(Values(1, 'one'), (2, 'two'), (3, 'three')) 
as t(num, letter)
~~~

### Filtering counts

~~~
SELECT
	EXTRACT(MONTH FROM payment.payment_date) AS month,
	SUM(amount)::decimal(18,2) AS total_amount,
	COUNT(payment_id) AS total_count,
	COUNT(payment_id) FILTER (WHERE staff_id = 1) AS mike_count,
	SUM(amount) FILTER (where staff_id = 1) AS mike_amount,
 FROM payment
GROUP BY month
ORDER BY month
~~~
