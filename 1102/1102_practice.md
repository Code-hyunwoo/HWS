# :boom: Practice

---



### Follow



### accounts/profile.html																																	

```javascript
{% extends 'base.html' %}

{% block content %}
<h1>{{ person.username }}님의 프로필</h1>

{% with followings=person.followings.all followers=person.followers.all %}
  <div>
    <div id="follow-count">
      팔로잉 : {{ followings|length }} / 팔로워 : {{ followers|length }}
    </div>
    {% if request.user != person %}
      <div>
        <form id="follow-form" data-user-id="{{ person.pk }}">
          {% csrf_token %}
          {% if request.user in followers %}
            <button>언팔로우</button>
          {% else %}
            <button class="btn-primary">팔로우</button>
          {% endif %}
        </form>
      </div>
    {% endif %}
  </div>
{% endwith %}


<hr>

<h2>{{ person.username }}'s 게시글</h2>
{% for article in person.article_set.all %}
  <div>{{ article.title }}</div>
{% endfor %}

<hr>

<h2>{{ person.username }}'s 댓글</h2>
{% for comment in person.comment_set.all %}
  <div>{{ comment.content }}</div>
{% endfor %}

<hr>


<a href="{% url 'articles:index' %}">[back]</a>

<script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>
<script>
  const form = document.querySelector('#follow-form')
  const csrftoken = document.querySelector('[name=csrfmiddlewaretoken]').value
  form.addEventListener('submit', function (event) {
    event.preventDefault()
    const userId = event.target.dataset.userId
    //방법이 2가지임
    // axios.post(http://127.0.0.1:8000/accounts/${userId}/follow/, {}, {headers: {'X-CSRFToken': csrftoken}})
    axios({
      method: 'post',
      url: `http://127.0.0.1:8000/accounts/${userId}/follow/`,
      headers: {'X-CSRFToken': csrftoken },
    })
    .then(response => {
      console.log(response)
      const followersCount = response.data.followers_count
      const followingsCount = response.data.followings_count
      const followed = response.data.followed

      const followCount = document.querySelector('#follow-count')

      followCount.innerText = `팔로잉 : ${followingsCount} / 팔로워 : ${followersCount}`

      const followBtn = document.querySelector('#follow-form > button')
      /*
      if (followed) {
        followBtn.innerText = '언팔로우'
      } else {
        followBtn.innerText = '팔로우'
      }
      */
      // followBtn.classList.toggle('btn-secondary')
      // followBtn.classList.toggle('btn-primary')
      if (followed) {
        followBtn.innerText = '언팔로우'
        followBtn.setAttribute('class', 'btn-secondary')
      } else {
        followBtn.innerText = '팔로우'
        followBtn.setAttribute('class', 'btn-primary')
      }
    })
    .catch((error) => {
          if (error.response.status == 401) {
            window.location.href = '/accounts/login/'
          }
    })
  })

</script>
{% endblock %}

```

​																					

### accounts/views.py														

```javascript
@require_POST
def follow(request, user_pk):
    if request.user.is_authenticated:
        # 팔로우 받는 사람
        you = get_object_or_404(get_user_model(), pk=user_pk)
        me = request.user

        # 나 자신은 팔로우 할 수 없다.
        if you != me:
            if you.followers.filter(pk=me.pk).exists():
            # if request.user in person.followers.all():
                # 팔로우 끊음
                you.followers.remove(me)
                followed = False
            else:
            # 팔로우 신청
                you.followers.add(me)
                followed = True
        
            follow_status = {
                'followed': followed,
                'followers_count': you.followers.count(),
                'followings_count': you.followings.count(),
            }
            return JsonResponse(follow_status)
    return HttpResponse(status=401)
```

