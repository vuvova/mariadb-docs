# DATE FUNCTION

## Syntax

```
DATE(expr)
```

## Description

Extracts the date part of the [date](../../data-types/date-and-time-data-types/date.md) or [datetime](../../data-types/date-and-time-data-types/datetime.md) expression _expr_. Returns NULL and throws a warning when passed an invalid date.

## Examples

```
SELECT DATE('2013-07-18 12:21:32');
+-----------------------------+
| DATE('2013-07-18 12:21:32') |
+-----------------------------+
| 2013-07-18                  |
+-----------------------------+
```

<sub>_This page is licensed: GPLv2, originally from [fill\_help\_tables.sql](https://github.com/MariaDB/server/blob/main/scripts/fill_help_tables.sql)_</sub>

{% @marketo/form formId="4316" %}
