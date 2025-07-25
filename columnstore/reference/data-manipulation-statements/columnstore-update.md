# ColumnStore Update

The `UPDATE` statement changes data stored in rows.

1. [Syntax "Syntax"](columnstore-update.md#syntax)

## Syntax

Single-table syntax:

```sql
UPDATE  table_reference 
  SET col1={expr1|DEFAULT} [,col2={expr2|DEFAULT}] ...
  [WHERE where_condition]
  [ORDER BY ...]
  [LIMIT row_count]
```

Multiple-table syntax:

```sql
UPDATE table_references
    SET col1={expr1|DEFAULT} [, col2={expr2|DEFAULT}] ...
    [WHERE where_condition]
```

{% hint style="info" %}
Note: It can only 1 table (but multiple columns) be updated from the table list in table\_references.
{% endhint %}

<sub>_This page is licensed: CC BY-SA / Gnu FDL_</sub>

{% @marketo/form formId="4316" %}
