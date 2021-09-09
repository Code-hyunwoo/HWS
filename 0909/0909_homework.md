# :boom: Homework

---



## 1.Compiled Bootstrap

CSS, JS 파일을 다운로드 받아 Django 프로젝트에 Static 파일로 추가하시오.

부트스트랩이 적용되기 위해 작성해야 할 코드를 제출하시오.

​																								

```python
프로젝트 밑에 static 폴더 생성

# settings.py

STATICFILES_DIRS = [BASE_DIR/'static'] 추가

/project/static/밑에 다운로드 받은 CSS, JS 파일 가져오기
```

​																															

```python
{% extends 'base.html' %}
{% load static %}

{% block css %}
    <link rel="stylesheet" href="{% static 'css/bootstrap.css' %}">
{% endblock css %}

{% block content %}
<h1 class="text-info">Articles Home</h1>
<hr>
<a href="{% url 'articles:create' %}">[NEW]</a>
<br><br>
{% for article in articles %}
    <h2>{{article.title}}</h2>
    <a href="{% url 'articles:detail' article.pk %}">상세보기</a>
    <hr>
{% endfor %}
<img src="{% static 'articles/cat.png' %}" alt="">
{% endblock content %}
```

​											