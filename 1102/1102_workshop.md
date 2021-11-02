# :boom: Workshop

---



### Likes



### index.html																																	

```javascript
{% extends 'base.html' %}

{% block content %}
  <h1>Articles</h1>
  {% if request.user.is_authenticated %}
    <a href="{% url 'articles:create' %}">[CREATE]</a>
  {% else %}
    <a href="{% url 'accounts:login' %}">[새 글을 작성하려면 로그인하세요.]</a>
  {% endif %}
  <hr>
  {% for article in articles %}
    <p>
      <b>작성자 : <a href="{% url 'accounts:profile' article.user.username %}">{{ article.user }}</a></b>
    </p>
    <p>글 번호 : {{ article.pk }}</p>
    <p>글 제목 : {{ article.title }}</p>
    <p>글 내용 : {{ article.content }}</p>
    <div>
      <form class="like-form" data-id="{{article.pk}}">
        {% csrf_token %}
        {% if request.user in article.like_users.all %}
          <button class="btn btn-link">
            <i id="like-{{article.pk}}" class="fas fa-heart fa-lg" style="color:crimson;"></i>
          </button>
        {% else %}
          <button class="btn btn-link">
            <i id="like-{{article.pk}}" class="fas fa-heart fa-lg" style="color:black;"></i>
          </button>
        {% endif %}
      </form>
    </div>
    <p>
      <span id="like-count-{{article.pk}}">
        {{ article.like_users.all|length }}
      </span>
        명이 이 글을 좋아합니다.</p>
    <a href="{% url 'articles:detail' article.pk %}">[DETAIL]</a>
    <hr>
  {% endfor %}
  <script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta2/css/all.min.css" integrity="sha512-YWzhKL2whUzgiheMoBFwW8CKV4qpHQAEuvilg9FAn5VJUDwKZZxkJNuGM4XkWuk94WCrrwslk8yWNGmY1EduTA==" crossorigin="anonymous" referrerpolicy="no-referrer" />
  <script>
    const forms = document.querySelectorAll('.like-form')
    forms.forEach(function (form){
      // console.log(form)
      // axios.get('http://127.0.0.1:8000/articles/')
      form.addEventListener('submit', function (event){
        event.preventDefault()
        // console.log(event)
        const csrftoken = document.querySelector('[name=csrfmiddlewaretoken]').value
        // console.log(csrftoken)
        const articleID = event.target.dataset.id
        axios.post(`http://127.0.0.1:8000/articles/${articleID}/likes/`,{}, {headers: {'X-CSRFToken': csrftoken}
        })
        .then(function (response) {
          const count = response.data.count
          const liked = response.data.liked

         // const {count, liked} = response.data
          const likeIconColor = document.querySelector(`#like-${articleID}`)
          if (liked) {
            likeIconColor.style.color = 'crimson'
          } else {
            likeIconColor.style.color = 'black'
          }
         // likeButton.innerText = liked ? '좋아요 취소' : '좋아요'
          const likeCount = document.querySelector(`#like-count-${articleID}`)
          likeCount.innerText = count
        })
        .catch((error) => {
          if (error.response.status == 401) {
            window.location.href = '/accounts/login/'
          }
        })
      })
    })
    // 떴다 사라지는 이유로 데이터 전송이 일어나서...?
  </script>
{% endblock %}

```

​																															

​																																							

### articles/views.py

```python

@require_POST
def likes(request, article_pk):
    if request.user.is_authenticated:
        article = get_object_or_404(Article, pk=article_pk)

        if article.like_users.filter(pk=request.user.pk).exists():
        # if request.user in article.like_users.all():
            # 좋아요 취소
            article.like_users.remove(request.user)
            liked = False
        else:
            # 좋아요 누름
            article.like_users.add(request.user)
            liked = True
        like_status = {
            'liked': liked,
            'count': article.like_users.count(),
        }
        return JsonResponse(like_status)
    return HttpResponse(status=401)

```

