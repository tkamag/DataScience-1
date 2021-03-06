A Fuzzy Database Implementation in Python
=========================

# 1. Introduction

## Create a new database 

    CREATE DATABASE fuzzydb;
    
## Create similarity tables
    
    CREATE TABLE color_sim (color_id VARCHAR(10), purple FLOAT, blue FLOAT, green FLOAT, yellow FLOAT, orange FLOAT, red FLOAT);
    

    +------------+-------+-------+------+------+------------+------------+------------+------------+
    | district   | north | south | east | west | north_west | north_east | south_west | south_east |
    +------------+-------+-------+------+------+------------+------------+------------+------------+
    | north      |     1 |     0 |  0.2 |  0.2 |        0.5 |        0.5 |        0.1 |        0.1 |
    | south      |     0 |     1 |  0.2 |  0.2 |        0.5 |        0.5 |        0.5 |        0.5 |
    | east       |   0.2 |   0.2 |    1 |    0 |        0.1 |        0.5 |        0.1 |        0.5 |
    | west       |   0.2 |   0.2 |    0 |    1 |        0.5 |        0.1 |        0.5 |        0.1 |
    | north_west |   0.5 |   0.1 |  0.1 |  0.5 |          1 |        0.2 |        0.2 |          0 |
    | north_east |   0.5 |   0.1 |  0.5 |  0.1 |        0.2 |          1 |          0 |        0.2 |
    | south_west |   0.1 |   0.5 |  0.1 |  0.5 |        0.2 |          0 |          1 |        0.2 |
    | south_east |   0.1 |   0.5 |  0.5 |  0.1 |          0 |        0.2 |        0.2 |          1 |
    +------------+-------+-------+------+------+------------+------------+------------+------------+   

 mysql> select * from houseinfo;
 +------+-----------+-----------+------------+------+------+
 | id   | num_rooms | num_baths | district   | age  | area |
 +------+-----------+-----------+------------+------+------+
 |    1 |         4 |         2 | north      |   10 |  550 |
 |    2 |         3 |         1 | north      |    7 |  200 |
 |    3 |         2 |         1 | east       |    4 |  150 |
 |    4 |         3 |         1 | south      |    3 |  350 |
 |    5 |         5 |         2 | west       |    5 |  500 |
 |    6 |         6 |         3 | north_east |    3 |  700 |
 |    7 |         3 |         1 | west       |    5 |  200 |
 |    8 |         4 |         2 | north_east |    3 |  250 |
 |    9 |         2 |         1 | south_east |    5 |  150 |
 |   10 |         1 |         1 | north_west |    3 |  100 |
 |   11 |         3 |         1 | south      |    2 |  250 |
 +------+-----------+-----------+------------+------+------+ 

 mysql> select * from pricetable;
 +------+-------+-------+-------+-------+
 | id   | a     | b     | c     | d     |
 +------+-------+-------+-------+-------+
 |    1 | 10000 | 10000 | 10000 | 10000 |
 |    2 |  6000 |  6000 |  7500 |  7500 |
 |    3 |  5000 |  6000 |  6000 |  7000 |
 |    4 |  9000 |  9000 |  9000 |  9000 |
 |    5 | 12000 | 13000 | 14000 | 15000 |
 |    6 | 35000 | 35000 | 36000 | 36000 |
 |    7 | 13000 | 13000 | 13000 | 13000 |
 |    8 | 14000 | 14500 | 14500 | 15000 |
 |    9 |  5500 |  5500 |  5500 |  5500 |
 |   10 |  5000 |  6000 |  6500 |  7000 |
 |   11 |  8000 |  8000 |  8000 |  8000 |
 +------+-------+-------+-------+-------+
