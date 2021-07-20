# :boom: 	0720 Homework

---

​		

### 1. Mutable & Immutable

주어진 컨테이너들을 각각 변경 가능한 것과 변경 불가능한 것으로 분류하시오.

```
String, List, Tuple, Range, Set, Dictionary
```

​		

#### 	Mutable 

List, Set, Dictionary

#### 	Immutable

String, Tuple, Range

​		

### 2. 홀수만 담기

range와 slicing을 활용하여 1부터 50까지의 숫자 중, 홀수로만 이루어진 리스트를 만드시오.

```python
list(range(1,51))[0:50:2]
```

[1, 3, 5, 7, 9, 11, 13, 15, 17, 19, 21, 23, 25, 27, 29, 31, 33, 35, 37, 39, 41, 43, 45, 47, 49]

​				

### 3. Dictionary 만들기

 반 학생들의 정보를 이용하여 key는 이름, value는 나이인 dictionary를 만드시오.

```python
classmates = {'이재경' : '20', '윤소라' : '21', '이민형' : '22', '유창준' : '23', '이현우' : '24'}
type(classmates)
classmates.keys()
classmates.values()
classmates.items()
```

<class 'dict'>

dict_keys(['이재경', '윤소라', '이민형', '유창준', '이현우'])

dict_values(['20', '21', '22', '23', '24'])

dict_items([('이재경', '20'), ('윤소라', '21'), ('이민형', '22'), ('유창준', '23'), ('이현우', '24')])

​			

### 4. 반복문으로 네모 출력

두 개의 정수 n과 m이 주어졌을 때, 가로의 길이가 n, 세로의 길이가 m인 직사각형 형태를 별(*) 문자를 이용하여 출력하시오. 단, 반복문을 사용하여 작성하시오.

```python
n = 5
m = 9

for i in range(m):
    for j in range(n):
        print('*', end ='')
    print()
```

```python
*****
*****
*****
*****
*****
*****
*****
*****
*****
```

​			

​	

### 5. 조건 표현식

주어진 코드의 조건문을 조건 표현식으로 바꾸어 작성하시오.

```python
temp = 36.5
 if temp >= 37.5:
     print('입실 불가')
 else:
     print('입실 가능')
```



```python
temp = 36.5
print('입실 불가') if temp >= 37.5 else print('입실 가능')
```

 입실 가능

​				

### 6. 평균 구하기

주어진 list에 담긴 숫자들의 평균값을 출력하시오.

```python
scores = [80, 89, 99, 83]
```

```python
scores = [80, 89, 99, 83]
total = 0
for score in scores:
    total += score
avr = total / len(scores)
print(avr)
```

 87.78

​		
