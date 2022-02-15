# Sorting multiple columns with order by

If we are sorting two columns with order by the 
first column will be sorted and then whenever there is a tie the second column will be sorted 
accordingly.

`drop table if exists sample_table`
`create temp table sample_table as with raw_data(id, column_a, column_b) as (`
`VALUES`
`(1, 0, 'A'),`
`(2, 0, 'B'),`
`(3, 1, 'C'),`
`(4, 1, 'D'),`
`(5, 2, 'D'),`
`(6, 3, 'D'))`
---
`select * from raw_data`
---
`select * from sample_table order by column_a, column_b;`

Similarly, when sorting one in ascending and one in descending what will happen is can be 
understood from the below code:

`drop table if exists sample_table`
`create temp table sample_table as with raw_data(id, column_a, column_b) as (`
`VALUES`
`(1, 0, 'A'),`
`(2, 0, 'B'),`
`(3, 1, 'C'),`
`(4, 1, 'D'),`
`(5, 2, 'D'),`
`(6, 3, 'D'))`

`select * from raw_data`
`select * from sample_table order by column_a desc, column_b;`

In the second query the column_a gets sorted by descending order and for column_b wherevere
there is a tie as we can see in id 3,4 and 1,2. Column_a will return 1,1 and 0,0 as sorted 
and would perform ascending operation on column_b returning id 1 before id 2 and id 3 before
id 4.

Also, if we want both to be in descending we will get the result as accordingly.

`drop table if exists sample_table`
`create temp table sample_table as with raw_data(id, column_a, column_b) as (`
`VALUES`
`(1, 0, 'A'),`
`(2, 0, 'B'),`
`(3, 1, 'C'),`
`(4, 1, 'D'),`
`(5, 2, 'D'),`
`(6, 3, 'D'))`

`select * from raw_data`
`select * from sample_table order by column_a desc, column_b desc;`

Here, as opposed to checking for ties both will be sorted desc.

Now, we want to sort by column_b first and then column_a

`drop table if exists sample_table;`
`create temp table sample_table as with raw_data (id, column_a, column_b) as (`
  `VALUES`
    `(1, 0, 'A'),`
    `(2, 0, 'B'),`
    `(3, 1, 'C'),`
    `(4, 1, 'D'),`
    `(5, 2, 'D'),`
    `(6, 3, 'D')`
`)`
`select`
  `*`
`from`
  `raw_data;`
  
`select * from sample_table`
`order by column_b desc, column_a ;`


