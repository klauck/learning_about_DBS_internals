# Simplicity in Learning about Database System Internals
Hands-on Examples and Learnings about Database System (DBS) Internals

## Work in progress: Will be filled with the paper content on March 21.


## Hand-On Examples for Learning and Teaching DBS Internals

### PostgreSQL

Sources of detailed information:

* [PostgreSQL Documentation](https://www.postgresql.org/docs/current/index.html)

* [The Internals of PostgreSQL](https://www.interdb.jp/pg/)

* [PostgreSQL 14 Internals](https://postgrespro.com/community/books/internals)

#### Physical Database Organization

* ```SELECT setting FROM pg_settings WHERE name = ’data_directory’;```

  returns the base directory, where PostgreSQL stores its configuration and data files.

* ```SELECT relfilenode FROM pg_class WHERE relname = ’lineitem’;```
  
  returns the file name of the lineitem table.

* ```SELECT datname, oid FROM pg_database;```

   returns the object identifier per database.

* ```SELECT relname, oid FROM pg_class;```

  returns the object identifier per relation/table.

* ```CREATE EXTENSION pageinspect;``` sets up the [pageinspect extension](https://www.postgresql.org/docs/current/pageinspect.html).

* ```SELECT * FROM page_header(get_raw_page('nation', 0));```

  returns the page header of the nation table's first block.

* ```SELECT lp, lp_off, t_xmin, t_xmax, t_ctid FROM heap_page_items(get_raw_page('nation', 0));```

  returns the linepoiters, byte offsets, and MVCC information of all tuples that are stored on the nation table's first block.

#### Statistics

* ```SELECT attname, null_frac, n_distinct, most_common_vals, correlation FROM pg_stats WHERE tablename='nation';```

  shows some attribute statistics of the nation table.

#### Plan Inspection and Cost Estimation

* ```SELECT n_nationkey, n_name, n_regionkey FROM nation WHERE n_regionkey = 4;;```
  
  shows the content of the nation table first.

  ```EXPLAIN SELECT * FROM nation WHERE n_regionkey = 4;```
  
  shows the query plan, cost estimation and cardinality estimation.



## General Material for Learning DBS Internals

### Textbooks

### Papers, Conferences, and Workshops

### Advanced Courses and Lecture Series

### Blogs, Mailing Lists, Social Networks, the Internet
