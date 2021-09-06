# :boom: Homework

---

​																																																						

```python
def create(request):
      
    #create
    if request.method == 'POST':
        form = ArticleForm(request.POST)
        if form.is_valid():
            article = form.save()
            return redirect('articles:detail', article.pk)
    else: 
    #new
    	form = ArticleForm()
   	context = {
         'form':form,
       }
    return render(request, 'articles/create.html', context)
```

​																											

#### 1. 왜 변수 context는 if else 구문과 동일한 레벨에 작성되어 있는가?



먼저 만약 context 부분이 else 구문에 들여쓰기 되어있다면, 

form이 유효하지 않는 경우, if 구문 코드에서 나갔을 때 동작할 수 있는 코드가 없다는 문제점이 발생한다.

context를 if else 구문과 동일한 레벨로 작성하면 이러한 문제점을 해결할 수 있고, 

이외에에도 추가적인 이점이 있다.

else구문의 상황에서도 #new 새로운 form을 만들기만 하면 되기 때문에 else구문에서 form을 생성하고 

자연스럽게 context로 연결되어 문제가 없다.

또한, 유효성 검사를 실패했을 때, is_valid()의 역할로 왜 통과하지 못했는지에 대한 Error 메세지들이 

담겨서 context의 form이 나타나기 때문에 더욱 유용하다.

이러한 이점들과 유용성이 있기에 context는 if else 구문과 동일한 레벨에 작성되어지는 게 좋다.

​																	

#### 2. 왜 request의 http method는 POST 먼저 확인하도록 작성하는가?



두 가지의 이유가 있다.

먼저 불필요한 반복을 줄일 수 있다.

그리고 또 다른 이유는 if else 구문에서 만약 GET을 먼저 확인하게 된다면, else 구문에서 get이 아닌

모든 메서드들에 대해서 DB에 영향을 주는 POST방식의 구문들이 작동된다.

이를 방지하기 위해 POST를 먼저 확인하고, 이런 경우 else구문에서는 get이 아닌 다른 메서드가 와도 form을

생성하기만 하기 때문에 DB조작과 관련되지 않고, 문제가 발생하지 않으므로 POST를 먼저 확인하도록 

작성하는 것이 좋다.

