# :boom: Homework

---

​																																									

### 1. M:N True or False

각 문항을 읽고 맞으면 T, 틀리면 F를 작성하고, 틀렸다면 그 이유도 함께 작성하시오.



1. Django에서는 1:N 관계는 ForeignKeyField를 사용하고, M:N 관계는 ManyToManyField를 사용한다. 
2. ManyToManyField를 설정하고 만들어지는 테이블 이름은 "앱이름_클래스이름_지정한 필드이름"의 형태로 만들어진다.

3. ManyToManyField의 첫번째 인자는 참조할 모델, 두 번째 인자는 related_name이 작성되는데 두가지 모두 필수적으로 들어가야 한다.

   ​																										

**F: ForeignkeyField로 M:N을 만들 수도 있다.**

**T**

**F: 필수 인자는 위치인자 하나(M:N관계로 설정할 모델 클래스)**

​																								

​																								

### 2. Like in templates

아래 빈 칸 a와 b에 들어갈 코드를 각각 작성하시오.

​																													

```python
    <div>
      <form action="{% url 'articles:likes' article.pk %}" method="POST">
        {% csrf_token %}
        {% if user in article.like_users.all %}
          <button><i class="fas fa-heart" style="color:red"></i></button>
        {% else %}
          <button><i class="far fa-heart" style="color:black"></i></button>
        {% endif %}
      </form>
      <p> 좋아요 수 : {{ article.like_users.count }}</p>
    </div>
```

**a = user**

**b = article.like_user.all**

​																								

​																																			

### 3. Follow in views

```python
@require_POST
def follow(request, user_pk):
    if request.user.is_authenticated:
        user = request.user
        person = get_object_or_404(get_user_model(), pk=user_pk)
    
        if user != person:
            if person.followers.filter(pk=user.pk).exists():
            # if request.user in person.followers.all():
            # 언팔로우
                person.followers.remove(user)
            else:
            # 팔로우
                person.followers.add(user)
        return redirect('accounts:profile', person.username)
    return redirect('accounts:login')
```

**a =  user_pk**

**b = followers**

**c = filter**

**d = remove**

**e = add**

​																			

​																				

### 4. User AttributeError

다음과 같은 에러 메시지가 발생하는 이유와 이를 해결하기 위한 방법과 코드를 작성하시오.

```python
AttributeError at ~/accounts/signup/
auth.User has been swapped for 'accounts.User'
```



settings.AUTH_USER_MODEL을 다른 모델로 변경했지만,

기존 코드에서는 예전 User를 참조하기 때문에 발생하는 에러 메시지 이다.



User모델을 커스텀하여 사용하는 경우, 

auth.User를 사용할 때마다 커스텀한 User모델을 직접 import하여 사용해야 한다.



```python
from django.contrib.auth import get_user_model
User = get_user_model()
```

​																							

​																					

### 5. related_name

아래의 경우 Foreignkey 혹은 ManyToManyField에 related_name을 필수적으로 작성해야 한다.

그 이유를 설명하시오.

```python
class Article(models.Model):
    user = models.ForeignKey(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)
    like_users = models.ManyToManyField(settings.AUTH_USER_MODEL)
```



**이전 1:N(User:Article) 관계에서 이미 해당 매니저 이름을 사용중이기 때문**

​														

​																																										

### 6. follow templates

person 변수에는 view함수에서 넘어온 유저 정보가 담겨 있고, 모델 정보가 아래와 같을 때

빈칸에 알맞은 코드를 각각 작성하시오.



```python
<div class='fw-bold'>
팔로잉 수 : {{ followings|length }}
팔로워 수 : {{ followers|length }}</div>

{% if user != person %}
      <div>
        <form action="{% url 'accounts:follow' person.pk %}" method="POST">
          {% csrf_token %}
          {% if user in followers %}
            <input type="submit" value="언팔로우">
          {% else %}
            <input type="submit" value="팔로우">
          {% endif %}
        </form>
      </div>
    {% endif %}
```

**a =  person.followings.all**

**b = person.followers.all**

**c = user**

**d = person**

**e = person.pk**
