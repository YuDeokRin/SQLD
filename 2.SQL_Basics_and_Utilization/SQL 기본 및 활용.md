# SQL 기본 및 활용

제 1장 SQL  기본

- [x]  제 1절 관계형 데이터베이스 개요
- [x]  제 2절 DDL
- [ ]  제 3절 DML
- [ ]  제 4절 TCL
- [ ]  제 5절 WHERE 절
- [ ]  제 6절 함수(FUNCTION)
- [ ]  제 7절 GROUP BY, HAVING 절
- [ ]  제 8절 ORDER BY절
- [ ]  제 9절 조인(JOIN)

# 제 1절 관계형 데이터베이스 개요

## 1. 데이터베이스
넓은 의미에서의 데이터베이스는 이러한 일상적인 정보들을 모아 놓은 것 자체를 의미한다.
그러나 일반적으로 데이터베이스라고 말할 떄는 특정 기업이나 조직 또는 개인이 필요에 의해(Ex : 부가 가치가 발생하는) 데이터를 일정한 형태로 저장해 놓은 것을 의미한다.

## 2. SQL(Structured Query Language)
SQL(Structured Query Language)은 관계형 데이터베이스에서 데이터 정의, 데이터 조작, 데이터 제어를 하기 위해 사용하는 언어이다.
![image](https://user-images.githubusercontent.com/56623911/131689345-8c085c1c-f270-4296-a144-acabc9345d45.png)
## 3.TABLE
 테이블(TABLE)은 데이터를 저장하는 객체(Object)로서 관계형 데이터베이스의 기본 단위이다.
관계형 데이터베이스에서는 모든 데이터를 칼럼과 행의 2차원 구조로 나타낸다.
세로 방향을 칼럼(Column), 가로 방향을 행(Row)이라고 하고,  칼럼과 행이 겹치는 하나의 공간을 필드(Field)라고 한다. 

![image](https://user-images.githubusercontent.com/56623911/131693529-80eb85a4-bfd5-4dc1-81c7-eb911a79cc23.png)

테이블(Table) : 행과 컬럼의 2차원 구조를 가진 데이터의 저장 장소이며, 데이터베이스의 가장 기본적인 개념<br>
칼럼/열(Column) : 2차원 구조를 가진 테이블에서 세로 방향으로 이루어진 하나하나의 특정 속성(더이상 나눌 수 없는 특성)<br>
행(Row) : 2차원 구조를 가진 테이즐에서 가로 방향으로 이루어진 연결된 데이터<br>

선수와 관련된 데이터를 저장할 때 모든 데이터를 하나의 테이블로 저장하지 않는다. 밑에 그림을 보면 선수와 관련된 데이터를 선수 테이블과 구단 테이블이라는 복수의 테이블로 분할하여 저장하고 있다.<br>
그리고 분할된 테이블은 그 칼럼의 값에 의해 연결된다. 이렇게 테이블을 분할하여 데이터의 불필요한 중복을 줄이는 것을 정규화(Normalization)라고 한다.<br>
데이터의 정합성 확보와 데이터 입력/수정/삭제 시 발생 할 수 있는 이상 현상을(Anomaly)을 방지하기 위해 정규화는 관계형 데이터베이스 모델링에서 매우 중요한 프로세스이다.

![image](https://user-images.githubusercontent.com/56623911/131694141-7c92f5ad-f132-442f-bb47-e6a1acfb4c5d.png)

각 행을 한 가지 의미로 특정할 수 있는 한 개 이상의 칼럼을 기본키(Primary key)라고 하며, 여기서는 <선수>테이블의 '선수번호'와 <구단> 테이블의 '구단코드'가 기본키가 된다. 또, <선수> 테이블의 '구단코드'와 같이 다른 테이블의 기본 키로 사용되면서 테이블과의 관계를 연결하는 역할을 하는 칼럼을 외부키(Foreign Key)라고 한다.

![image](https://user-images.githubusercontent.com/56623911/131694833-880e5421-082a-4bc6-8126-1da5698bdc31.png)

## 4. ERD(Entity Relationship Diagram)

팀 정보와 선수 정보 간에는 어떤 의미의 관계가 존재하며, 다른 테이블과도 어떤 의미의 연관성이나 관계를 가지고 있다. ERD(Entity Relationship Diagram)는 이와 같은 관계의 의미를 직관적으로 표현할 수 있는 좋은 수단이다.


![image](https://user-images.githubusercontent.com/56623911/131695238-1f5ad519-3dfc-4e80-9ac9-376e57ae1289.png)





# 제 2절 DDL(DATA DEFINITION LANGUAGE)

### 1. 데이터 유형

![image](https://user-images.githubusercontent.com/56623911/131686030-4973ed71-9eb9-4d14-b64c-3634b1ae08f6.png)


2) CREATE TABLE

테이블을 일정한 형식에 의해서 생성된다. 테이블 생성을 위해서는 해당 테이블에 입력될 테이터를 정의하고 정의한 데이터를 어떠한 데이터 유형으로 선언할 것인지를 결정해야 한다.

1) 테이블과 칼럼 정의

테이블에 존재하는 모든 데이터는 고유하게 식별할 수 있으면서 반드시 값이 존재하는 단일 칼럼이나 칼럼의 조합들(후보키)중에 하나를 선정하여 기본키 칼럼으로 지정한다. 선수 테이블에 예로 들면 '선수ID' 칼럼이 기본키로 적당할 것이다.
기본키는 단일 칼럼이 아닌 여러 개의 칼럼으로도 만들어질 수 있다. 그리고 테이블과 테이블 간에 정의된 관계는 기본키(PRIMARY KEY)와 외부키(FOREIGN KEY)를 활용해서 설정하도록 한다.


![Untitled 8](https://user-images.githubusercontent.com/56623911/132091399-77868597-4232-42f1-b183-f2cdcbd1e0c6.png)


부서-사원 관계의 칼럼 정보

![Untitled 9](https://user-images.githubusercontent.com/56623911/132091352-617ce591-0e00-430c-a9ff-fd54762730e0.png)



테이블을 생성하는 구문 형식

```sql
CREATE TABLE 테이블이름 (
 칼럼명1 DATATYPE [DEFAULT 형식],
 칼럼명2 DATATYPE [DEFAULT 형식],
 칼럼명3 DATETYPE [DEFAULT 형식]
);
```

테이블 생성 시에 주의해야할 규칙

- 테이블명은 객체를 의미할 수 있는 적절한 이름을 사용한다. 가능한 단수형을 권고한다.
- 테이블 명은 다른 테이블의 이름과 중복되지 않아야 한다.
- 한 테이블 내에서는 칼럼명이 중복되게 지정될 수 없다.
- 테이블 이름을 지정하고 각 칼럼들은 괄호 "( )"로 묶어 지정한다.
- 각 칼럼들은 콤마 ","로 구분되고, 테이블 생성문의 끝은 항상 세미콜론 ";"으로 끝난다.
- 칼럼에 대해서는 다른 테이블까지 고려하여 데이터베이스 내에서는 일관성 있게 사용하는 것이 좋다(데이터 표준화 관점)
- 칼럼 뒤에 데이터 유형은 꼭 지정되어야 한다.
- 테이블명과 칼럼명은 반드시 문자로 시작해야 하고, 벤더별로 길이에 대한 한계가 있다.
- A-Z, a-z, 0-9, _, $, # 문자만 허용한다.
- 테이블 생성시 대/소문자 구분은 하지 않는다.
기본적으로 테이블이나 칼럼명은 대문자로 만들어진다.
- DATETIME 데이터 유형에는 별로로 크기를 지정하지 않는다.
- 문자 데이터 유형은 반드시 가질 수 있는 최대 길이를 표시해야 한다.
- 칼럼과 칼럼의 구분은 콤마로 하되, 마지막 칼럼은 콤마를 찍지 않는다.
- 칼럼에 대한 제약조건이 있으면 CONSTRAINT를 이용하여 추가할 수 있다.

테이블명이 잘못된 사례

10_PLAYER     ← 반드시 숫자가 아닌 문자로 시작되어야 함

T-PLAYER ← 특수 문자 "-"는 허영되지 않음

3) 제약 조건(CONSTRAINT)

제약 조건(CONSTRAINT)이란 사용자가 원하는 조건의 데이터만 유지하기 위한 즉, 데이터의 무결성을 유지하기 위한 데이터 베이스의 보편적인 방법으로 테이블의 특정 칼럼에 설정하는 제약이다.

![Untitled 10](https://user-images.githubusercontent.com/56623911/132091421-c7c0b8e5-a917-4ad3-b98a-530e13832059.png)


- NULL 의미

NULL(ASCII   코드 00번)은 공백(BLANK, ASCII 코드 32번) 이나 숫자 0(ZERO, ASCII 48번)과는 전혀 다른 값이며, 조건에 맞는 데이터가 없을 때의 공집합과도 다르다. 'NULL'은 '아직 정의되지 않은 미지의 값' 이거나 ' 현재 데이터를 입력하지 못하는 경우' 를 의미한다. 

- DEFAULT 의미

 데이터 입력 시에 칼럼의 값이 지정되어 있지 않을 경우 기본값(DEFAULT)을 사전에 설명할 수 있다. 데이터 입력시 명시된 값을 지정하지 않은 경우에 NULL 값이 입력되고, DEFAULT  값을 정의했다면 해당 칼럼에 NULL 값이 입력되지 않고 사전에 정의된 기본 값이 자동으로 입력된다.

### 3. ALTER TABLE

한번 생성된 테이블은 특별히 사용자가 구조를 변경하기 전까지 생성 당시의 구조를 유지하게 된다.
처음의 테이블 구조를 그대로 유지하는 것이 최선이지만, 업무적인 요구 사항이나 시스템 운영상 테이블을 사용하는 도중에 변경해야 할 일들이 발생할 수도 있다.
이 경우 주로 칼럼을 추가/삭제하거나 제약조건을 추가/삭제하는 작업을 진행하게 된다.

1) ADD COLUMN

기존 테이블에 필요한 칼럼을 추가하는 명령이다.
단, 새롭게 추가된 칼럼은 테이블의 마지막 칼럼이 되며 칼럼의 위치를 지정할 수는 없다.

```sql
ALTER TABLE         테이블명
ADD 추가할 칼럼명    데이터 유형;
```

2) DROP COLUMN

DROR COLUMN은 테이블에서 필요 없는 칼럼을 삭제할 수 있으며, 데이터가 있거나 없거나 모두 삭제 가능하다. 한 반에 하나의 칼럼만 삭제 가능하며, 칼럼 삭제 후 최소 하나 이상의 칼럼이 테이블에 존재해야 한다. 

주의할 부분은 한 번 삭제된 칼럼은 복구가 불가능하다.

```sql
ALTER TABLE 테이블명
DROP COLUMN  삭제할 컬럼명;
```

3) MODIFY COLUMN

테이블에 존재하는 칼럼에 대해서   ALTER TABLE 명령을 이용해 칼럼의 데이터 유형, 디폴트(Default)값, NOT NULL 제약조건에 대한 변경을 포함할 수 있다.

```sql
ALTER TABLE 테이블명
MODIFY( 칼럼명1 데이터 유형 [DEFAULT 식] [NOT NULL],
        칼럼명2 데이터 유형 ....);
```

칼럼을 변경할 때 몇 가지 사항을 고려해서 변경해야 한다.

- 해당 칼럼의 크기를 늘릴 수는 있지만 줄이지는 못한다. 이는 기존의 데이터가 훼손될 수 있기 때문이다.
- 해당 칼럼이 NULL 값만 가지고  있거나 테이블에 아무 행도 없으면 칼럼의 폭을 줄일 수 있다.
- 해당 칼럼이 NULL 값만을 가지고 있으면 데이터 유형을 변경할 수 있다.
- 해당 칼럼의 DEFAULT 값을 바꾸면 변경 작업 이후 발생하는 행 삽입에만 영향을 미치게 된다.
- 해당 칼럼의 NULL 값이 없을 경우에만 NOT NULL  제약조건을 추가할 수 있다.

4) RENAME COLUMN

아래는 테이블을 생성하면서 만들어졌던 칼럼명을 어떤 이유로 불가피하게 변경해야 하는 경우에 유용하게 쓰일 수 있는 RENAME COLUMN  이다.

```sql
ALTER TABLE 테이블명
RENAME COLUMN 변경해야 할 칼럼명 TO 새로운 칼럼명;
```

5) DROP CONSTRAINT

테이블 생성 시 부여했던 제약조건을 삭제하는 명령어 형태는 다음과 같다.

```sql
ALTER TABLE 테이블명
DROP CONSTRAINT 제약조건명;
```

6) ADD CONSTRAINT

테이블 생성 시 제약조건을 적용하지 않았다면, 생성 이후에 필요에 의해서 제약조건을 추가할 수 있다.다음은 특정 칼럼에 제약조건을 추가하는 명령어 형태이다.

```sql
ALTER TABLE 테이블명
ADD CONSTRAINT 제약조건명 제약조건 (칼럼명);
```

### 4. RENAME TABLE

RENAME 명령어를 사용하여 테이블의 이름을 변경할 수 있다.

```sql
RENAME 변경전 테이블명 TO  변경 후 테이블명;
```

### 5. DROP TABLE

테이블을 잘못 만들었거나 테이블이 더 이상 필요 없을 경우 해당 테이블을 삭제해야 한다. 다음은 불필요한 테이블을 삭제하는 명령이다.

```sql
DROP TABLE 테이블명 [CASCADE CONSTRAINT];
```

CASCADE CONSTRAINT 옵션은 해당 테이블과 관계가 있었던 참조되는 제약조건에 대해서도 삭제한다는 것을 의미한다.

### 6. TRUNCATE TABLE

TRUNCATE TABLE은 테이블 자체가 삭제되는 것이 아니고, 해당 테이블에 들어있던 모든 행동들이 제거되고 저장 공간을 재사용 가능하도록 해제한다. 테이블 구조를 완전히 삭제하기 위해서는 DROP TABLE을 실행하면 된다.

```sql
TRUNCATE TABLE 테이블명;
```

TRUNCATE TABLE의 경우는 테이블 구조는 그대로 유지한 채 데이터만 전부 삭제하는 기능이다.

TRUNCATE는 데이터 구조의 변경 없이 테이블의 데이터를 일괄 삭제하는 명령어로 DML로 분류할 수도 있지만 내부 처리 방식이나  Auto Commit 특성 등으로 인해  DDL로 분류 하였다.

## 제 3절 DML(DATA MANIPULATION LANGUAGE)

### 1. INSERT

테이블에 데이터를 입력하는 방법은 두 가지 유형이 있으며 한 번에 한 건만 입력된다.

```sql
--1. CASE 
INSERT INTO 테이블명 (COLUMN_LIST)
VALUES (COLUMN_LIST에 넣을 VALUE_LIST);



--2. CASE
INSERT INTO 테이블명 
VALUES (전체 COLUMN에 넣을 VALUE_LIST);
```

해당 칼럼명과 입력되어야 하는 값을 서로 1:1로 매핑해서 입력하면 된다.

해당 칼럼의 데이터 유형이 CHAR나 VARCHAR2 등 문자 유형일 경우 『 ' 』(SINGLE QUOTATION)로 입력할 값을 입력한다. 숫자일 경우 『 ' 』 (SINGLE QUOTATION)을 붙이지 않아야 한다.

1. CASE

 첫 번째 유형은 테이블의 칼럼을 정의할 수 있는데, 이때 칼럼의 순서는 테이블의 칼럼 순서와 매치할 필요는 없으며, 정의하지 않은 칼럼은 Default로 NULL값이 입력된다. 단, Primary Key나 Not NULL 로 지정된 칼럼은 NULL이 허용되지 않는다.

```sql
INSERT INTO PLAYER(
PLAYER_ID, PLAYER_NAME, TEAM_ID, POSITION, HEIGHT, WEIGHT, BACK_NO)
VALUES ('2002007', '박지성', 'K07', 'MF', 178, 73, 7);
```

![Untitled 11](https://user-images.githubusercontent.com/56623911/132091461-d6ea40f4-24a0-4a31-8f24-6cd02d58b11c.png)

1. CASE 

두 번째 유형은 모든 칼럼에 데이터를 입력하는 경우로 굳이 COLUMN_LIST를 언급하지 않아도 되지만, 칼럼의 순서대로 빠짐없이 데이터가 입력되어야 한다.

```sql
INSERT INTO player
        VALUES('2002010', '이청용', 'K07', '', 'BlueDragon', '2002', 'MF', '17', NULL, NULL, '1',180,69);
```

![Untitled 12](https://user-images.githubusercontent.com/56623911/132091466-1be8bf60-98e3-4442-9ccd-e896b1571c62.png)


데이터를 입력하는 경우 정의되지 않은 미지의 값인 E_PLAYER_NAME은 두 개의 『 ' '  』SINGLE QUOTATION 을 붙여서 표현하거나, NATION이나 BIRTH_DATE의 경우처럼 NULL이라고 명시적으로 표현할 수 있다.

### 2. UPDATE

입력한 정보 중에 잘못 입력되거나 변경이 발생하여 정보를 수정해야 하는 경우가 발생할 수 있다. 다음은 UPDATE 문장의 기본 형태이다. UPDATE 다음에 수정되어야 할 컬럼이 존재하는 테이블명을 입력하고 SET다음에 수정되어야 할 칼럼명과 해당 칼럼에 수정되는 값으로 수정이 이루어진다.

```sql
UPDATE 테이블명
SET 수정되어야 할 칼럼명 = 수정되기를 원하는 새로운 값;
```

```sql
--예제 : 선수테이블의 백넘버를 일괄적으로 99로 수정한다.
UPDATE PLAYER
SET BACK_NO = 99;
480개의 행이 수정되었다.
```

```sql
--예제 : 선수 테이블의 포지션을 일괄적으로 'MF'로 수정한다.
UPDATE PLAYER
SET POSITION = 'MF';
480개의 행이 수정되었다.
```

### 3. DELETE

```sql
DELETE [FROM] 삭제를 원하는 정보가 들어있는 테이블명;
```

```sql
--예제
DELETE FROM PLAYER;
--480개의 행이 삭제되었다.
```

※참고

데이터베이스는  DDL 명령어와 DML 명령어를 처리하는 방식에 있어서 차이를 보인다.

DDL(CREATE, ALTER, RENAME, DROP) 명령어인 경우에는 직접 데이터베이스의 테이블에 영향을 미치기 때문에 DDL명령어를 입력하는 순간 명령어에 해당하는 작업이 즉시(Auto Commit)완료된다.

DML(INSERT, UPDATE, DELETE, SELECT)명령어의 경우, 조작하려는 테이블을 메모리버퍼에 올려놓고 작업을 하기 때문에 실시간으로 테이블에 영향을 미치는 것은 아니다.
따라서 버퍼에서 처리한 DML명령어가 실체 테이블에 반영되기 위해서는 COMMIT 명령어를 입력하여 TRANSACTION을 종료해야 한다.

※ 테이블의 전체 데이터를 삭제하는 경우

시스템 활용 측면에서는 삭제된 데이터르 로그로 저장하는 DELETE TABLE보다는 시스템 부하가 적은 TRUNCATE TABLE을 권고한다.
단, TRUNCATE TABLE의 경우 삭제된 데이터의 로그가 없으므로 ROLLBACK이 불가능하므로 주의해야 한다.

### 4. SELECT

사용자가 입력한 데이터는 언제라도 조회가 가능하다. 앞에서 입력한 자료들을 조회해보는 SQL문다음과 같다.

```sql
SELECT [ALL/DISTINCT] 보고 싶은 칼럼명, 보고 싶은 칼럼명 ...
FROM  해당 칼럼들이 있는 테이블명;

-ALL : Default 옵션이므로 별도로 표시하지 않아도 된다.
       중복된 데이터가 있어도 모두 출력한다.
-DISTINCT : 중복된 데이터가 있는 경우 1건으로 처리해서 출력한다.
```

예제) 조회하기를 원하는 칼럼명을 SELECT 다음에 콤마 구분자(,)로 구분하여 나열하고, 
FROM 다음에 해당 칼럼이 존재하는 테이블명을 입력하여 실행시킨다. 입력한 선수들의 데이터를 조회한다.

```sql
SELECT PLAYER_ID, PLAYER_NAME, TEAM_ID, POSITION, HEIGHT, WEIGHT, BACK_NO
FROM PLAYER;
```

- ALL 옵션

```sql
--예제
SELECT ALL POSITION
FROM PLAYER;
```

- DISTINCT 옵션

```sql
--예제
SELECT DISTINCT POSITION
FROM PLAYER;
```

- WILDCARD 사용하기

해당 테이블의 모든 칼럼 정보를 보고 싶을 경우에는 와일드 카드로 에스터리스크(*)를 사용하여 조회할 수 있다.

```sql
SELECT * 
FROM  테이블명;
```

```sql
--예제
SELECT *
FROM PLAYER;
```

- ALIAS  부여하기

조회된 결과에 일종의 별명(ALIAS, ALIASES)을 부여해서 칼럼 레이블을 변경할 수 있다. 칼럼 별명( ALIAS)에 대한 사항을 정리하면 다음과 같다.

-칼럼명 바로 뒤에 온다.

-칼럼명과 ALIAS 사이에 AS, as 키워드를 사용할 수 있다.(option)

-이중 인용부호(Double quotation)는 ALIAS가 공백, 특수문자를 포함할 경우와 대소문자 구분이 필요할 경우 사용된다.

```sql
--예제 
SELECT PLAYER_NAME AS 선수명, POSITION AS 위치, HEIGHT AS 키, WEIGHT AS 몸무게
FROM PLAYER;
```

※ 참고 

칼럼 별명을 적용할 때 별명 중간에 공백이 들어가는 경우 『 "  "』를 사용해야 한다. 

### 5. 산술 연산자와 합성 연산자

- 산술 연산자

-산술 연산자는 NUMBER와 DATE 자료형에 대해 적용되며 일반적으로 수학에서의 사칙 연산과 동일

-우선순위를 위한 괄호 적용이 가능

![Untitled 13](https://user-images.githubusercontent.com/56623911/132091471-d8a65b75-9c7e-40b3-bd7e-4476f08af91a.png)


```sql
--예제 : 선수들의 키에서 몸무게를 뺀 값을 알아본다.
SELECT PLAYER_NAME 이름, HEIGHT - WHIGHT "키-몸무게"
FROM PLAYER;
```

```sql

--예제 : 선수들의 키와 몸무게를 이용해서 BMI 비만지수를 측정한다.
SELECT PLAYER_NAME 이름, ROUND(WEIGHT/((HEIGHT/100)*(HEIGHT/100)),2) "BMI 비만지수"
FROM PLAYER;
```

- 합성(CONCATENATION)연산자

문자와 문자를 연결하는 합성(CONCATENATION) 연산자를 사용하면 별도의 프로그램 도움 없이도 SQL  문장만으로도 유용한 리포트를 출력할 수 있다. 

- 합성(CONCATENATON)연산자의 특징

-문자와 문자를 연결하는 경우 2개의 수직 바( | | ) 에 의해 이루어 진다. (Oracle)

-CONCAT( string1, string2) 함수를 사용할 수 있다.

-칼럼과 문자 또는 다른 칼럼과 연결시킨다.

-문자 표현식의 결과에 의해 새로운 칼럼을 생성한다.

```sql
--예제
SELECT PLAYER_NAME || '선수,' || HEIGHT || 'cm,' || WEIGHT || 'kg' 체격정보
FROM PLAYER;
```

![Untitled 14](https://user-images.githubusercontent.com/56623911/132091484-24a8906f-3063-4546-84bb-914777d3cc47.png)


## 제 4절 TCL(TANSACTION CONTROL LANGUAGE)

### 1. 트랜잭션 개요

### 2. COMMIT

### 3. ROLLBACK

### 4. SAVEPOINT

## 제 5절 WHERE 절

### 1. WHERE 조건절 개요

### 2. 연산자의 종류

### 3. 비교 연산자

### 4. SQL

### 5. 논리 연산자

### 6. 부정 연산자

### 7. ROWNUM, TOP 사용

## 제 6절 함수(FUNCTION)

### 1. 내장 함수(BUILT-IN FUNTION) 개요

### 2. 문자형 함수

### 3. 숫자형 함수

### 4. 날짜형 함수

### 5. 변환형 함수

### 6. CASE 표현

### 7. NULL 관련 함수

## 제 7절 GROUP BY, HAVING 절

### 1. 집계 함수(Aggregate Function)

### 2. GROUP BY 절

### 3. HAVING 절

### 4. CASE 표현을 활용한 월별 데이터 집계

### 5. 집계 함수와 NULL 처리

## 제 8절 ORDER BY  절

### 1. ORDER BY  정렬

### 2. SELECT 문장 실행 순서

### 3. Top N 쿼리

### 제 9절 조인(JOIN)

### 1. JOIN 개요

### 2. EQUI JOIN

### 3. Non EQUI JOIN

### 4. 3개 이상 TABLE JOIN
