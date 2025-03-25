# Users

### Create Users
```sql
CREATE USER 'admin'@'localhost' IDENTIFIED BY "abc1234";
```
```sql
CREATE USER 'guest'@'localhost' IDENTIFIED BY "xyz45";
```

```sql
CREATE USER 'student'@'localhost' IDENTIFIED BY "pqr789";
```

### Change DB
```sql
USE mysql;
```

### Show Users
```sql
SELECT user, host, password FROM user;
```

```
+---------+-----------+-------------------------------------------+
| User    | Host      | Password                                  |
+---------+-----------+-------------------------------------------+
| root    | localhost |                                           |
| admin   | localhost | *5C923DF43CBBF31AA3B451CC68A9CB894BB4D726 |
| root    | 127.0.0.1 |                                           |
| root    | ::1       |                                           |
| pma     | localhost |                                           |
| guest   | localhost | *B5A298C2F2A7DADDD5A813B11BEE4E06E31C09BB |
| student | localhost | *E7E2131E644A0971A307B62EBF638E415D5CC865 |
+---------+-----------+-------------------------------------------+
7 rows in set (0.001 sec)
```

```sql
SELECT * FROM user;
```

### Delete User
```sql
DROP USER 'guest'@'localhost';
```

```sql
SELECT user, host, password FROM user;
```

```
+---------+-----------+-------------------------------------------+
| User    | Host      | Password                                  |
+---------+-----------+-------------------------------------------+
| root    | localhost |                                           |
| admin   | localhost | *5C923DF43CBBF31AA3B451CC68A9CB894BB4D726 |
| root    | 127.0.0.1 |                                           |
| root    | ::1       |                                           |
| pma     | localhost |                                           |
| student | localhost | *E7E2131E644A0971A307B62EBF638E415D5CC865 |
+---------+-----------+-------------------------------------------+
6 rows in set (0.001 sec)
```

