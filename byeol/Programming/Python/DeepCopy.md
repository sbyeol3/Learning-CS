# Python : 가변성과 불변성

## 객체, 가변성과 불변성
Python의 모든 데이터 타입들은 객체(object)다.

객체는 `가변(mutable) 객체`와 `불변(immutable) 객체`로 나뉜다. 
불변 객체는 객체 생성 이후 값을 변경할 수 없는 object를 의미하고, 가변 객체는 반대로 값을 변경할 수 있는 object를 의미한다.
대부분의 경우에서 불변 객체 타입이 가변 객체 타입보다 효율적이다.

분류 | 데이터 타입
--- | ---
가변(mutable) | list, set, dict
불변(immutable) | int, float, bool, tuple, string, unicode

[참고 링크](http://foobarnbaz.com/2012/07/08/understanding-python-variables/)

---

## 불변(immutable) 객체
```python
a = 3
b = 5
c = 7
print(id(a),id(b),id(c))
# (140468310543096, 140468310543048, 140468310543000)
```
여기서 변수 c의 값을 수정하게 되면,
```python
...
c = 10
print(id(a),id(b),id(c))
# (140468310543096, 140468310543048, 140468310542928)
```
c는 원래 정수 7이라는 객체의 주소(14...3000)를 가리키고 있었는데
10이라는 값을 다시 주면서 10 객체의 주소를 가리키면서 id 값이 변경된 것이다. 만약 c에 3이라는 값을 할당하면 a와 동일한 객체의 주소를 가리킨다.<br>

  

## 가변(mutable) 객체
가변 객체를 사용할 때 주의해야 하는 점은 가변 객체를 복사하는 경우,<br>
예를 들어 a = b일 때 a에 b의 값 자체를 복사해서 넣는 게 아니라 b가 가리키는 곳을 a가 가리키게 되는 것이다.

코드로 확인을 해보자.
```python
example = [1,2,3,4,5]
copy = example
print(id(example), example)
# (4502187904, [1, 2, 3, 4, 5])
print(id(copy), copy)
# (4502187904, [1, 2, 3, 4, 5])

example.pop() 
print(id(example), example)
# (4502187904, [1, 2, 3, 4])
print(id(copy), copy)
# (4502187904, [1, 2, 3, 4])
```
copy는 example의 배열 값 자체를 복사하지 않고 가리키는 주소를 복사했으므로example의 값이 변경되면 copy도 같은 값을 가리키면서 값이 변경된다.
-> 이러한 복사를 `얕은 복사(shallow copy)`라고 한다.

<br>

## 깊은 복사 (deep copy)
가리키고 있는 주소를 복사하는 것이 아닌 값 자체를 복사하는 것을 `'깊은 복사(deep copy)'`라고 한다. 

* __리스트 (list)__
  ```python
    listOrigin = [7,17,27]
    listCopy = listOrigin[:]
    listCopy2 = list(listOrigin)
    print(id(listOrigin),id(listCopy),id(listCopy2))
    # (4512706432, 4512850144, 4512923944)

    listOrigin.pop()
    print(listOrigin,listCopy,listCopy2)
    #([7, 17], [7, 17, 27], [7, 17, 27])
  ```

* __셋 (set), 딕셔너리 (dict)__
  ```python
  # Set
    like = {'bancha','yeoncha','hyuga'}
    happy = set(like) # or like.copy()
    happy.remove('bancha')
    print(like,happy)
    # > (set(['hyuga', 'bancha', 'yeoncha']), set(['hyuga', 'yeoncha']))

    # ----> shallow copy
    happiness = like
    happiness.remove('bancha')
    print(like,happiness)
    # > (set(['hyuga', 'yeoncha']), set(['hyuga', 'yeoncha']))
  ```
  ```python
  # dict
    hate = {"tomorrow":"choolgun","need":"holiday"}
    hyeom = hate.copy()
    hate.pop("need")
    print(hate,hyeom)
    # ({'tomorrow': 'choolgun'}, {'need': 'holiday', 'tomorrow': 'choolgun'})
  ```
* 기타 객체
    * 이외 객체에서 깊은 복사를 할 때는 copy 모듈을 사용한다.
  ```python
    import copy
    str = "deep copy"
    newStr = str.deepcopy(str)
  ```