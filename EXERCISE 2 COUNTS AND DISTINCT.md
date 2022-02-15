# EXERCISE 2 COUNT AND DISTINCT


**QUESTION 1**
---
Which actor_id has the most number of unique film_id records in the dvd_rentals.film_list table?
---
`select actor_id, count(DISTINCT film_id) from dvd_rentals.film_actor group by 1 order by 2 desc limit 5`

**QUESTION 2**
---
How many distinct fid values are there for the 3rd most common price value in the dvd_rentals.nicer_but_slower_film_list table?
---
`select count(distinct fid), price from dvd_rentals.nicer_but_slower_film_list group by 2 order by 1 desc limit 3`

**QUESTION 3**
---
How many unique country_id values exist in the dvd_rentals.city table?
---

`select count(distinct country_id) from dvd_rentals.city`

**QUESTION 4**
---
What percentage of overall total_sales does the Sports category make up in the dvd_rentals.sales_by_film_category table?
---

`select category, ROUND(100*total_sales::NUMERIC / sum(total_sales) OVER(), 2) as percentage from dvd_rentals.sales_by_film_category`

**QUESTION 5**
---
What percentage of unique fid values are in the Children category in the dvd_rentals.film_list table?
---

`select category, ROUND(100*count(distinct fid)::NUMERIC / sum(count(distinct fid)) over(), 2) as percentage from dvd_rentals.film_list group by category order by category`
