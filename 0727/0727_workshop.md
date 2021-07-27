# :boom: Workshop

---

​		

## 1. 무엇이 중복일까

문자열을 전달 받아 해당 문자열에서 중복해서 나타난 문자들을 담은 list를 반환하는 **duplicated_letters**함수를 작성하시오 .

```python
duplicated_letters('apple') #=['p']
duplicated_letters('banana') #=['a','n']
```

​			

```python
def duplicated_letters(words):
    answer = set()
    for word in words:
        if words.count(word)>1:
            answer.add(word)
    return list(answer)       
```

**['p']**

**['n', 'a']**

​							

## 2. 소대소대

문자열을 전달 받아 해당 문자열을 소문자와 대문자가 번갈아 나타나도록 변환하여 반환하는 **low_and_up** 함수를 작성하시오 . 이때 , 전달 받는 문자열은 알파벳으로만 구성된다 .

```python
low_and_up('apple') #=> aPpLe
low_and_up('banana') #=> bAnAnA
```

​			

```python
def low_and_up(words):
  new_words = ''
  for idx in range(len(words)):
      if idx % 2:
          word = words[idx].upper()
          new_words += word
      else:
          word = words[idx].lower()
          new_words += word
  return new_words

print(low_and_up('apple')) 
print(low_and_up('banana'))
```

**aPpLe**

**bAnAnA**							

​											

## 3. 숫자의 의미

0부터 9까지로 이루어진 list를 전달 받아 , 연속적으로 나타나는 숫자는 하나만 남기고 제거한 list를 반환하는 **lonely** 함수를 작성하시오 . 이때 , 제거된 후 남은 수들이 담 긴 list의 요소들은 기존의 순서를 유지해야 한다 .

```python
lonely([1, 1, 3, 3, 0, 1, 1]) #=> [1,3,0,1]
lonely([4, 4, 4, 3, 3]) #=> [4, 3]
```

​					

```python
# 1 번째 방법
def lonely(X):
    answer = [X[0]]
    for i in range(1,len(X)):
        if X[i] != X[i-1]:
            answer.append(X[i])
    return answer


# 2 번째 방법
def lonely(words):
  res= [words[0]]
  for i in words:
      if res[-1] ==i:
        continue
      else:
        res.append(i)
  return res
```

**[1, 3, 0, 1]**

**[4, 3]**	

​			



