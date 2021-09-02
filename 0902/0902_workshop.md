# :boom: Workshop

---

​																				

​																									

## 1. READ

​																										

![image-20210902160214526](0902_workshop.assets/image-20210902160214526.png)

```python
{% extends 'base.html' %}

{% block content %}
<h1 class="fw-bold">INDEX</h1>
<a href="{% url 'articles:new' %}" class="text-decoration-none">NEW</a>
<br>
<br>
{% for article in articles %}
<h3>글 제목: {{ article.title }}</h3>
<h4>글 내용: {{ article.content }}</h4>

<a href="{% url 'articles:detail' article.pk %}" class="text-decoration-none">DETAIL</a>
<hr>
{% endfor %}

{% endblock content %}
```

​									

## 2. Create

​																							

![image-20210902160338924](0902_workshop.assets/image-20210902160338924.png)

```python
{% extends 'base.html' %}

{% block content %}
<h1 class="fw-bold">NEW</h1>
<form action="{% url 'articles:create' %}" method="POST">
    {% csrf_token %}
    <label for="title">TITLE:</label>
    <input type="text" id='title' name='title'><br><br>
    <label for="content">CONTENT:</label>
    <textarea name="content" id="content" cols="30" rows="10"></textarea><br>
    <input type="submit" value="작성">
</form>

<a href="{% url 'articles:index' %}" class="text-decoration-none">BACK</a>
{% endblock content %}
```

​																									

## 3. DETAIL



![image-20210902171533500](0902_workshop.assets/image-20210902171533500.png)

```python
{% extends 'base.html' %}

{% block content %}
<h2 class="fw-bold">DETAIL</h2>
<hr>
<h3>게시글 제목: {{article.title}}</h3>
<p>게시글 내용:{{article.content}}</p>
<p>작성일:{{article.created_at}}</p>
<p>수정일:{{article.updated_at}}</p>
<br>
<div class="d-flex flex-row">
<a href="{% url 'articles:edit' article.pk %}" class='btn btn-primary m-1' >EDIT</a>

<form action="{% url 'articles:delete' article.pk %}" method='POST'>
{% csrf_token %}
<button class="btn btn-danger m-1">DELETE</button>
</form>
</div>
<br>
<a href="{% url 'articles:index' %}" class="text-decoration-none"> BACK </a>
{% endblock content %}



def delete(request,pk):
    article= Article.objects.get(pk=pk)
    if request.method == 'POST':
        article.delete()
        return redirect('articles:index')
    else:
        return redirect('articles:detail', article.pk)

```

​																			

​					![image-20210902175458833](0902_workshop.assets/image-20210902175458833.png)

```python
{% extends 'base.html' %}

{% block content %}
<h2 class="fw-bold">DETAIL</h2>
<hr>
<h3>게시글 제목: {{article.title}}</h3>
<p>게시글 내용:{{article.content}}</p>
<p>작성일:{{article.created_at}}</p>
<p>수정일:{{article.updated_at}}</p>
<br>

<a href="{% url 'articles:edit' article.pk %}" class="text-decoration-none" >EDIT</a>

<a href="{% url 'articles:delete' article.pk %}" class="text-decoration-none">DELETE</a>

<br>
<a href="{% url 'articles:index' %}" class="text-decoration-none"> BACK </a>
{% endblock content %}



def delete(request,pk):
    article= Article.objects.get(pk=pk)    
    article.delete()
    
    return redirect('articles:index')
```





​									

## 4. Update

​													

![image-20210902161849984](0902_workshop.assets/image-20210902161849984.png)

```python
{% extends 'base.html' %}

{% block content %}
<h1 class="fw-bold">EDIT</h1>
<form action="{% url 'articles:update' article.pk %}" method="POST">
    {% csrf_token %}
    <label for="title">TITLE:</label>
    <input type="text" id='title' name='title' value='{{ article.title}}'><br><br>
    <label for="content">CONTENT:</label>
    <textarea name="content" id="content" cols="30" rows="10">{{article.content}}</textarea><br>
    <input type="submit" value="수정">
</form>

<a href="{% url 'articles:index' %}" class="text-decoration-none">BACK</a>

{% endblock content %}
```

​											

## 5. Delete

​					

```python
def delete(request,pk):
    article= Article.objects.get(pk=pk)
    if request.method == 'POST':
        article.delete()
        return redirect('articles:index')
    else:
        return redirect('articles:detail', article.pk)
```



