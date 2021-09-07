# :boom: Workshop

---

​																																																														

### 1. Read

![image-20210907153635994](0907_workshop.assets/image-20210907153635994.png)

```python
{% extends 'base.html' %}

{% block content %}

    <h2 class='fw-bold'>Articles</h2>
    <a href="{%url "articles:create"%}" class='text-decoration-none'>NEW</a>
    <hr>
    <div class="row row-cols-1 row-cols-sm-2 row-cols-md-3 g-2">
        {% for article in articles %}
        <div class="col">
            <div class="card text-center" >
                <h2 >{{article.title}}</h2>
                <a href="{% url 'articles:detail' article.pk%}" class='text-decoration-none'><h3>{{article.content}}</h3></a>
                <img src="{{ article.poster }}" alt="오류">
                <hr>
            </div>
        </div>        
        {% endfor %}    
    </div>
{% endblock content %}



#views
def index(request):
    articles = Article.objects.all()
    context = {
        'articles':articles,
    }
    return render(request, 'articles/index.html',context)
```

​																																						

### 2. Create

![image-20210907153914944](0907_workshop.assets/image-20210907153914944.png)

```python
{% extends 'base.html' %}
{% load bootstrap5 %}

{% block content %}
<h2 class='fw-bold'>New</h2>
<form action="{%url 'articles:create' %}"method = 'POST'>
    {% csrf_token %}
    {% bootstrap_form form %}
    <input type="submit" value="작성">
</form>
<a href="{%url 'articles:index'%}" class='text-decoration-none'>BACK</a>
{% endblock content %}


#views
@require_http_methods(["GET", "POST"])
def create(request):
    if request.method =='POST':
        form = ArticleForm(request.POST)
        if form.is_valid():
            form.save()
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

![image-20210907154057806](0907_workshop.assets/image-20210907154057806.png)



```python
{% extends 'base.html' %}
{% block content %}
    <h2 class='fw-bold'>Detail</h2>
    <hr>
    <h2>글 제목: {{article.title}}</h2>
    <h2>글 내용: {{article.content}}</h2>
    <a href="{{article.poster}}"><img src="{{article.poster}}" style="width:400px;height:500px"alt="오류"></a>
    <p>작성일: {{article.created_at|date:'Y년 M j일 D A h:i'}}</p>
    <p>수정일: {{article.updated_at|date:'Y년 M j일 D A h:i'}}</p>
    <a href="{%url 'articles:update' article.pk%}" class='text-decoration-none'>수정하기</a> <br>
    <a href="{%url 'articles:delete' article.pk%}" class='text-decoration-none'>삭제하기</a> <br>
    <hr>
    <a href="{%url 'articles:index' %}" class='text-decoration-none'>돌아가기</a>

{% endblock content %}


#views
def detail(request, pk):
    article = Article.objects.get(pk=pk)

    context = {
        'article':article,
    }
    return render(request, 'articles/detail.html', context)
```

​																													

### 4. Update

![image-20210907154228722](0907_workshop.assets/image-20210907154228722.png)

```python
{% extends 'base.html' %}
{% load bootstrap5 %}

{% block content %}
    <h2 class='fw-bold'>Edit</h2>
    <form action="{%url 'articles:update' article.pk%}" method='POST'>
        {% csrf_token %}
        {% bootstrap_form form %}
        <input type="submit" value="수정">
    </form>

    <a href="{%url 'articles:detail' article.pk%}" class='text-decoration-none'>상세페이지로 이동</a>
{% endblock content %}


#views

def update(request, pk):
    article = Article.objects.get(pk=pk)

    if request.method == 'POST':
        form = ArticleForm(request.POST, instance=article)
        if form.is_valid():
            article = form.save()
            return redirect('articles:detail', article.pk)
    
    else:
        form = ArticleForm(instance=article)
    context = {
        'article': article,
        'form' : form,
    }
    return render(request, 'articles/update.html', context)
```

​																	

### 5. Delete

```python
def delete(request, pk):
    article = Article.objects.get(pk=pk)
    article.delete()

    return redirect('articles:index')
```

