
# ACOS

## Syntax


```
ACOS(X)
```


## Description


Returns the arc cosine of `X`, that is, the value whose cosine is `X`.
Returns `NULL` if `X` is not in the range `-1` to `1`.


## Examples


```
SELECT ACOS(1);
+---------+
| ACOS(1) |
+---------+
|       0 |
+---------+

SELECT ACOS(1.0001);
+--------------+
| ACOS(1.0001) |
+--------------+
|         NULL |
+--------------+

SELECT ACOS(0);
+-----------------+
| ACOS(0)         |
+-----------------+
| 1.5707963267949 |
+-----------------+

SELECT ACOS(0.234);
+------------------+
| ACOS(0.234)      |
+------------------+
| 1.33460644244679 |
+------------------+
```


<sub>_This page is licensed: GPLv2, originally from [fill\_help\_tables.sql](https://github.com/MariaDB/server/blob/main/scripts/fill_help_tables.sql)_</sub>


{% @marketo/form formId="4316" %}
