# :boom: Homework

---

​											

### 1. SQL 용어 및 개념

아래의 보기에서 각 문항의 설명에 맞는 용어를 고르시오.

​	기본키  테이블  스키마  레코드  컬럼

​											

1) 관계형 데이터베이스에서 구조와 제약 조건에 관련한 전반적인 명세를 기술 한 것    **스키마**
2) 열과 행의 모델을 사용해 조직된 데이터 요소들의 집합     **테이블**
3) 고유한 데이터 형식이 지정되는 열   **컬럼**
4) 단일 구조 데이터 항목을 가리키는 행  **레코드** 

5. 각 행의 고유값  **기본키**



​																			

### 2. SQL 문법

다음 중 DML이 아닌 것을 고르시오.

​																													

1. CREATE

2. UPDATE

3. DELETE

4. SELETE

   ​																

**1.CREATE  CREATE는 DDL이고, INSERT가 DML이다.**

​											

### 3. Relational DBMS

RDBMS의 개념적 정의와 이를 기반으로 한 DB-Engine의 종류 세 가지 이상 작성하시오.

​																					

**관계형 모델을 기반으로 하는 데이터베이스 관리시스템**

**MySQL,  SQLite, PostgreSQL, ORACLE, MS SQL**

​																									

### 4. INSERT INTO

다음과 같은 스키마를 가지는 테이블이 있을 때,

아래의 보기 중 틀린 문장을 고르시오.

```python
CREATE TABLE classmates(
    name TEXT,
    age INT,
    address TEXT
)
```

​																				

```python
(1) INSERT INTO classmates (name, age, address) VALUES('홍길동',20,'seoul');
(2) INSERT INTO classmates VALUES('홍길동',20,'seoul');
(3) insert into classmates values(address='seoul', age=20, name='홍길동');
(4) insert into classmates (address, age, name) values('seoul', 20, '홍길동');
```

**(3)**  **Error: no such column: address 라고 뜨면서 에러남**

​																						

### 5. 와일드카드 문자	

SQL에서 사용가능한 와일드카드 문자인 %와 _을 비교하여 작성하시오.



**% 는 이 자리에 문자열이 있을 수도, 없을 수도 있다.**

**_는 반드시 이 자리에 한 개의 문자가 존재해야 한다.**

