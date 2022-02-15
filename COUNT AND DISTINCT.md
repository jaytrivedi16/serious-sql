# COUNT AND DISTINCT

**GROUP BY COUNT**

Let's say we want to find out the frequency of the output and group by,
for this we can use a GROUP BY clause and COUNT function.  

`SELECT rating, COUNT(*) AS frequency FROM dvd_rentals.film_list GROUP BY rating;`

---



Further, let's use order by clause to view the results in descending order:

`select rating, count(*) as frequency from dvd_rentals.film_list group by rating order by frequency desc;`

**ADDING PERCENTAGE TO THE CALCULATION**

This following section is an optional bonus component as it will touch on some SQL techniques which we have yet to cover so far in this course!

Sometimes the frequency is just not enough to really understand the frequency at a quick glance, so we like to create an additional percentage column to our dataset.

There are actually various ways to perform this operation but I will keep things simple and show you the most efficient way using a modified window function combining both SUM and COUNT functions with an OVER() clause.

Take note of that ::NUMERIC right after the COUNT(`*`) - this is to avoid the dreaded integer floor division which is covered in much more depth in the appendix!

`SELECT rating, COUNT(*) AS frequency, COUNT(*)::NUMERIC / SUM(COUNT(*)) OVER () AS percentage FROM dvd_rentals.film_list GROUP BY rating ORDER BY frequency DESC;`

In the above code, we are selecting rating counting all of the inputs, converting it to numeric data type as with percentages
the decimal comes and then using sum(count(`*`)) to add all the values of the frequency and over() clause is used to help in division.

To round it off,

`select rating, count(*) as frequency, round(100* count(*):: NUMERIC / sum(count(*)) over(), 2) as percentage from dvd_rentals.film_list group by rating order by frequency desc;`

---

**COUNTS FOR MULTIPLE COLUMN COMBINATIONS**

When counting for multiple columns we can do this by using group by clause and just specify additional columns in the grouping element expressions at the bottom of the SQL statement.
When we use GROUP BY in more than 2+ columns, the subsequent count function will aggregate the records based off the unique combination of the values in these columns instead of a single 1.

`select rating, category, count(*) as frequency from dvd_rentals.film_list group by rating, category order by frequency desc limit 5

Similarly, you can reduce the writing of target columns used in GROUP BY or ORDER BY clause by the positional number that the columns appear in the select statement.

For instance, `select rating, category, count(*) as frequency from dvd_rentals.film_list group by 1,2`
Here 1 denotes rating and 2 denotes the category used in the select statement.
