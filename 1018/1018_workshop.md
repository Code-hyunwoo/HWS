# :boom: Workshop

---



### Django Project



1) 댓글 기능을 구현한다.

2) 각 게시글에는 여러 댓글이 작성될 수 있다.

3) 댓글 모델은 댓글내용, 작성시간, 수정시간 컬럼을 가지고 있다.

4) 댓글목록은 detail 페이지에서 출력되며 같은 곳에서 작성할 수 있다.

5) 각 댓글은 삭제 할 수 있다.

   ​																							

​																							

### models.py

```python
from django.db import models
from django.db.models.deletion import CASCADE

# Create your models here.
class Article(models.Model):
    title = models.CharField(max_length=10)
    content = models.TextField()
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)

    def __str__(self):
        return self.title


class Comment(models.Model):
    article = models.ForeignKey(Article, on_delete=CASCADE)
    content = models.CharField(max_length=200)
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)

    def __str__(self):
        return self.content
    
```

​															

​																																		

### forms.py

```python
from django import forms
from .models import Article, Comment


class ArticleForm(forms.ModelForm):

    class Meta:
        model = Article
        # fields = '__all__'
        fields = ('title', 'content',)


class CommentForm(forms.ModelForm):

    class Meta:
        model = Comment
        # fields = '__all__'
        exclude = ('article',)
```



​																							

### urls.py

```python
from django.urls import path
from . import views


app_name = 'articles'
urlpatterns = [
    path('', views.index, name='index'),
    path('create/', views.create, name='create'),
    path('<int:pk>/', views.detail, name='detail'),
    path('<int:pk>/delete/', views.delete, name='delete'),
    path('<int:pk>/update/', views.update, name='update'),
    path('<int:pk>/comments/', views.comments_create, name='comments_create'),
    path('<int:article_pk>/comments/<int:comment_pk>/delete/', views.comments_delete, name='comments_delete'),
]
```

​																								

​																							

### views.py

```python
@require_POST
def comments_create(request, pk):
       article = get_object_or_404(Article, pk=pk)
       comment_form = CommentForm(request.POST)
       if comment_form.is_valid():
       # 댓글에 내용만 들어가고 댓글작성시 사용자 id를 넘겨주는 부분이 없음
           comment = comment_form.save(commit=False)
           comment.article = article
           comment.save()
        return redirect('articles:detail', article.pk)
    return redirect('accounts:login')


@require_POST
def comments_delete(request, article_pk, comment_pk):
    comment = get_object_or_404(Comment, pk=comment_pk)
    comment.delete()
    return redirect('articles:detail', article_pk)
```

​																		

​																						

### detail.html

```python
{% extends 'base.html' %}

{% block content %}
  <h2>DETAIL</h2>
  <h3>{{ article.pk }} 번째 글</h3>
  <hr>
  <p>제목 : {{ article.title }}</p>
  <p>내용 : {{ article.content }}</p>
  <p>작성시각 : {{ article.created_at }}</p>
  <p>수정시각 : {{ article.updated_at }}</p>
  <hr>
  <a href="{% url 'articles:update' article.pk %}" class="btn btn-primary">[UPDATE]</a>
  <form action="{% url 'articles:delete' article.pk %}" method="POST">
    {% csrf_token %}
    <button class="btn btn-danger">DELETE</button>
  </form>
  <a href="{% url 'articles:index' %}">[back]</a>
  <hr>
  <!-- 댓글 목록 -->
  <h4>댓글 목록</h4>
  {% if comments %}
    <p><b>{{ comments|length }}개의 댓글이 있습니다.</b></p> 
  {% endif %}
  <hr>
  <ul>
  {% for comment in comments %}
    <li>
      {{ comment.content }}
      <form action="{% url 'articles:comments_delete' article.pk comment.pk %}" method="POST" class="d-inline">
        {% csrf_token %}
        <input type="submit" value="DELETE">
      </form>
    </li>
  </ul>
  <!-- 댓글 작성 form -->
  <form action="{% url 'articles:comments_create' article.pk %}" method="POST">
     {% csrf_token %}
     {{ comment_form }}
     <input type="submitr" value="댓글 작성하기">
  </form>

  {% endfor %}
{% endblock %}
```

