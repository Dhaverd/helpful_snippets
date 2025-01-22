# MySQL users actions

## Show users with hosts

```
SELECT User, Host FROM mysql.user;
```

## Check user privileges

```
SHOW GRANTS FOR 'someuser'@'somehost.somedomain';
```

## Create user

```
CREATE USER 'some_user'@'somehost.somedomain' IDENTIFIED BY 'some_password';
FLUSH PRIVILEGES;
```

## Delete user

```
DROP USER 'some_user'@'somehost.somedomain';
FLUSH PRIVILEGES;
```

## Granting privileges

### Grant all privileges

```
GRANT ALL PRIVILEGES ON *.* TO 'some_user'@'somehost.somedomain' WITH GRANT OPTION;
FLUSH PRIVILEGES;
```

### Grant privilege on database 'some_db'

```
GRANT SELECT ON `some_db`.* TO 'some_user'@'somehost.somedomain';
FLUSH PRIVILEGES;
```

### Grant privilege on table 'some_db'.'some_table'

```
GRANT SELECT ON `some_db`.'some_table' TO 'some_user'@'somehost.somedomain';
FLUSH PRIVILEGES;
```

### Grant privilege to select and update some columns on table 'some_db'.'some_table'

```
GRANT SELECT (id, some_column), UPDATE (some_column) ON `some_db`.`some_table` TO 'some_user'@'somehost.somedomain';
```

### Grant with inheritance

```
GRANT SELECT, INSERT, UPDATE, DELETE ON `some_db`.* TO 'some_user'@'somehost' WITH GRANT OPTION;
FLUSH PRIVILEGES;
```

**'WITH GRANT OPTION'** makes it possible to convey to others what is permitted to oneself.

## Revoking privileges

### Revoke privilege to select from database 'somedb'

```
REVOKE SELECT ON `somedb`.* FROM 'someuser'@'somehost';
FLUSH PRIVILEGES;
```

### Revoke all privileges from user

```
ALL PRIVILEGES ON *.* FROM 'someuser'@'somehost';
FLUSH PRIVILEGES;
```

### Revoke all privileges to database 'somedb' from user

```
ALL PRIVILEGES ON `somedb`.* FROM 'someuser'@'somehost';
FLUSH PRIVILEGES;
```

### Revoke all privileges from user

```
REVOKE ALL PRIVILEGES, GRANT OPTION FROM 'someuser'@'somehost';
FLUSH PRIVILEGES;
```

## Change password

```
ALTER USER 'test_user'@'localhost' IDENTIFIED BY 'new_password';
```