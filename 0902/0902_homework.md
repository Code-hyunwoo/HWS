# :boom: Homework

---

​												

### 1. Django Model

models.py를 작성한 후 마이그레이션 작업을 위해 터미널에 작성해야 하는 두 개의 핵심 명령어를 작성하시오.



**makemigrations**

**migrate**



### 2. 다음 중 옳지 않은 것을 고르시오.



**3 번**

```python
# 1
post = Post()
post.title = 'a'
post.content = 'b'
post.save()

# 2
post = Post(title='가', content='나')
post.save()

# 3
post = Post('제목', '내용')
post.save()

# 4
Post.objects.create(title='1', content='2')
```



### **3. 첫 번째 post를 가져오는 코드로 옳지 않은 코드는?**



**2 번**

**negative indexing은 지원하지 않음**

```python
# 1
post1 = Post.objects.all()[0]

# 2
post2 = Post.objects.all()[-10]

# 3
post3 = Post.objects.all().first()

# 4
post4 = Post.objects.all().get(id=1)
```



### **4. ** Edit

title를 '안녕하세요' content를 '반갑습니다'로 수정하기 위한 코드를 작성하시오.



```python
#1 django extension
my_post = Post()
my_post.title = '타이틀초기값'
my_post.content = '컨텐트초기값'
my_post.save()

my_post = Post.objects.get(pk=1)
#새 값 할당
my_post.title='안녕하세요'
my_post.content='반갑습니다'
#저장 필수
my_post.save()


#2 인풋값을 이용한 수정
def edit(request, pk):
    my_post = Post.objects.get(pk=pk)
    context = {'my_post' = my_post,}
    return render(request, 'articles/edit.html', context)

def update(request, pk):
    my_post = Post.objects.get(pk=pk)
    my_post.title = request.POST.get('title')
    my_post.content = request.POST.get('content')
    my_post.save()
    return redirect('articles:detail', article.pk)
```



### **5. post 객체를 QuerySet 형태로 반환 해주기 위해 빈칸에 들어갈 코드**



```python
posts = Post.objects.all()
```

