# :boom: Workshop

---



### Django Model Form

```python
# models.py
class Reservation(model.Model):
    name = models.CharField(max_length=10)
    date = models.DateField()
```



```python
from django import forms
from .models import Reservation

class ResercationForm(__(a)__):
    
    class __(b)__:
        model = Reservation
        filed = '__all__'
```

​									

**(a)  forms.ModelForm**

**(b)  Meta**

​									

```python
def create(request):
    if request.method == 'POST':
        form = ReservationForm(request.POST)
        if form.is_valid():
            reservation = form.save()
            return redirect('reservations:detail', reservation.pk)
    else:  
    	form = ArticleForm()
        context = {
           'form':form,
        }
        return render(request, 'articles/create.html', context)
```

서버를 실행시킨 후 기능을 테스트 해보니 특정 상황에서 문제가 발생하였다.

이유과 해결방법을 작성하시오.



​	**context 변수부터 그 밑의 return 까지 else 구문에 들여쓰기가 되어있는 상황이다.**

**이런 경우 form 유효성 검사에서 유효하지 않는 경우, 유효성 검사 진행하는 if 구문을 벗어나면 코드가 갈 곳이**

**없어져서 문제가 발생한다.**

**이를 해결하기 위해서** 

**context 변수부터 그 밑의 return 구문을 if else 구문과 동일한 레벨에서 작성한다.**

​																																											

```python
def update(request, pk):
    reservation = Reservation.objects.get(pk=pk)
    if request.method == 'POST':
        __(a)__
        if form.is vaild():
            reservaion = form.save()
            return redirect('reservations:detail', reservation.pk)
    else:
        __(b)__
    context = {
        'reservaion': reservation,
        'form': form
    }
    return render(request, 'reservaions/update.html', context)
```

글 수정 기능을 구현하기 위해 빈칸에 들어갈 코드 (a), (b)를 작성하시오.

​																																

**(a)   form = ReservationForm(request.POST, instance=reservation)**

**(b)   form = ReservationForm(instance=reservation)** 

​																											

```python
<h2> edit </h2>
<form action="{% url ' reservations:update' reservation.pk %}" method="POST">
{% csrf_token %}
{{ form.__(a)__}}
<input type="submit" value="submit">
</form>
```

form 출력을 구현하기 위해 빈칸 (a) 에 작성할 수 있는 코드를 모두 작성하시오.

​																						

**(a)   =    as_p  /  as_ul  /  as_table**