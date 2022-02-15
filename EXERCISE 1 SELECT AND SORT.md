# EXERCISE FOR SELECT AND SORT

**QUESTION 1**
---
What is the name of the category with the highest category_id in the dvd_rentals.category table?
---
`select
  name, category,
  category_id
from
  dvd_rentals.category
order by
  category_id desc
limit
  1;`
  
 **QUESTION 2**
 ---
 For the films with the longest length, what is the title of the “R” rated film with the lowest 
 replacement_cost in dvd_rentals.film table?
 ---
 `select
  length,
  title,
  replacement_cost, rating
from
  dvd_rentals.film
order by length desc, replacement_cost;`

**QUESTION 3**
---
Who was the manager of the store with the highest total_sales in the dvd_rentals.sales_by_store table?
---	
`select
  manager,
  total_sales
from
  dvd_rentals.sales_by_store
order by
  total_sales desc;`
  
**QUESTION 4**
---
What is the postal_code of the city with the 5th highest city_id in the dvd_rentals.address table?
---
select
  postal_code,
  city_id
from
  dvd_rentals.address
order by
  city_id desc
limit
  5;