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
```

### Login with another user account
```
mysql -u admin -p
```

## Manage Users

### Update username

```sql
UPDATE USER SET user='NewAdmin' WHERE user='admin';
```
```sql
SELECT user, host, password FROM user;
```
```
+----------+-----------+-------------------------------------------+
| User     | Host      | Password                                  |
+----------+-----------+-------------------------------------------+
| root     | localhost |                                           |
| NewAdmin | localhost | *5C923DF43CBBF31AA3B451CC68A9CB894BB4D726 |
| root     | 127.0.0.1 |                                           |
| root     | ::1       |                                           |
| pma      | localhost |                                           |
| student  | localhost | *E7E2131E644A0971A307B62EBF638E415D5CC865 |
+----------+-----------+-------------------------------------------+
```
```sql
FLUSH privileges;
```
```sql
ALTER USER 'NewAdmin'@'localhost' IDENTIFIED BY 'abc1234';
```
```
mysql -u NewAdmin -p
```
---
```sql
UPDATE USER SET user='student1' WHERE user='student';
```
```sql
SELECT user, host, password FROM user;
```
```
+----------+-----------+-------------------------------------------+
| User     | Host      | Password                                  |
+----------+-----------+-------------------------------------------+
| root     | localhost |                                           |
| NewAdmin | localhost | *5C923DF43CBBF31AA3B451CC68A9CB894BB4D726 |
| root     | 127.0.0.1 |                                           |
| root     | ::1       |                                           |
| pma      | localhost |                                           |
| student1 | localhost | *E7E2131E644A0971A307B62EBF638E415D5CC865 |
+----------+-----------+-------------------------------------------+
```
```sql
FLUSH privileges;
```
```sql
ALTER USER 'student1'@'localhost' IDENTIFIED BY 'xyz45';
```
```
mysql -u student1 -p
```

### Update user password
```sql
SET password FOR 'student1'@'localhost' = password('xyz456');
```

### Update user host
```sql
UPDATE USER SET host='vau.ac.lk' WHERE user='student1' AND host='localhost';
```