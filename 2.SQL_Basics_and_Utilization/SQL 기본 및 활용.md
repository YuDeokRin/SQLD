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


### 2. CREATE TABLE



### 3. ALTER TABLE

### 4. RENAME TABLE

### 5. DROP TABLE

### 6. TRUNCATE TABLE

## 제 3절 DML(DATA MANIPULATION LANGUAGE)

### 1. INSERT

### 2. UPDATE

### 3. DELETE

### 4. SELECT

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
