# :boom: Workshop

---

​																																																						

### 1. READ

​																																				

![image-20210909171001601](0909_workshop.assets/image-20210909171001601.png)

```python
{% extends 'base.html' %}
{% load static %}
{% block css %}
    <link rel="stylesheet" href="{% static 'css/style.css' %}">
{% endblock css %}   

{% block content %}
    <img src="{% static 'articles/black.jpg' %}" alt="image" style="width:500px;height:300px">
<br>
<br>
<h1>Articles</h1>
<a href="{% url 'articles:create' %}" class='text-decoration-none'>CREATE</a>
<hr>
{% for article in articles  %}
<p> 글 번호:{{article.pk}}</p>
<p> 글 제목:{{article.title}}</p>
<p> 글 내용:{{article.content}}</p>
<a href="{%url 'articles:detail' article.pk%}"class='text-decoration-none'>DETAIL</a>
<hr>
{% endfor %}

{% endblock content %}       
```

​											

### 2. Create

​															

![image-20210909171437847](0909_workshop.assets/image-20210909171437847.png)

```python
#create.html
{% extends 'base.html' %}
{% load bootstrap5 %}

{% block content %}
<h1 class='fw-bold'>Create</h1>
<form action="{% url 'articles:create'%}"method='POST' enctype='multipart/form-data'>
    {% csrf_token %}
    {% bootstrap_form form %}
    <input type="submit" value="제출"> 
</form>
<br>
<a href="{%url 'articles:index' %}" class='text-decoration-none'>BACK</a>
{% endblock content %}
```

```python
#views.py

def create(request):
    if request.method == 'POST':
        form = ArticleForm(request.POST, request.FILES)
        if form.is_valid():
            form.save()
            messages.add_message(request, messages.SUCCESS, '게시글이 작성되었습니다.')
            # messages.info(request,'게시글이 작성되었습니다.')
            return redirect('articles:index')
    else:
        form = ArticleForm()
    context = {
        'form' : form,
    }

    return render(request, 'articles/create.html', context)
```

​																											

### 3. Detail

​																			

![image-20210909180845488](0909_workshop.assets/image-20210909180845488.png)

```python
#detail.html
{% extends 'base.html' %}

{% block content %}

<p> 글 제목 : {{article.title}}</p>
<p> 글 내용 : {{article.content}}</p>
{% if article.image_thumb %}
<img src="{{ article.image_thumb.url }}" alt="img">
{% endif %}
<p>작성 시간: {{ article.created_at|date:"SHORT_DATE_FORMAT" }}</p>
<p>수정 시간: {{ article.updated_at|date:"M, j, Y" }}</p>
<hr>
<a href="{%url 'articles:update' article.pk%}" class='btn btn-primary'>UPDATE</a>
<a href="{%url 'articles:delete' article.pk%}" class='btn btn-danger'>DELETE</a> <br>
<a href="{%url 'articles:index'%}" class = 'text-decoration-none'>back</a>
{% endblock content %}
```

​											

### 4. UPDATE

​																				

![image-20210909182050772](0909_workshop.assets/image-20210909182050772.png)

```python
#update.html
{% extends 'base.html' %}
{% load bootstrap5 %}

{% block content %}
<h1 class='fw-bold'> UPDATE </h1>
<form action="{% url 'articles:update' article.pk%}"method='POST' enctype='multipart/form-data'>
    {% csrf_token %}
    {% bootstrap_form form %}
    <input type="submit" value="OK" class='btn btn-primary'>
    <button class='btn btn-primary'><a href="{%url 'articles:detail' article.pk%}" class='text-white text-decoration-none'>Cancel</a></button>
</form>
<hr>
<a href="{%url 'articles:index'%}" class='text-decoration-none'>back</a>
{% endblock content %}

#view.py

def update(request,pk):
    article = Article.objects.get(pk=pk)
    if request.method == 'POST':
        form = ArticleForm(request.POST, request.FILES, instance=article)
        if form.is_valid():
            article = form.save()
            return redirect('articles:detail', article.pk)
    
    else:
        form = ArticleForm(instance=article)
    context = {
        'article': article,
        'form': form,
    }
    return render(request, 'articles/update.html', context)
```

​																							

### 5. Delete	

```python
def delete(request, pk):
    article = Article.objects.get(pk=pk)
    article.delete()
    # messages.add_message(request, messages.WARNING, '게시글이 삭제되었습니다.')
    messages.warning(request, '게시글이 삭제되었습니다.')
    return redirect('articles:index')							
```

​																	

​																				