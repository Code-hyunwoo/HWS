# :boom: Workshop

---



### Todo App Project



#### 회원가입

​																											

views.py

```python
# 장고가 만든 것
from django.shortcuts import redirect, render
from django.contrib.auth.forms import AuthenticationForm
from django.contrib.auth import login as auth_login
from django.contrib.auth import logout as auth_logout

# 우리가 만든 것
from .forms import CustomUserCreationForm

# Create your views here.

def signup(request):
    if request.method == "POST":   # 사용자가 값을 입력했을 때,
        form = CustomUserCreationForm(request.POST)
        if form.is_valid():
            form.save()
            return redirect('accounts:login')
    else:      # Get일 때, url에 접속했을 때,
        form = CustomUserCreationForm()
    context = {
        'form' : form,
    }
    return render(request, 'accounts/signup.html', context)

def login(request):
    if request.method == "POST":
        form = AuthenticationForm(request, request.POST)
        if form.is_valid():
            user = form.get_user() # form에서 어떤 유저 인지 가져오기
            auth_login(request, user)
            return redirect('todos:index')
    else:
        form = AuthenticationForm()
    
    context = {
        'form': form,
    }
    return render(request, 'accounts/login.html', context)


def logout(request):
    auth_logout(request)
    return redirect('todos:index')
```

​																							

​																								

#### 로그인

​																						

forms.py

```python
from django.contrib.auth.forms import UserCreationForm
from django.contrib.auth  import get_user_model

class CustomUserCreationForm(UserCreationForm):

    class Meta(UserCreationForm.Meta):   # User~Form에 있는 meta 클래스 상속
        model = get_user_model()  
        # 이게 overriding 이라고 하는데, 
        # 현재 meta 클래스에서 찾는거고,
        # 나머지는 상속 받은(부모)의 UserCreationForm.Meta
        # get_user_model()  == 현재 활성화된 user 모델을 찾아오는 것
        fields = UserCreationForm.Meta.fields
       
```



#### Todo 목록(index)

​																																																

models.py

```python
from django.db import models
from django.conf import settings
# Create your models here.

# User(1) -> Todo(N)
# models.py 에서만 settings.AUTH_USER_MODEL
class Todo(models.Model):
    author = models.ForeignKey(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)
    title = models.CharField(max_length=100)
    completed = models.BooleanField(default=False)
```

​															

forms.py

```python
from django import forms
from django.forms import fields
from .models import Todo

class TodoForm(forms.ModelForm):

    class Meta:
        model = Todo
        fields = ['title', 'completed']
```

​																			

#### Todo 생성(new)

​																									

views.py

```python
from django.shortcuts import redirect, render
from .models import Todo
from .forms import TodoForm
from django.contrib.auth.decorators import login_required
# Create your views here.

@login_required
def index(request):

    # todos = Todo.objects.all()
    # 본인이 작성한 todo만 보이도록 설정
    # 역참조
    todos = request.user.todo_set.all()

    context = {
        'todos' : todos,
    }
    return render(request, 'todos/index.html', context)

@login_required
def new(request):
    if request.method == 'POST':
        form = TodoForm(request.POST)
        if form.is_valid():
            todo = form.save(commit=False)
            todo.author = request.user
            todo.save()
            return redirect('todos:index')
    else:
        form = TodoForm()
    context = {
        'form': form
    }
    return render(request, 'todos/new.html', context)
```

​																																

index.html

```python
{% extends 'base.html' %}

{% block content %}
<h1>todo index</h1>

{% for todo in todos  %}
    <div> 
        <h1>할 일: {{ todo.title }}</h1>
        <p>작성자: {{ todo.author }} </p>
        <p>완료 여부: {{ todo.completed }}</p>
        <hr>
    </div>

{% endfor %}

{% endblock content %}
```

