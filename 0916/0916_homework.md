# :boom: Homework

---

​																

### 1. User Model BooleanField

User 모델에서 사용할 수 있는 칼럼 중 BooleanField로 정의 된 칼럼을 모두 작성하시오.

​																			

**is_staff ,   is_active , is_superuser**

​																			

### 2. username max length

django에서 기본적으로 사용하는 User 모델의 username 컬럼이 저장할 수 있는 최대길이를 작성하시오.

​																

**150**

​																	

### 3. login validation

단순히 사용자가 '로그인 된 사용자인지' 만을 확인하기 위하여 User 모델 내부에 정의된 속성의 이름을 작성하시오.

​									

**is_authenticated**

​												

### **4. Login 기능 구현**

다음은 로그인 기능을 구현한 코드이다. 빈 칸에 들어갈 코드를 작성하시오.

​																

```python
from django.contrib.auth.forms import (a)AuthenticationForm
from django.contrib.auth import (b)login as auth_login

def login(request):
    if request.method == "POST":
        form = AuthenticationForm(request, request.POST)
        if form.is_valid():
            auth_login(request, form.get_user())  
            
            return redirect(request.GET.get('next') or 'articles:index')

    else: 
        form = AuthenticationForm()
    context = {
        'form' : form
    }
    return render(request, 'accounts/auth_form.html', context)
```

**(a)  AuthenticationForm**

**(b) login**

**(c) form.get_user()**

​																													

### **5. who are you?**

로그인을 하지 않았을 경우 template에서 user 변수를 출력했을 때 나오는 클래스의 이름을 작성하시오.

​																								

**AnonymousUser**

​														

### 6. 암호화 알고리즘 

Django에서 기본적으로 User 객체의 password 저장에 사용하는 알고리즘, 그리고 함께 사용된 해시 함수를 작성하시오.

​																													

 **the PBKDF2 algorithm with a SHA256 hash**

```python
PASSWORD_HASHERS = [
    'django.contrib.auth.hashers.PBKDF2PasswordHasher',
    'django.contrib.auth.hashers.PBKDF2SHA1PasswordHasher',
    'django.contrib.auth.hashers.Argon2PasswordHasher',
    'django.contrib.auth.hashers.BCryptSHA256PasswordHasher',
]
```



​												

### 7. Logout 기능 구현

로그아웃 기능을 구현하기 위하여 다음과 같이 코드를 작성하였다.

로그아웃 기능을 실행 시 문제가 발생한다고 할 때 그 이유와 해결 방법을 작성하시오.

```python
def logout(request):
    logout(request)
    return redirect('accounts:login')
```



```python
django에는 logout의 이름으로 기본 logout 기능이 있고, 지금 logout이름으로 함수를 설정하려하기때문에
import 할 때 logout 이름을 변경하여 사용한다.

from django.contrib.auth import logout as auth_logout

def logout(request):
    auth_logout(request)
    return redirect('articles:index')
```



​															
