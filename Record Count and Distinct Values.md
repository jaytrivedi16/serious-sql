# RECORD COUNT AND DISTINCT VALUES

## RECORD COUNT

We can use count(`*`), count(1), count(col_name) to count the number of rows in the table. 
If we want to see how many rows are there in film_list table we can write it as:

`select count(*) as row_count from dvd_rentals.film_list;`

## DISTINCT

Whenever there is duplicates in dataset we can use distinct to give us the distinct values without 
the duplicates.

`select distinct ratings from dvd_rentals.film_list;`

Similarly, if we want to count the number of distinct values in the table our query would be:
`select count(distinct category) as unique_category from dvd_rentals.film_list;`

## GROUP BY COUNT

To find how many counts or frequency of the ratings or group by the result using count:

`select rating, count(*) as frequency from dvd_rentals.film_list group by rating;`

Rating is in both select and group by statements as any of the column which is in select and 
is not an aggregate needs to be in group by clause. It has to be group by and then order by and 
then limit

In some SQL implementations, count(1) would be slower than count(`*`) because it needs to check
implicitly if the count(1) is null or not.

## TO CHECK FOR PERCENTAGE

When we are doing count we will use percentage to show real time calcultations

`select
  `rating,
  `count(*) as frequency,`
  `count(*) :: NUMERIC / SUM(COUNT(*)) OVER () AS percent`  
`from dvd_rentals.film_list
`group by rating
`order by frequency desc;`

`count(*) :: NUMERIC / SUM(COUNT(*)) OVER () AS percent` is a window function. sum(count(`*`) over()
is looking for total count of records. Casting of numeric is very important and is used to do
integer-float division. This is required as if both are integer when dividing, it will give
the lower ceiling of the number thus discarding the value after decimal. Numeric is a data type and
used to return the decimal data type.

Theory:
1. Integer Float Division
2. Window Function

## MULTIPLE COLUMN GROUP BY

We want to group by using two columns:

`select rating, count(*) as frequency, category from dvd_rentals.film_list group by rating, category
`order by frequency desc limit 5;

whatever order of columns you are using in select use the same in group by to keep it readable and
simple.

## GROUP BY ORDINAL SYNTAX
 `select rating, category, count(*) as frequency from dvd_rental.film_list order by 1,2;`
 
 Ordinal syntax refers to the order in which columns appear in select statement for instance,
 here 1 refers to the rating and 2 refers to the category.
 
 Always 1 index for ordinal syntax!!!!!
