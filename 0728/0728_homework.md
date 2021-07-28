# :boom: Homework

---



### 1. Type Class

Python 은 객체 지향 프로그래밍 언어이다 . 

Python 에서 기본적으로 정의되어 있는 클래스를 최소 5가지 이상 작성하시오 .



```python
str, set, dict, int, list
```

​							

### 2. Magic Method

아래에 제시된 매직 메서드들이 각각 어떠한 역할을 하는지 간단하게 작성하시오 .

```python
__init__, __del__, __str__, __repr__

__init__
> 인스턴스가 생성되고 나서 호출되는 메소드. 인자를 받아서 내부에 지정 가능
__del__
> 객체의 소멸에 될때 해야할 일을 지정. 
__str__
> 객체를 이해하기 쉽게 표현할 수 있는 문자열.
__repr__
> 객체를 나타내는 공식적인 문자열.
```





### 3. Instance Method

.sort()와 같이 문자열 , 리스트 , 딕셔너리 등을 조작 할 때 사용하였던 것들은 클래스에 정의된 메서드들이었다 . 

이처럼 문자열 , 리스트 , 딕셔너리 등을 조작하는 메서드를 최소 3가지 이상 그 역할과 함께 작성하시오 .

```python
.reverse()
> 문자열을 역순(반대로) 나열(정렬 아님)
.pop()
> 원소를 제거하고 반환(unordered일 경우는 임의)
.lower()
> string을 모두 소문자로 만들어 반환
```

​									

### 4. Module Import

```python
# fibo.py

def fibo_recursion(n):
    if n < 2: 
        return n
    else:
        return fibo_recurion(n-1) + fibo_recursion(n-2)
```

위와 같은 코드가 같은 폴더 안의 fibo.py 파일에 작성되어 있을 때, 아래와 같은 형태로 함수를 실행 할 수 있도록 하는 import 문을 빈칸 (a) , (b) , (c)를 채워 넣어 완성하시오 .

​											

```python
from __(a)__ import __(b)__ as __(c)__

recursion(4)
```

**from fibo import fibo_recursion as recursion**

**(a) = fibo  (b) = fibo_recursion (c) recursion**

​																	