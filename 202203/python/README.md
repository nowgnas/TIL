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

### **2022 03 06**

## Python 가상환경 만들기

Dokcker를 사용하기 위한 python 가상환경을 구축해 보려고 한다. python이 설치된 상황에서 가상환경을 만들어 보자.

```shell
python3 -m venv venv
```

python3를 설치하여 `venv`라는 이름의 `venv`가상환경을 만든다.

### 가상환경 실행하기

```shell
# linux
source venv/bin/activate

# windows
venv/Scripts/activate.bat
```

각 운영체제에서 가상환경을 활성화 하는 명령어이다.

### 설치된 가상환경의 패키지 확인

```shell
pip3 freeze
```

가상환경이 설치된 후 어떤 라이브러리가 설치되어 있는지 확인할 수 있는 명령어다. `pip3`는 python3을 설치하고 사용할 수 있다.
