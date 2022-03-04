# Python

## Python 내장 함수 정리하기

### **2022 03 04**

## itertools

```python
arr = [1, 2, 3]
comnbArr = list(itertools.permutations(arr, 2))
# [(1, 2), (1, 3), (2, 1), (2, 3), (3, 1), (3, 2)]

comnbArr = list(itertools.combinations(arr, 2))
# [(1, 2), (1, 3), (2, 3)]
```

- `combinations`은 리스트 원소들의 조합을 반환하고 `permutation`는 리스트의 원소들을 이용한 순차적 조합을 반환한다.

---
