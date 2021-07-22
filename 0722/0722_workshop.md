# :boom: Workshop

---



### 1.  숫자의 의미

정수로 이루어진 list를 전달 받아 , 각 정수에 대응되는 아스키 문자를 이어붙인 문자열을 반환하는

 get_secret_word함수를 작성하시오 . 

단, list 는 65 이상 90 이하 그리고 97 이상 122 이하의 정수로만 구성되어 있다 .

```python
get_secret_word([83, 115, 65, 102, 89]) #= 'SsAfY'
```

​		

```python
def get_secret_word(n):
    answer = ''
    for i in n:
        answer += chr(i)
    return f"'{answer}'"
        
print(get_secret_word([83, 115,65, 102, 89]))    
```

​	**'SsAfY'**			

​				

### 2.  내 이름은 몇일까?

문자열을 전달 받아 해당 문자열의 각 문자에 대응되는 아스키 숫자들의 합을 반환하는

**get_secret_number**함수를 작성하시오 . 단, 문자열은 A~Z, a~z 로만 구성되어 있다 . 

```python
get_secret_number('tom') #=> 336
```

​			

```python
def get_secret_number(n):
    answer = 0
    for i in n:
        answer += ord(i)
    return answer

print(get_secret_number('tom'))
```

   **336**			

​		

### 3. 강한 이름

문자열 2개를 전달 받아 두 문자열의 각 문자에 대응되는 아스키 숫자들의 합을 비교하여 

더 큰 합을 가진 문자열을 반환하는  **get_strong_word**함수를 작성하시오 .

```python
get_strong_word('z', 'a') #=> 'z'
get_strong_word('tom', 'john') #=> 'john'
```

​			

```python
def get_strong_word(a, b):
    total_a = 0
    total_b = 0
    for i in a:
        total_a += ord(i)
    for j in b:
        total_b += ord(j)
    if total_a > total_b:
        return f"'{a}'"
    else:
        return f"'{b}'"


print(get_strong_word('z', 'a'))
print(get_strong_word('tom', 'john'))
```

**'z'**

**'john'**

