# :boom: Homework

---

​			

### 1. Circle 인스턴스 만들기

아래와 같은 Circle 클래스가 있을 때, 반지름이 3이고 x,y좌표가 (2,4)인 Circle 인스턴스를 만들어 넓이와 둘레를 출력하시오.



```python
class Circle:
    pi = 3.14
    x = 0
    y = 0
    r = 0
    
    def __init__(self, r, x, y):
        self.r = r
        self.x = x
        self.y = y
        
    def area(self):
        return self.pi * self.r * self.r
    
    def circumference(self):
        return 2 * self.pi * self.r
    
    def center(self):
        return (self.x, self.y)
```

```python
c1 = Circle(3, 2, 4)
print(c1.area())
print(c1.circumference())
```

**28.259999999999998**

**18.84**

​						

​											

### 2. Dog와 Bird는 Animal이다

다음과 같이  Animal 클래스가 주어질 때, 해당 클래스를 상속 받아 아래의 보기와 같이 동작하는 Dog 클래스와 

Bird 클래스를 작성하시오.

```python
class Animal:
    def __init__(self, name):
        self.name = name
        
    def walk(self):
        print(f'{self.name}! 걷는다!')
    
    def eat(self):
        print(f'{self.name}! 먹는다!')
```

```python
dog = Dog('멍멍이')
dog.walk() # 멍멍이! 달린다!
dog.bark() # 멍멍이! 짖는다!

bird = Bird('구구')
bird.walk() # 구구! 걷는다!
bird.eat() # 구구! 먹는다!
bird.fly() # 구구! 푸드덕!
```

​										

```python
class Dog(Animal):
    def __init__(self, name):
        self.name = name
    
    def walk(self):
        print(f'{self.name}! 달린다!')
       
    def bark(self):
        print(f'{self.name}! 짖는다!')
        

class Bird(Animal):
    def __init__(self, name):
        self.name = name
    
    def fly(self):
        print(f'{self.name}! 푸드덕!')
```

**멍멍이! 달린다!**
**멍멍이! 짖는다!**
**구구! 걷는다!**
**구구! 먹는다!**
**구구! 푸드덕!**		

​														

### 3. 오류의 종류

아래에 제시된 오류들이 각각 어떠한 경우에 발생하는지 간단하게 작성하시오 .



```python
ZeroDivisionError   
> 0으로 나누고자 할 때 발생
NameError
> namespace 상에 이름이 없는 경우
TypeError
> 타입 불일치, argument 개수 초과, 불일치 등
IndexError
> 인덱스가 존재하지 않거나 범위를 벗어나는 경우
KeyError
> 해당 키가 존재하지 않는 경우
ModuleNotFoundError
> 존재하지 않는 모듈을 import 하는 경우
ImportError
> Module은 있으나 존재하지 않는 클래스/ 함수를 가져오는 경우
```

