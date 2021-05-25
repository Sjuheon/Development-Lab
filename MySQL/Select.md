`select * from table`

<pre>
mysql> select * from coin;
+------+----------+---------+------------+
| name | price    | compare | total      |
+------+----------+---------+------------+
| XRP  |     1050 | +9.O5%  | 2,765,441M |
| DOGE |      401 | +7.20%  | 1,483,292M |
| ETC  |    72680 | +14.82% | 1,640,139M |
| BTC  | 45861000 | +7.79%  | 1.253.004M |
| ETH  |  2902000 | +8.00   | 1,403,878M |
| BTT  |        4 | +7.61%  | 325,277M   |
+------+----------+---------+------------+
6 rows in set (0.00 sec)
</pre>

<br>

`select * from table where A(conditional expression)`

<pre>
mysql> select * from coin where price < 10000;
+------+-------+---------+------------+
| name | price | compare | total      |
+------+-------+---------+------------+
| XRP  |  1050 | +9.O5%  | 2,765,441M |
| DOGE |   401 | +7.20%  | 1,483,292M |
| BTT  |     4 | +7.61%  | 325,277M   |
+------+-------+---------+------------+
3 rows in set (0.00 sec)
</pre>

<br>

`select * from table where A and B`

<pre>
mysql> select * from coin where price > 1000 and price < 1000000;
+------+-------+---------+------------+
| name | price | compare | total      |
+------+-------+---------+------------+
| XRP  |  1050 | +9.O5%  | 2,765,441M |
| ETC  | 72680 | +14.82% | 1,640,139M |
+------+-------+---------+------------+
2 rows in set (0.00 sec)
</pre>

<br>

`select * from table where A or B`

<pre>
mysql> select * from coin where name = "DOGE" or price = 4;
+------+-------+---------+------------+
| name | price | compare | total      |
+------+-------+---------+------------+
| DOGE |   401 | +7.20%  | 1,483,292M |
| BTT  |     4 | +7.61%  | 325,277M   |
+------+-------+---------+------------+
2 rows in set (0.00 sec)
</pre>

<br>

`select * from table where (A or B) and (C or D)`

<pre>
mysql> select * from coin where (name = "DOGE" or name = "BTT") and (price = 4 or price = 1050);
+------+-------+---------+----------+
| name | price | compare | total    |
+------+-------+---------+----------+
| BTT  |     4 | +7.61%  | 325,277M |
+------+-------+---------+----------+
1 row in set (0.00 sec)
</pre>

<br>

`select * from table where not A`

<pre>
mysql> select * from coin where not price < 2000;
+------+----------+---------+------------+
| name | price    | compare | total      |
+------+----------+---------+------------+
| ETC  |    72680 | +14.82% | 1,640,139M |
| BTC  | 45861000 | +7.79%  | 1.253.004M |
| ETH  |  2902000 | +8.00   | 1,403,878M |
+------+----------+---------+------------+
3 rows in set (0.00 sec)
</pre>

<br>

```
select * from table where text like 'A%'
```

<pre>
mysql> select * from coin where name like 'DO%';
+------+-------+---------+------------+
| name | price | compare | total      |
+------+-------+---------+------------+
| DOGE |   401 | +7.20%  | 1,483,292M |
+------+-------+---------+------------+
1 row in set (0.00 sec)
</pre>

<br>

```
select * from table where text like '%A%'
```

<pre>
mysql> select * from coin where name like '%C%';
+------+----------+---------+------------+
| name | price    | compare | total      |
+------+----------+---------+------------+
| ETC  |    72680 | +14.82% | 1,640,139M |
| BTC  | 45861000 | +7.79%  | 1.253.004M |
+------+----------+---------+------------+
2 rows in set (0.00 sec)
</pre>
