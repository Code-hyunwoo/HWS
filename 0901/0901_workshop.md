# :boom: ​Workshop

---





### base.html



```python
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.0/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-KyZXEAg3QhqLMpG8r+8fhAXLRk2vvoC2f3B09zVXn8CA5QIVfZOJ3BCsw2P0p/We" crossorigin="anonymous">
  <title>Document</title>
</head>
<body>
  <div class="container">
    {% block content %}
    {% endblock %}
  </div>
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.0/dist/js/bootstrap.bundle.min.js" integrity="sha384-U1DAWAznBHeqEIlVSCgzq+c9gqGAJn5c/t99JyeKa9xxaYpSvHU5awsuZVVFIhvj" crossorigin="anonymous"></script>
</body>
</html>		
```

​																			

### Read

```python
{% extends 'base.html' %}

{% block content %}
  <h1>INDEX</h1>
  <br>
  <a href="" >NEW</a>
  <br>
  <br>
  
    <h3>제목 : 게시글 제목</h3>
    <h5>내용 : 게시글 내용</h5>
    <br>
  <a href="{% url 'articles:new' %}">DETAIL</a>
{% endblock %}
```

​				

​															

### Create

```python
{% extends 'base.html' %}

{% block content %}
  <h1>NEW</h1>
  <form action="{% url 'articles:create' %}" method="POST">
    {% csrf_token %}
    <label for="title">TITLE: </label>
    <input type="text" id="title" name="title">
    <br>

    <label for="content">CONTENT: </label>
    <textarea name="content" id="content" cols="30" rows="10"></textarea>
    <br>
    <input type="submit" value="작성">
  </form>
  <a href="{% url 'articles:index' %}">BACK</a>
{% endblock %}
```

