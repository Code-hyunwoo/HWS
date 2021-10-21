# :boom: homework

---

​																																

### 1. MTV

MTV가 무엇의 약자이며 Django에서 각각 어떤 역할을 하고 있는지 작성하시오.

​																										

**MTV(Model-Template-View)**

**Model**

**MVC패턴의 모델에 대응되며 DB에 저장되는 데이터**

**Template**

**MVC패턴의 뷰에 대응되며 유저에게 보여지는 화면**

**View**

**MVC패턴의 컨트롤러에 대응되며 요청에 따라 적절한 로직을 수행하여 결과를 템플릿으로 렌더링하여 응당**

​																											

​																

### 2. 404 Page not found

기본적으로 '/' 페이지에 접속하는 경우 index.html를 렌더링하고자 한다.

아래 빈칸에 알맞은 코드를 작성하시오.



```python
from django.contrib import admin
from django.urls import path, include
from __(a)__ import __(b)__

urlpatterns = [
    path('admin/', admin.site.urls),
    path('articles/', include('articles.urls')),
    path('', __(c)__),
]

```

**a = articles** 

**b = views**

**c = views.index**

​																								

​																							

### 3. templates and static

Django 프로젝트는 기본적으로 render할 html과 같은 template 파일과 css, js와 같은 static 파일을 

앱 폴더 내부의 templates와 static 이름의 폴더에서 찾는다. 

만약 해당 위치가 아닌 임의의 위치에 파일을 위치 시키고 싶으면 (a) 파일의 (b) 와 (c) 라는 변수에 담긴 

리스트의 요소를 정의하면 된다.



**a = settings.py**

**b = STATIC_URL**

**c = BASE_DIR**

​											



### 4. migration

Django에서 선언한 Model을 Database에 반영하는 과정에서 사용하는 명령어에 대한 설명이다.

각 설명에 해당하는 명령어를 작성하시오.

1) 마이그레이션 생성      **makemigrations**

2) 마이그레이션 DB 반영 여부 확인     **showmigrtaions**

3) 마이그레이션에 대응되는 SQL문 출력     **sqlmigrate**

4) 마이그레이션 파일의 내용을 DB에 최종 반영      **migrate**

   ​																												

### 5. ModelForm True or False

​																	

1. POST와 GET 방식은 의미론상의 차이이며 실제 동작 방식은  동일하다.  - **F**

2. ModelForm과 Form Class의 핵심차이는 Model의 정보를 알고있는지의 여부이다. -  **T**

3. AuthenticationForm은 User 모델과 관련된 정보를 이미 알고 있는 ModelForm으로 구성되어 있다. -  **F**

4. ModelForm을 사용할 때 Meta 클래스에 fields 관련 옵션은 반드시 작성해야 한다. - **T**

   ​																															

   ​																																				

### 6. media 파일 경로

사용자가 업로드한 파일이 저장되는 위치를 Django 프로젝트 폴더(crud) 내부의 /uploaded_files로 

지정하고자 한다. 이 때, settings.py에 작성해야 하는 설정 2가지를 작성하시오.

​									

**MEDIA_ROOT**

**MEDIA_URL**

​												

### 7. DB True or False

아래의 설명을 읽고 T/F 여부를 작성하시오.

1. RDBMS를 조작하기 위해서 SQL문을 사용한다. - **T**

2. SQL에서 명령어는 반드시 대문자로 작성해야 동작한다. - **F**

3. 일반적인 SQL문에서는 세미콜론( ; )까지를 하나의 명령어로 간주한다. - **T**

4. SQLite에서 .tables, .headers on과 같은 dot( . )로 시작하는 명령어는 SQL문이 아니다. - **F**

5. 하나의 데이터베이스 안에는 반드시 한 개의 테이블만 존재해야 한다. - **F**

   ​																					

### 8. on_delete

게시글과 댓글의 관계에서 댓글이 존재하는 게시글은 삭제할 수 없도록 __(a)__에 들어갈 코드를 작성하시오. 

그리고 이러한 설정이 되어있는 상황에서 Article 객체를 삭제하려고 할 때 발생하는 오류를 작성하시오.

```python
class Comment(models.Modle):
    content = models.TextField()
    article = models.ForeignKey(Article, on_delete=models.__(a)__)
```

**(a) = protect**

**Error = protected Error**

​																																										

### 9. Like in models

Article 모델과 User 모델을 M:N 관계로 설정하여 ‘좋아요’ 기능을 구현하려고 한다. 

(a)__와 __(b)에 들어갈 내용을 작성하시오. 

```python
from django.db import models
from django.conf import settings

# Create your models here.
class Article(models.Model):
    content = models.TextField()
    user = models.ForeignKey(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)
    like_users = models.__(a)__(settings.AUTH_USER_MODEL,__(b)__='like_articles')
```

**a = ManyToManyField**

**b = related_name**

​																							

### 10. Follow in models

follow 기능을 구현하기 위해 accounts app의 models.py에 아래와 같은 모델을 작성하였다. 

Migration 작업 이후에 Database에 만들어지는 중개 테이블의 이름을 작성하고 

이 테이블의 id를 제외한 컬럼 이름을 각각 작성하시오.

```python
from django.db import models
from django.contrib.auth.models import AbstractUser

# Create your models here.
class User(AbstractUser):
    followings = models.ManyToManyField('self', symmetrical=False, related_name='followers')
```

**테이블 이름 :** **accounts_user**

**컬럼 : password, last_login, is_superuser, username, first_name, last_name, email, is_staff, is_active, date_joined**

​																																		
