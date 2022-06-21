# SQL 기초 🍕 



## SQL 명령어

* 데이터베이스: Table 여러 개로 구성됨
* Table: pandas에서 dataframe과 동일함

* 명령 마칠 때 ;를 붙여야 함

---



- CREATE DATABASE 데이터베이스이름; : 데이터베이스를 생성하라
- DROP DATABASE StudentAdministration; # 데이터베이스 지우기

- SHOW DATABASES; : 데이터베이스를 보여주어라

```sql
CREATE DATABASE StudentAdministration; # 학생관리시스템 만들기
DROP DATABASE StudentAdministration; # 학생관리시스템 지우기
SHOW DATABASES; # 데이터베이스를 보여주어라
+-----------------------+
| Database              |
+-----------------------+
| StudentAdministration | # 만든 데이터프레임
| information_schema    |
| mysql                 |
| performance_schema    |
| sys                   |
+-----------------------+
5 rows in set (0.01 sec)
```



- USE StudentAdministraion; # 해당 데이터베이스 안으로 들어감
- SHOW tables; # 테이블 보기

```sql
USE StudentAdministraion; # 해당 데이터베이스 안으로 들어감
SHOW tables; # 테이블 보기
Empty set (0.00 sec) # table 아직 안 만들어서 empty
```



- CREATE TABLE 테이블 이름 # 테이블 생성

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



- 테이블에 데이터 생성 후 어떤 내용이 있는지 확인

```sql
INSERT INTO StudentBasic VALUES (
'20224189', '이정훈', '종로구평창동파크팰리스', '남', '의료정보학');
INSERT INTO StudentBasic VALUES (
'20224190', '이유진', '대치동타워펠리스', '여', '소비자학');
INSERT INTO StudentBasic VALUES (
'20224191', '박진영', '한남빌라', '남', '소비자학');
INSERT INTO StudentBasic VALUES (
'20224192', '김소영', '한남유엔빌리지', '여', '컴퓨터공학');
INSERT INTO StudentBasic VALUES (
'20224189', '김소영', '한남유엔빌리지', '여', '컴퓨터공학');

INSERT INTO Score VALUES ('20224189', '2021-2', '의료이미지딥러닝', 'A-');
INSERT INTO Score VALUES ('20224190', '2021-2', '의료이미지딥러닝', 'A+');
INSERT INTO Score VALUES ('20224191', '2021-2', '의료이미지딥러닝', 'A+');
INSERT INTO Score VALUES ('20224192', '2021-2', '의료이미지딥러닝', 'A+');
```



- SELECT * FROM StudentBasic; # StudentBasic 테이블에서 모든 row를 출력하라
- SELECT * FROM Score; # Score 테이블에서 모든 row를 출력하라

```sql
SELECT * FROM StudentBasic; # StudentBasic 테이블에서 모든 row를 출력하라
SELECT * FROM StudentBasic limit 1; # StudentBasic 테이블에서 1줄만 보여주어라
SELECT * FROM StudentBasic where Gender = '여'; # StudentBasic 테이블에서 여자만 보여주어라  
SELECT * FROM StudentBasic where Gender = '여' or Major = '의료정보학';
```

- 데이터 지우기

```sql
DELETE FROM StudentBasic where Gender='여';
```

- 테이블 지우기

```sql
DROP TABLE StudentBasic;
```

- Primary key 설정하여 테이블 생성

```sql
CREATE TABLE StudentBasic (
    StudentID int PRIMARY KEY,
    Name varchar(30),
    Address varchar(255),
    Gender varchar(3), 
    Major varchar(30)
);
```

- StudentBasic의 Pimary key를 기준으로 테이블 합치기

```sql
SELECT *
FROM StudentBasic
LEFT JOIN Score ON StudentBasic.StudentID = Score.StudentID;
```

- 행 개수 세기

```sql
Select count(*) from StudentBasic;
```

- Gender로 그룹화하여 count

```sql
Select Gender, count(*) from StudentBasic group by Gender;
```

- 테이블 수정하여 Primary key 추가

```sql
ALTER TABLE Score MODIFY COLUMN StudentID int PRIMARY KEY;
```



