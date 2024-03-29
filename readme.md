# Tips of python

## min, max heap
python의 heapq는 min heap을 지원함. 그래서 max heap으로 만드려면 조금 응용이 필요.
list에 tuple을 넣어서 음수로 첫인자를 넣으면 max_heap이 구성됨.

```python
from sys import stdin
from heapq import heappush, heappop

k = heappop(h)[1]
heappush(h, (-a, a))
```

## Class 주의
container 사용시 class를 사용할때가 있는데, task 100만개 차이가 1초가까이 발생한다.
가능하면 list로 코드를 작성하자.

<img src="https://user-images.githubusercontent.com/18378009/166109002-71187a41-baab-4fe0-bd39-70c2a40521ab.png" alt="image" width=60% height=60%>

## split 주의
split은 sep 값에 아무것도 넣지 않으면 모든 공백에 대해서 처리를 해준다. 
그래서 아래의 예시는 결과가 다르게 나온다.

```python
word1 = input().strip().split(" ")
word2 = input().strip().split()
print(word1)
print(word2)
```

```text
['']
[]
```

## list-element index 호출
- list.index(element)
ex) list = ['a','b','c']
    list.index('a') ==> 0 호출

## 시간 측정
- cProfile, pstats module을 사용하면 함수의 속도를 측정할 수 있다.

```python
from cProfile import Profile
from pstats import Stats

profiler = Profile()
profiler.runcall(main)

stats = Stats(profiler)
stats.strip_dirs()
stats.sort_stats('cumulative')
stats.print_stats()
```

## 배열 입력 받기
```python
board = []
for _ in range(n):
    # 12345
    board.append(list(map(int, input())))
    # 1 2 3 4 5
    board.append(list(map(int, input().split())))
```

## 입력 빠르게 받기 
```python
from sys import stdin
board = list(map(int,stdin.readline().split('')))
```

## 문자열 역순 출력
```python
board = ['a', 'b', 'c', 'd', 'e']
print(board[::-1])
```

## ascii
```python
ord('a')
chr(ord('a'))
```

## 순열, 조합
```python
# permutations : iterator 원소들로 길이 N인 순열을 생성. 두번째 인자를 전달하지 않으면 iterator 개수가 default 로 들어가는 듯
it = itertools.permutations([1,2,3,4], 2)
print(list(it))

it = itertools.permutations([1,2,3,4], 4)
print(list(it))

# combinations : 길이 N인 조합을 만들어준다.
it = itertools.combinations([1,2,3,4],2)
print(list(it))

# combinations_with_replacement : combination과 동일하지만 중복을 포함한다. 즉, 중복조합을 만들어준다.
it = itertools.combinations_with_replacement([1,2,3,4],2)
print(list(it))
```

```text
[(1, 2), (1, 3), (1, 4), (2, 1), (2, 3), (2, 4), (3, 1), (3, 2), (3, 4), (4, 1), (4, 2), (4, 3)]
[(1, 2, 3, 4), (1, 2, 4, 3), (1, 3, 2, 4), (1, 3, 4, 2), (1, 4, 2, 3), (1, 4, 3, 2), (2, 1, 3, 4), (2, 1, 4, 3), (2, 3, 1, 4), (2, 3, 4, 1), (2, 4, 1, 3), (2, 4, 3, 1), (3, 1, 2, 4), (3, 1, 4, 2), (3, 2, 1, 4), (3, 2, 4, 1), (3, 4, 1, 2), (3, 4, 2, 1), (4, 1, 2, 3), (4, 1, 3, 2), (4, 2, 1, 3), (4, 2, 3, 1), (4, 3, 1, 2), (4, 3, 2, 1)]
[(1, 2), (1, 3), (1, 4), (2, 3), (2, 4), (3, 4)]
[(1, 1), (1, 2), (1, 3), (1, 4), (2, 2), (2, 3), (2, 4), (3, 3), (3, 4), (4, 4)]
```


# Tips
## 소수 구하기
- 소수를 구할때는 2부터 sqrt(N) 까지만 순환해도 찾을 수 있다.
  - 2 * 4 를 체크하는 것과 4 * 2를 체크하는 것은 동일하기 때문

