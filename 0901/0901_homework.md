# :boom: Homework

---

​																		

### 1. Model 반영하기

"Django가 Model에 생긴 변화를 DB에 반영하는 방법"을 뜻하는 용어를 작성하시오.

​											

**Migrations**

​														

### 2. Model 변경사항 저장하기

1. 위에서 작성한 Model의 변경사항을 저장하기 위한 명령어를 작성하시오.

   ​													

​	**makemigrations**

```python
$ python manage.py makemigrations
```

​																

2. 이로 인해 생성된 마이그레이션 파일에 대응되는 SQL문을 확인하기 위한 명령어와 출력결과를 작성하시오.

   ​																																

​	**sqlmigrate**

```python
$ python manage.py sqlmigrate articles 0001

BEGIN;
--
-- Create model Article
--
CREATE TABLE "articles_article" ("id" integer NOT NULL PRIMARY KEY AUTOINCREMENT, "title" varchar(10) NOT NULL, "content" text NOT NULL);
COMMIT;
```

​																		

### 3. Python shell

Django에서 사용 가능한 모듈 및 메서드를 대화식 python shell에서 사용하려고 할 때, 

어떤 명령어를 통해 해당 shell을 실행할 수 있는지 작성하시오.

​												

**shell_plus**

```python
$ python manage.py shell_plus
```

​																							

### 4. Django Model Field

Django에서 Model을 정의할 때 사용할 수 있는 필드 타입을 5가지 이상 작성하시오.

​																						

**AutoField** =  ID로 사용 가능한 자동으로 증가하는 필드. 직접 사용할 필요는 없다.

**CharField** =  길이의 제한이 있는 문자열을 넣을 때 사용. max_length가 필수 인자

**TextField** = 글자 수가 많을 때 사용 max_length는 옵션

**DateField** = datetime.date 인스턴스에 의해 표현되는 날짜.

-  **DateField.auto_now** = 객체가 저장될 때마다 매번 자동으로 필드를 현재시간으로 설정
-  **DateField.auto_now_add** = 객체가 처음 생성될 때 자동으로 현재시간이 설정. 생성의 타임스탬프

**URLField**

**TimeField**

**BinaryField**

