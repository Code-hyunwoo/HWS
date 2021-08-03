# :boom: Homework

---

​										

### 1. Semantic Tag

보기 중 콘텐츠의 의미를 명확히 하기위해 HTML5에서 새롭게 추가된 시맨틱 태그를 모두 고르시오.

```html
div, header, h1, section, footer, a, form, span
```

**header : 문서 전체나 섹션의 헤더**

**section : 문서의 일반적인 구분, 컨텐츠의 그룹을 표현**

**footer : 문서 전체나 섹션의 푸터(마지막 부분)**							

​																																																

### 2. input Tag

아래 이미지와 같이 로그인 Form을 생성하는 HTML코드를 작성하시오.

단, USERNAME글자를 클릭하면 아이디를 입력하는 input에, 

PWD 글자를 클릭하면 비밀번호를 입력하는 input에 focusing 되도록 하시오.

​														

```html
    <label for="USERNAME">USERNAME :</label>
    <input type="text"id="username"name="username"placeholder="이름을 입력해주세요"required,autofocus> <br>
    <label for="pass">PWD :</label> 
    <input type="password"id="pass"name="password"required,autofocus>
    <input type="submit"value="로그인">
```

​													

### 3. 크기 단위

단위 em 은 요소에 지정된 상속된 사이즈나 기본 사이즈에 대해 상대적인 사이즈를 설정한다 . 

즉, 상속의 영향으로 사이즈가 의도치 않게 변경될 수 있는데 

이를 예방하기 위해 HTML 최상위 요소의 사이즈를 기준으로 삼는 크기 단위는 무엇인가 ?

​														

**rem**

​														

### 4. 선택자

다음 예제를 통해 '자손 결합자'와 '자식 결합자'의 차이를 설명하시오.

​																

```html
 /*자손 결합자*/
div p { 
   color: crimson;
}
 /* 자식 결합자 */
div > p {
   color: crimson;
}
```

자손 결합자는 선택자 하위의 모든 요소에 영향을 준다. 

따라서 예제의 경우 div선택자 하위의 모든 p 선택자 요소 컬러가 crimson이 된다.

자식 결합자의 경우,  바로 아래의 요소에만 영향을 준다.

따라서 div 선택자의 바로 아해 p선택자 요소 컬러만 crimson이 된다.

