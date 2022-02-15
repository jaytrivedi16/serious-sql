### How to sort multiple columns? Introdution to CTE

`drop table if exists sample_table;
create temp table sample_table as with raw_data (id, column_a, column_b) as (
  VALUES
    (1, 0, 'A'),
    (2, 0, 'B'),
    (3, 0, 'C'),
    (4, 1, 'D'),
    (5, 2, 'D')
)
select
  *
from
  raw_data;
  
select * from sample_table;`