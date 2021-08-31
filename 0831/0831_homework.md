# :boom: Homework

---

​																										

### 1. MTV

Django는 MTV 디자인 패턴으로 이루어진 Web Framework이다.

여기서 MTV는 무엇의 약자이며, 각각 MVC 디자인 패턴과 어떻게 매칭이 되며 

각 키워드가 django에서 하는 역할을 간략히 서술하시오.

​																			

**M (Model) - Model**

**데이터 구조를 정의하고 데이터베이스의 기록을 관리**

**T(Template) - View**

**파일구조나 레이아웃을 정의**

**실제 내용을 보여주는 데 사용**

**V(View) - Controller**

**HTTP 요청을 수신하고 응답을 반환**

**Model을 통해 요청을 충족시키는데 필요한 데이터에 접근**

**Template에게 응답의 서식 설정을 맡김**

​																		

### 2. URL

(a) 는 Django에서 URL 자체를 변수처럼 사용해서 동적으로 주소를 만드는 것을 의미한다.

​													

**(a) = Variable Routing**

​															

### 3. Django template path

Django 프로젝트는 render할 template 파일들을 찾을 때, 

기본적으로 settings.py에 등록된 각 앱 폴더 안의 (a)폴더 내부를 탐색한다.

​															

**(a) = templates**

​															

### **4. Django Template Language**

​							

1) **menus 리스트 반복문 출력**

```python
{% for menu  in menus %}
	<p>{{ menu }}</p>
{% endfor %}
```

​										

2. **posts 리스트를 반복문을 활용하여 0번 글부터 출력**

```python
{% for post  in posts %}
	<p>{{ forloop.counter0 }}번 글 {{ post }}</p>
{% endfor %}
```

​							

3. **user 리스트가 비어있다면 현재 가입한 유저가 없습니다. 출력**

```python
{% for user in users %}
	<p>{{ user }}</p>
{% empty %}
	<p>현재 가입된 유저가 없습니다.</p>
{% endfor %}
```

​									

4. **첫 번째 반복문일 때와 아닐 때를 조건문으로 분기처리하시오.**

```python
{% if forloop.first  %}
	<p>첫 번째 반복문 입니다.</p>
{% else %}
    <p>첫 번째 반복문이 아닙니다.</p>
{% endif %}
```

​													

5. **posts 리스트를 반복문을 활용하여 0번 글부터 출력**

```python
<!-- 5 -->
<p>{{ 'hello'|length}}</p>
<!-- My Name Is Tom -->
<p>{{ 'my name is tom'|title }}</p>
```

​																	

6.**변수 today에 datetime 객체가 들어와있을 때 출력된 결과가 주석과 같아지게 작성**

```python
<!-- 2020년 02월 02일 (Sun) PM 02:02 -->
{{ today|date:"Y년 m월 d일 (D) A H:i"}}
```

​																

### 5. Form tag with Django

​																																											

1) form 태그의 속성인 action의 역할에 대해 설명하시오.

   ​											

   **action = 입력 데이터가 전송될 URL 지정**

   ​													

2)  method가 가질 수 있는 속성 값을 작성하시오.

   ​															

   **post**

   ​													

3) input 태그에 각각 '안녕하세요', '반갑습니다', '파이팅' 문자열을 넣고 submit 버튼을 눌렀을 때 

   이동하는 url 경로를 작성하시오.

   ​																					

   **post/create/?title=안녕하세요/?content=반갑습니다/?my-site=파이팅**

   ​																															