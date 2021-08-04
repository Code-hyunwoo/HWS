# :boom: Homework

---

## Bootstrap

공식 문서의 Component를 활용하여 물음에 답하시오.

1) 각 문항에 제시된 이미지는 현재 lab.ssafy.com에서 사용중인  components이다.

​      제시된 요소에 사용된 Bootstrap Component가 무엇인지 작성하시오.

2. 위에서 답한 Bootstrap Component를 사용하여 제시된 요소와 유사한 형태가 되도록 코드를 작성하시오.

   ​															

   

### Buttons

```html
  <div class="d-grid gap-2 col-6 mx-auto">
        <button class="btn btn-success" type="button">sign in</button>
```

​																								

### Navbar

```html
 <ul class="nav nav-tabs bg-dark">
                <li class="navbar-brand" href="#">
                  <img src="https://blog.kakaocdn.net/dn/bawTIq/btq6lZWnFtY/6YNzuPTw6V8Sk0EmSa0o10/img.jpg" alt="" width="30" height="24">
                </li>
                <li class="nav-item dropdown">
                  <a class="nav-link dropdown-toggle text-white" data-bs-toggle="dropdown" href="#" role="button" aria-expanded="false">프로젝트</a>
                  <ul class="dropdown-menu">
                    <li><a class="dropdown-item" href="#">Action</a></li>
                    <li><a class="dropdown-item" href="#">Another action</a></li>
                    <li><a class="dropdown-item" href="#">Something else here</a></li>
                    <li><hr class="dropdown-divider"></li>
                    <li><a class="dropdown-item" href="#">Separated link</a></li>
                  </ul>
                </li>
                <li class="nav-item dropdown">
                    <a class="nav-link dropdown-toggle text-white" data-bs-toggle="dropdown" href="#" role="button" aria-expanded="false">그룹들</a>
                    <ul class="dropdown-menu">
                      <li><a class="dropdown-item" href="#">Action</a></li>
                      <li><a class="dropdown-item" href="#">Another action</a></li>
                      <li><a class="dropdown-item" href="#">Something else here</a></li>
                      <li><hr class="dropdown-divider"></li>
                      <li><a class="dropdown-item" href="#">Separated link</a></li>
                    </ul>
                  </li>
                <li class="nav-item">
                  <a class="nav-link text-white" href="#">활동</a>
                </li>
                <li class="nav-item">
                  <a class="nav-link text-white" href="#">마일스톤</a>
                </li>
                <li class="nav-item">
                  <a class="nav-link text-white" href="#">스니펫</a>
                </li>
            </ul>      
```

​															

### Pagination

```html
<nav aria-label="...">
            <ul class="pagination">
              <li class="page-item disabled">
                <a class="page-link" href="#" tabindex="-1" aria-disabled="true">Prev</a>
              </li>
              <li class="page-item active" aria-current="page">
                  <a class="page-link" href="#">1</a>
              <li class="page-item"><a class="page-link" href="#">2</a></li>
              <li class="page-item"><a class="page-link" href="#">3</a></li>
              <li class="page-item"><a class="page-link" href="#">4</a></li>
              <li class="page-item">
                <a class="page-link" href="#">Next</a>
              </li>
            </ul>
          </nav>    
```

​																			

### Alerts, Form, Buttons

```html
        <div class="container">
            <div class="alert alert-danger bg-danger text-white" role="alert" >
                Invalid Login or password</div>
            <p class="text-center fw-bold fs-2">SSAFY 전용 Gitlab 시스템</p>
            <hr>
            <form> 
                <div class="mb-3">
                <p class="text-center fw-bold mb-3 fs-4">Sign in</p>
                <hr>
                <label for="inputEmail" class="form-label fw-bold">Username or email</label> 
                <input type="email" id="inputEmail" class="form-control" required autofocus> 
                </div>
                <div class="mb-3">
                <label for="inputPassword" class="form-label fw-bold">Password</label> 
                <input type="password" id="inputPassword" class="form-control" required> 
                </div>
                <div class="checkbox mb-3 d-flex"> 
                    <input type="checkbox" class="form-check-input" id="examplecheck1"> 
                    <label class="form-check-label fw-bold" for="examplecheck1">  Remember me  </label> 
                    <span class="ms-auto text-blue fw-bold"><a href="#">Forgot your password?</a></span> 
                </div>

                <div class="d-grid gap-2 col-12 mx-auto">
                    <button class="btn btn-success" type="button">sign in</button>
            </form>
        </div>
    
```

