# :boom:	0719 Homework

---

​		   

### 	1. python 예약어

python에서 사용할 수 없는 식별자(예약어)를 찾아 작성하시오.

```python
import keyword
print(keyword.kwlist)

# 다음의 키워드는 예약어로 사용할 수 없음
['False', 'None', 'True', '__peg_parser__', 'and', 'as', 'assert', 'async', 'await', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
```

​		     

​		     

### 	2. 실수 비교

아래와 같은 두 실수 값을 올바르게 비교하기 위한 코드를 작성하시오.

```python
num1 = 0.1 * 3
num2 = 0.3

#1. 
abs(num1-num2) <= 1e-10
#2.
import sys
print(abs(num1-num2) <= sys.float_info.epsilon)
#3.
import math
math.isclose(num1, num2)
```

​		  	  

​		   

### 	3. 이스케이프 시퀀스

(1) 줄 바꿈, (2) 탭, (3) 백슬래시를 의미하는 이스케이프 시퀀스를 작성하시오.

```python
(1) 줄바꿈 = \n
(2) 탭 = \t
(3) 백슬래시 = \\
```

​		   		 

​		     

### 	4. String Interpolation

'안녕, 철수야'를 string interpolation을 사용하여 출력하시오.

```python
name = '철수'

print(f"'안녕, {name}야'")

```

'안녕, 철수야'		 

​		    



### 	5. 형 변환

다음 중, 실행 시 오류가 발생하는 코드를 고르시오.

```python
str(1) #(1)
int('30') #(2)
int(5) #(3)
bool('50') #(4)
int('3.5') #(5)
```

​	정수 형식이 아닌 경우 타입 변환할 수 없음 따라서 (5)	  

​			  

### 	6. 네모 출력

두 개의 정수 n과 m이 주어졌을 때, 가로의 길이가 n, 세로의 길이가 m인 직사각형 형태를 별(*) 문자를 이용하여 출력하시오.

```python

n = int(input()) #5
m = int(input()) #9


print(m*("*"*n+"\n"))

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

### 	7. 이스케이프 시퀀스 응용

print()  함수를 한 번만 사용하여 다음 문장을 출력하시오.

```python
"파일은 c:\Windows\Users\내문서\Python에 저장이 되었습니다."
나는 생각했다. 'cd를 써서 git bash로 들어가 봐야지.'

print('\"파일은 c:\\Windows\\users\\내문서\\Python에 저장이 되었습니다.\"\n나는 생각했다. \'cd를 써서 git bash로 들어가 봐야지.\'')
```

"파일은 c:\Windows\users\내문서\Python에 저장이 되었습니다."
나는 생각했다. 'cd를 써서 git bash로 들어가 봐야지.'			  

​			  

### 	8.근의 공식

다음은 이차 방정식의 근을 찾는 수식이다. 이를 파이썬 코드로 작성하시오.

```python
# ax^2+bx+c=0 의 이차방적식의 근(X1,X2)을 구하는 공식

X1 = (-b+(b**2-4*a*c)**(0.5))/(2*a)
X2 = (-b-(b**2-4*a*c)**(0.5))/(2*a)
```

