# SQL ๊ธฐ์ด ๐ 



## SQL ๋ช๋ น์ด

* ๋ฐ์ดํฐ๋ฒ ์ด์ค: Table ์ฌ๋ฌ ๊ฐ๋ก ๊ตฌ์ฑ๋จ
* Table: pandas์์ dataframe๊ณผ ๋์ผํจ

* ๋ช๋ น ๋ง์น  ๋ ;๋ฅผ ๋ถ์ฌ์ผ ํจ

---



- CREATE DATABASE ๋ฐ์ดํฐ๋ฒ ์ด์ค์ด๋ฆ; : ๋ฐ์ดํฐ๋ฒ ์ด์ค๋ฅผ ์์ฑํ๋ผ
- DROP DATABASE StudentAdministration; # ๋ฐ์ดํฐ๋ฒ ์ด์ค ์ง์ฐ๊ธฐ

- SHOW DATABASES; : ๋ฐ์ดํฐ๋ฒ ์ด์ค๋ฅผ ๋ณด์ฌ์ฃผ์ด๋ผ

```sql
CREATE DATABASE StudentAdministration; # ํ์๊ด๋ฆฌ์์คํ ๋ง๋ค๊ธฐ
DROP DATABASE StudentAdministration; # ํ์๊ด๋ฆฌ์์คํ ์ง์ฐ๊ธฐ
SHOW DATABASES; # ๋ฐ์ดํฐ๋ฒ ์ด์ค๋ฅผ ๋ณด์ฌ์ฃผ์ด๋ผ
+-----------------------+
| Database              |
+-----------------------+
| StudentAdministration | # ๋ง๋  ๋ฐ์ดํฐํ๋ ์
| information_schema    |
| mysql                 |
| performance_schema    |
| sys                   |
+-----------------------+
5 rows in set (0.01 sec)
```



- USE StudentAdministraion; # ํด๋น ๋ฐ์ดํฐ๋ฒ ์ด์ค ์์ผ๋ก ๋ค์ด๊ฐ
- SHOW tables; # ํ์ด๋ธ ๋ณด๊ธฐ

```sql
USE StudentAdministraion; # ํด๋น ๋ฐ์ดํฐ๋ฒ ์ด์ค ์์ผ๋ก ๋ค์ด๊ฐ
SHOW tables; # ํ์ด๋ธ ๋ณด๊ธฐ
Empty set (0.00 sec) # table ์์ง ์ ๋ง๋ค์ด์ empty
```



- CREATE TABLE ํ์ด๋ธ ์ด๋ฆ # ํ์ด๋ธ ์์ฑ

  ```sql
  CREATE TABLE StudentBasic (
      StudentID int,
      Name varchar(30),
      Address varchar(255),
      Gender varchar(3), 
      Major varchar(30)
  );
  
  CREATE TABLE Score (
      StudentID int,
      Semester varchar(30),
      Subject varchar(30),
      Score varchar(3)
  );
  
  SHOW TABLES;
  +---------------------------------+
  | Tables_in_StudentAdministration |
  +---------------------------------+
  | Score                           |
  | StudentBasic                    |
  +---------------------------------+
  2 rows in set (0.00 sec)
  ```



- ํ์ด๋ธ์ ๋ฐ์ดํฐ ์์ฑ ํ ์ด๋ค ๋ด์ฉ์ด ์๋์ง ํ์ธ

```sql
INSERT INTO StudentBasic VALUES (
'20224189', '์ด์ ํ', '์ข๋ก๊ตฌํ์ฐฝ๋ํํฌํฐ๋ฆฌ์ค', '๋จ', '์๋ฃ์ ๋ณดํ');
INSERT INTO StudentBasic VALUES (
'20224190', '์ด์ ์ง', '๋์น๋ํ์ํ ๋ฆฌ์ค', '์ฌ', '์๋น์ํ');
INSERT INTO StudentBasic VALUES (
'20224191', '๋ฐ์ง์', 'ํ๋จ๋น๋ผ', '๋จ', '์๋น์ํ');
INSERT INTO StudentBasic VALUES (
'20224192', '๊น์์', 'ํ๋จ์ ์๋น๋ฆฌ์ง', '์ฌ', '์ปดํจํฐ๊ณตํ');
INSERT INTO StudentBasic VALUES (
'20224189', '๊น์์', 'ํ๋จ์ ์๋น๋ฆฌ์ง', '์ฌ', '์ปดํจํฐ๊ณตํ');

INSERT INTO Score VALUES ('20224189', '2021-2', '์๋ฃ์ด๋ฏธ์ง๋ฅ๋ฌ๋', 'A-');
INSERT INTO Score VALUES ('20224190', '2021-2', '์๋ฃ์ด๋ฏธ์ง๋ฅ๋ฌ๋', 'A+');
INSERT INTO Score VALUES ('20224191', '2021-2', '์๋ฃ์ด๋ฏธ์ง๋ฅ๋ฌ๋', 'A+');
INSERT INTO Score VALUES ('20224192', '2021-2', '์๋ฃ์ด๋ฏธ์ง๋ฅ๋ฌ๋', 'A+');
```



- SELECT * FROM StudentBasic; # StudentBasic ํ์ด๋ธ์์ ๋ชจ๋  row๋ฅผ ์ถ๋ ฅํ๋ผ
- SELECT * FROM Score; # Score ํ์ด๋ธ์์ ๋ชจ๋  row๋ฅผ ์ถ๋ ฅํ๋ผ

```sql
SELECT * FROM StudentBasic; # StudentBasic ํ์ด๋ธ์์ ๋ชจ๋  row๋ฅผ ์ถ๋ ฅํ๋ผ
SELECT * FROM StudentBasic limit 1; # StudentBasic ํ์ด๋ธ์์ 1์ค๋ง ๋ณด์ฌ์ฃผ์ด๋ผ
SELECT * FROM StudentBasic where Gender = '์ฌ'; # StudentBasic ํ์ด๋ธ์์ ์ฌ์๋ง ๋ณด์ฌ์ฃผ์ด๋ผ  
SELECT * FROM StudentBasic where Gender = '์ฌ' or Major = '์๋ฃ์ ๋ณดํ';
```

- ๋ฐ์ดํฐ ์ง์ฐ๊ธฐ

```sql
DELETE FROM StudentBasic where Gender='์ฌ';
```

- ํ์ด๋ธ ์ง์ฐ๊ธฐ

```sql
DROP TABLE StudentBasic;
```

- Primary key ์ค์ ํ์ฌ ํ์ด๋ธ ์์ฑ

```sql
CREATE TABLE StudentBasic (
    StudentID int PRIMARY KEY,
    Name varchar(30),
    Address varchar(255),
    Gender varchar(3), 
    Major varchar(30)
);
```

- StudentBasic์ Pimary key๋ฅผ ๊ธฐ์ค์ผ๋ก ํ์ด๋ธ ํฉ์น๊ธฐ

```sql
SELECT *
FROM StudentBasic
LEFT JOIN Score ON StudentBasic.StudentID = Score.StudentID;
```

- ํ ๊ฐ์ ์ธ๊ธฐ

```sql
Select count(*) from StudentBasic;
```

- Gender๋ก ๊ทธ๋ฃนํํ์ฌ count

```sql
Select Gender, count(*) from StudentBasic group by Gender;
```

- ํ์ด๋ธ ์์ ํ์ฌ Primary key ์ถ๊ฐ

```sql
ALTER TABLE Score MODIFY COLUMN StudentID int PRIMARY KEY;
```



