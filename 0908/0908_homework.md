# :boom: Homework

---

​																

### **1. static 파일 기본 설정**

개발자가 작성한 CSS파일이나 미리 업로드한 이미지 파일 등이 Django 프로젝트 폴더 내부 assets 폴더에 있다.

이처럼 기존 static 파일 경로 외에 추가 경로를 정의해야 할 경우 

settings.py에 추가해야 하는 설정과 값을 작성하시오.

​						

1. **django.contrib.staticfiles가 INSTALLED_APPS 포함**

2. **settings.py에서 STATIC_URL 정의**

   ​																				

### 2. media 파일 기본 설정

사용자가 업로드 파일의 저장치를 Django 프로젝트 폴더 내부 uploaded_files 폴더로 지정하고자 한다.

이 때, settings.py에 작성해야 하는 설정과 값을 모두 작성하시오.

​																										

**STATIC_ROOT = BASE_DIR / 'staticfiles'** 

**STATIC_URL = '/static/'** 

**STATICFILES_DIRS = [  BASE_DIR / 'static', ]**

​																											

### 3. Serving files uploaded by uesr during development

settings.py에 MEDIA_URL 값이 작성되어 프로젝트에 사용자가 업로드한 파일이 업로드 될 수 있게 되었다.

하지만 사용자가 실제 웹 페이지 내에서 이 파일을 조회할 수 있도록 하기 위해선 

업로드 된 파일에 대한 URL을 생성해주는 설정이 필요하다.

다음 코드를 작성하시오.

​																																	

```PYTHON
from django.conf import __(a)__
from __(b)__ import __(c)__

urlpatterns = [
    
] + static (__(d)__)
```

**(a) settings**

**(b) django.conf.urls.static**

**(c) static**

**(d) settings.MEDIA_URL, document_root=settings.MEDIA_ROOT**

​																							

### 4. Media file with HTML input

```python
<form action="#" method="POST" enctype="__(a)__">
	<label for="data">UPLOAD: </label>
    <input type="file" name="data" id="data" accept="__(b)__">
    <input type="submit" value="submit">
</form>
```

​																

- <input type="file"> 태그를 사용할 경우 반드시 사용해야 하는 enctype 속성의 값(a)를 작성하시오.

  ​																				

  **(a) multipart/form-data**

  ​																		

- accept 속성은 파일 업로드 제어에서 선택할 수 있는 파일 유형을 정의하며 속성이며, input 태그의 type이 file 경우에만 유효하다. 예를 들어, "표준 비디오 형식 뿐만 아니라 pdf 형식도 받을 수 있어야 한다." 라고 할 때,
  빈칸 (b)에 들어갈 알맞은 속성 값을 작성하시오.

  ​																														

​		**(b) video/*, . pdf**

​								