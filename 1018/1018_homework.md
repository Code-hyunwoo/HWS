# :boom: Homework

---



### 1. True or False

각 문항을 읽고 맞으면 T, 틀리면 F를 작성하고 틀렸다면 그 이유도 함께 작성하시오.

1) Foreignkey는 부모 테이블의 데이터를 참조하기 위한 키이다.
2) 1:N 관계에서 1은 N의 데이터를 직접 참조 할 수 있다.
3) on_delete 속성은 Foreignkey 필드의 필수 인자이다.
4) 1:N 관계에서 외래 키는 반드시 부모 테이블의 PrimaryKey여야 한다.



**T**

**F** : 데이터관계를 보장할 수  없기 때문에 comment_set을 통하여 역참조 할 수 있다.(?) 

**T**

**F** : 반드시 Primarykey일 필요는 없지만 유일한 값이어야 함



### 2. Foreignkey column name

다음과 같이 이름이 articles인 app의 models.py에 작성된 코드를 바탕으로 테이블이 만들어 졌을 때, 

데이터베이스에 저장되는 ForeignKey 컬럼의 이름과 테이블의 이름이 무엇인지 작성하시오.



```python
from django.db import models

class Question(model.Model):
    title = models.CharFiels(max_length=50)

class Comment(models.Model):
    answer = models.ForeignKey(Question, on_delete=CASCADE)
    content = models.CharField(max_length=100)
```



**컬럼 이름 = answer_id**

**테이블 이름 = articles_comment**



### 3. 1:N model manager

위 2번 문제 모델 관계를 바탕으로 어느 template 페이지가 다음과 같이 작성되어 있을 때,

질문에 작성된 모든 댓글을 출력하고자한다. 해당 template에서 Question 객체를 사용할 수 있다면

빈칸에 알맞은 코드를 작성하시오.



```python
{% for comment in __(a)__ %}
	<p> {{ comment.content }} </p>
{% endfor %}
```



**(a) = comments**



### 4. next parameter

다음과 같이 게시글을 삭제하는 delete 함수와 로그인을 위한 login 함수가 작성되어 있다.

만약 비로그인 사용자가 삭제를 시도한다면, django는 해당 사용자를 url에 next 파라미터가 붙은 login 페이지로 redirect 한다.



1) redirect된 로그인 페이지에서 로그인에 성공했을 때 발생하는 HTTP response status code를 작성하고, 

   이 오류가 발생한 원인을 작성하시오.



**@login_required 와 @require_POST 를 같이 쓰게되면**

**비로그인 상태로 접근 - > 로그인 창 - > 로그인성공 - > 405error 발생**

**redirect(request.GET.get('next')) 을 통해서 GET방식으로 되돌아가기 때문에 생기는 로직상의 에러**

**@login_require 대신 request.user.is_authenticated 사용하기**



2. 위에서 발생한 오류를 해결하기 위해 다음과 같이 동작하는 코드로 수정하시오.

   -  게시글 삭제는 HTTP POST method로만 가능하다.

   - 인증되지 않은 사용자가 게시글 삭제를 시도하는 경우, 해당 게시글 상세페이지로 redirect 되도록 한다.

     (게시글은 삭제되지 않는다.)		



```python
@require_POST
def delete(request, pk):
    # 작성자만 삭제할 수 있도록 수정
    article = get_object_or_404(Article, pk=pk)
    if request.user.is_authenticated:
        if request.user == article.user:
            article.delete()
            return redirect('articles:index')
    return redirect('articles:detail', article.pk)


def login(request):
    if request.user.is_authenticated:
        return redirect('articles:index')

    if request.method == 'POST':
        form = AuthenticationForm(request, request.POST)
        if form.is_valid():
            auth_login(request, form.get_user())
            return redirect(request.GET.get('next') or 'articles:index')
    else:
        form = AuthenticationForm()
    context = {
        'form': form,
    }
    return render(request, 'accounts/login.html', context)    
```

