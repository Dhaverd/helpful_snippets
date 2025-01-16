# Identify what locking table

## Method 1

```
SHOW open tables WHERE In_use > 0;
```

## Method 2

```
SELECT
    OBJECT_SCHEMA, 
    OBJECT_NAME, 
    GROUP_CONCAT(DISTINCT EXTERNAL_LOCK)
FROM 
    performance_schema.table_handles 
WHERE 
    EXTERNAL_LOCK IS NOT NULL
GROUP BY 
    OBJECT_SCHEMA, 
    OBJECT_NAME;
```

## Process list

```
SHOW PROCESSLIST;
```