# :boom: Homework

---

​						

## 1. Built-in 함수와 메서드

 sorted() 와 .sort() 의 차이점을 코드의 실행 결과를 활용하여 설명하시오 .

​																					

**.sort()**와 **sorted()** 는 모두 list를 정렬해준다는 공통점이 있지만, .sort()는 sorted()와는 **다르게 원본 list를 변형**시키고, None을 리턴한다는 차이점이 있습니다.

```python
lotto = [31, 3, 28, 15, 33, 18]
lotto.sort() = [3, 15, 18, 28, 31, 33]
print(lotto)
```

```python
[3, 15, 18, 28, 31, 33] # 원본이 변화
```

```python
lotto = [31, 3, 28, 15, 33, 18]
sorted(lotto) = [3, 15, 18, 28, 31, 33]
print(lotto)
```

```python
[31, 3, 28, 15, 33, 18] # 원본이 변화하지않음
```

​							

## 2.extend()와 .append()

.extend() 와 .append()의 차이점을 코드의 실행 결과를 활용하여 설명하시오 .

​													

 **append()**와 **extend()**는 항목을 추가한다는 공통점이 있지만, append는 값을 추가하고, extend는 리스트에 iterable(특히 string[주의]) 값을 추가하는 차이가 있습니다.

```python
cafe = ['coffee','starbucks']
cafe.append(['cocoa'])
cafe.extend(['cocoa'])
print(cafe)
```

```python
['coffee', 'starbucks', ['cocoa'], 'cocoa'] #append는 리스트 그대로 추가, extend는 문자열 추가
```

```python
#특히 string 주의
cafe = ['coffee','starbucks']
cafe.append('ediya')
cafe.extend('ediya')
print(cafe)
```

```python
['coffee', 'starbucks', 'ediya', 'e', 'd', 'i', 'y', 'a'] #extend는 문자열 나눠서 추가
```

​						

## 3. 복사가 잘 된 건가?

아래의 코드를 실행 하였을 때, 변수 a와 b에 담긴 list의 요소가 같은지 혹은 다른지 여부를 판단하고 그 이유를 작성하시오 .

​					

```python
a = [1,2,3,4,5]
b = a

a[2] = 5

print(a)
print(b)
```

```python
[1, 2, 5, 4, 5] # a
[1, 2, 5, 4, 5] # b     a=b
```

​	**list는 mutable하고, 리스트의 복사는 같은 리스트의 주소를 참조하므로, 해당 주소의 일부 값을 변경하는 경우 이를 참조하는 모든 변수에 영향을 준다. 따라서 변수 a와 b의 요소는 같이 변한다.**

​				

