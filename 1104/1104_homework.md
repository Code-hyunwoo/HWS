# :boom: Homework

---

​																											

### 1. 아래의 설명을 읽고 T/F 여부를 작성하시오.

- 동일한 요소에 v for 와 v if, 두 디렉티브가 함께 있다면,  v - if 가 더 높은 우선 순위를 가지며 , v - if 는 루프가 반복 될 때마다 실행된다.    **F**  (v-for가 우선순위가 더 높음)
- 동일한 요소에 v for 와 v if, 두 디렉티브가 함께 있다면, 매 반복 시에 v-if의 조건문으로 요소의 렌더링 여부를 결정한다.   **F**  (v-for가 우선순위가 더 높음)
- v-bind 디렉티브는 ““@ “, v-on 디렉티브는 “ : shortcut( 약어 을 제공한다. **F** (반대)
- v-model 디렉티브는 input, textarea , select 같은 HTML Element 와 단방향 데이터 바인딩을 이루기 때문에 v-model 속성값의 제어를 통해 값을 바꿀 수 있다.   **F** (양방향 데이터 바인딩)



​																																																																																															

### 2. computed와 watch의 개념과 그 차이에 대해서 간단히 서술하시오.



Computed

- 특정 데이터를 직접적으로 사용하여 다른 값으로 만들 때 사용
- 계산해야 하는 목표 데이터를 정의하는 선언형 프로그래밍

- 특정 값이 변동하면 해당 값을 다시 계산해서 보여준다.

watch

- 특정 데이터의 변화 상황에 맞춰 다른 data등이 바뀌어야 할 때 주로 사용

- 감시할 데이터를 지정하고, 그 데이터가 바뀌면 특정 함수를 실행

- 데이터가 바뀌면 특정 함수를 실행하는 명령형 프로그래밍

- 특정 값이 변동하면 다른 작업을 한다.

  ​																																																					

​																																																																																																		

### 3. 다음의 빈칸 (a), (b), (c) 에 들어갈 코드를 작성하시오

​																																													

```javascript
<body>
  <div id="app">
      <div (a) = "(num, (b)) in (c)" :key ="(b)">
   			 <p>{{ num }}</p>
	  </div>
  </div>

    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
    <script>
      const app = new Vue({
        el: '#app',
        data: {
          nums: [1, 2, 3, 4, 5, 6],
        },
        computed: {
            oddNumbers: function () {
                return this.nums.filter(num => {
                    return num % 2 == 1
                })
            }
        }
      })
    </script>
  </body>
</html>
```

​																														

**a = v-for**

**b = index**

**c = oddNumbers**

