# :boom: Homework

---



​																													

### 1. 아래의 설명을 읽고 T/F 여부를 작성하시오.

- URI 는 정보의 자원을 표현하고, 자원에 대한 행위는 HTTP Method로 표현한다.
  - **T : URI (Uniform Resource Indentifier) 와 명령어를 통해 RESTful 하게 나타낼 수 있어야 한다.**



- HTTP Method는 GET 과 POST 두 종류 뿐이다.
  - **F: GET, POST, PUT, DELETE 가 있다.**



- https://www.fifia.com/worldcup/teams/team/43822/create/는 계층 관계를 잘 표현한 RESTful한 URI 라고 할 수 있다. 

  - **F:  REST URL은 생성하는 단계에서 create를 별도로 명시하지 않는다.**

   

### 2. 다음의 HTTP status code의 의미를 간략하게 작성하시오.



- 200 - **Success(OK), 요청이 성공적으로 진행됨**
- 400 - **Bad Request, 잘못된 메시지 요청, 변조된 라우팅 등을 통해 요청을 처리할 수 없는 경우.**
- 401 - **Unauthorized, 권한이 인증되지 않음**
- 403 - **Forbidden, 요청 권한이 없음**
  - 401과 403은 비슷하나 그 차이를 알아두어야 할 필요가 있다.
  - `401` - '당신은 인증되지 않았습니다.' or '로그인(인증) 정보를 잘 못 입력하여 권한이 없습니다.'
  - `403` - '당신이 누구인지 알고 뭘 요청하는지 알지만, 당신에게는 승인되지 않는 리소스입니다.'
- 404 - **Not Found, 요청받은 리소스를 찾을 수 없음.**
- 500 - **Interner Server Error, 서버 관리자가 잘못함... 요청을 처리하는 과정에서 예상치 못한 상황 발생**



​																							

### 3. 아래의 모델을 바탕으로 ModelSerializer인 StudentSerializer 

### class를 작성하시오.



```python
class Student(models.Model):
    name = models.TextField()
    age = models.CharField(max_length=20)
    address = models.TextField()
```



```python
from rest_framework import serializers
from .models import Student

class StudentSerializer(serializers.serializer):
    class Meta:
        model = Student
        fields = ['name', 'address']
```



### 4. Serializer의 의미를 DRF 공식문서를 참고하여 간단하게 설명하시오.

**직렬화.**

**데이터 구조나 객체 상태를 동일하거나 다른 컴퓨터 환경에 저장하고,** 

**나중에 재구성할 수 있는 포맷으로 변환하는 과정**

