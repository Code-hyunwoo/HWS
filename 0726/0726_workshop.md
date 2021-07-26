# :boom: 0726 Workshop

---



## 1. 평균 점수 구하기

key 값으로 과목명 , value 값으로 점수를 가지는 dictionary 를 전달 받아 , 전체 과목의 평균 점수를 반환하는 함수 get_dict_avg 함수를 작성하시오 .

​				

```python
get_dict_avg({
    'python' : 80,
    'algorithm' : 90,
    'django' : 89,
    'web' : 83
}) #= 85. 5
```

​				

```python
def get_dict_avg(X):
    total = 0
    for score in X.values():
        total += score
    return total / len(X)
```

​													

## 2. 혈액형 분류하기

여러 사람의 혈액형 (A, B, AB, O)에 대한 정보가 담긴 list를 전달 받아 , key는 혈액형의 종류 , value는 사람 수인 dictionary를 반환하는 **count_ blood** 함수를 작성하시오 .

​					

```python
count_blood([
    'A','B','A','O','AB','AB',
    'O','A','B','O','B','AB'
]) #=> {'A': 3, 'B' : 3, '0': 3, 'AB': 3}
```

​						

```python
def count_blood(X):
    data = {}
    data['A'] = X.count('A')
    data['B'] = X.count('B')
    data['o'] = X.count('O')
    data['AB'] = X.count('AB')
    return data
```

​									