---

### 문제 1: 올바른 답을 선택하세요.

1. **(a)** `abc` 문자열을 매칭할 수 있는 정규 표현식은 무엇입니까?
   - i. `[a-z]*cc+`
   - ii. `(ab?)(a.*c)`
   - iii. `(az+)+.*`
   - iv. `ab+(bc)?c*`

   **답:** ii. `(ab?)(a.*c)`

   **설명:** `(ab?)(a.*c)`는 `abc` 문자열을 매칭할 수 있습니다. `ab?`는 `a` 또는 `ab`를 매칭하고, `a.*c`는 `a`로 시작하고 `c`로 끝나는 문자열을 매칭합니다.

2. **(b)** 다음 정규 표현식 `(ca*b|a[ab])+`에 의해 매칭될 수 있는 문자열은 무엇입니까?
   - i. `baca`
   - ii. `cabab`
   - iii. `bca`
   - iv. `ca`

   **답:** ii. `cabab`

   **설명:** `(ca*b|a[ab])+`는 `ca*b` 또는 `a`로 시작하는 문자열을 매칭합니다. `cabab`는 `ca*b`와 `a`로 구성되어 있어 매칭됩니다.

3. **(c)** 짝수 정수(2로 나누어 떨어지는)를 매칭할 수 있는 정규 표현식은 무엇입니까?
   - i. `([-+]?[0-9]+)%2`
   - ii. `-?[0-9]*[02468]$`
   - iii. `(.[0-8]/2)+`
   - iv. `([0-9]|0|2|4|6|8)+`

   **답:** ii. `-?[0-9]*[02468]$`

   **설명:** `-?[0-9]*[02468]$`는 음수나 양수로 끝나는 숫자가 0, 2, 4, 6, 8인 정수를 매칭합니다.

4. **(d)** Python에서 `with` 블록의 사용을 가장 잘 설명하는 것은 무엇입니까?
   - i. 블록을 벗어날 때 자동으로 관련된 리소스를 닫습니다.
   - ii. 파일 이름 대신 파일 내용과 함께 정규 표현식을 사용할 수 있습니다.
   - iii. `sys.argv` 리스트를 채워서 명령줄 인수에서 파일 이름을 읽을 수 있게 합니다.
   - iv. 프로그래머가 오류 처리 코드를 포함할 필요가 없도록 파일에서 잘못된 입력을 다시 읽는 과정을 자동화합니다.

   **답:** i. 블록을 벗어날 때 자동으로 관련된 리소스를 닫습니다.

   **설명:** `with` 블록은 파일이나 네트워크 연결과 같은 리소스를 자동으로 닫아줍니다.

5. **(e)** 리스트와 딕셔너리의 차이를 가장 잘 설명하는 것은 무엇입니까?
   - i. 리스트는 리스트 빌딩 패턴을 사용할 수 있지만, 딕셔너리에는 유사한 패턴이 없습니다.
   - ii. 딕셔너리는 사용자 정의 함수에 의해 생성된 데이터 대신 매칭된 정규 표현식에서 데이터를 추출하는 데 사용할 수 있습니다.
   - iii. 딕셔너리는 문자열만 저장합니다.
   - iv. 딕셔너리는 저장된 데이터를 참조하기 위해 인덱스 번호가 아닌 모든 유형의 데이터를 허용합니다.

   **답:** iv. 딕셔너리는 저장된 데이터를 참조하기 위해 인덱스 번호가 아닌 모든 유형의 데이터를 허용합니다.

   **설명:** 리스트는 순서가 있는 데이터를 인덱스로 참조하는 반면, 딕셔너리는 키를 사용하여 데이터를 참조할 수 있습니다.

---

### 문제 2: Python 코드를 작성하여 두 입력값 x와 y를 받아서 x+y/x-y를 출력하세요.

```python
def calculate(x, y):
    return (x + y) / (x - y)

# 예시 실행
x = 6
y = 4
result = calculate(x, y)
print(result)  # 출력: 5.0
```

**설명:** `calculate` 함수는 입력값 `x`와 `y`를 받아서 `(x + y) / (x - y)`를 계산하여 반환합니다. 예를 들어, `x`가 6이고 `y`가 4인 경우, 10 / 2 = 5가 됩니다.

---

### 문제 3: 파라미터로 정수 리스트를 받고, 5보다 작은 모든 숫자의 음수 값을 반환하는 Python 함수를 작성하세요.

```python
def get_negatives(lst):
    return [-num for num in lst if num < 5]

# 예시 실행
input_list = [-20, 17, 3, 9, 5, -40, 1]
result = get_negatives(input_list)
print(result)  # 출력: [20, -3, 40, -1]
```

**설명:** `get_negatives` 함수는 리스트의 모든 숫자를 순회하며 5보다 작은 숫자를 음수로 바꾸어 새로운 리스트로 반환합니다.

---

### 문제 4: 양의 정수 x를 받아서 x를 2로 나누는 첫 x번의 결과를 반환하는 Python 함수를 작성하세요.

```python
def divide_by_two(x):
    result = []
    for _ in range(x):
        result.append(x)
        x /= 2
    return result

# 예시 실행
x = 5
result = divide_by_two(x)
print(result)  # 출력: [5, 2.5, 1.25, 0.625, 0.3125]
```

**설명:** `divide_by_two` 함수는 주어진 `x`를 2로 나누는 과정을 반복하며, 결과를 리스트에 추가합니다. 이 과정을 `x`번 반복합니다.

---

### 문제 5: 문자열 x의 모든 'a'를 'b'로 대체하는 Python 함수를 작성하세요.

```python
def replace_a_with_b(x):
    return x.replace('a', 'b')

# 예시 실행
x = "apples and bananas"
result = replace_a_with_b(x)
print(result)  # 출력: "epples end benenes"
```

**설명:** `replace_a_with_b` 함수는 문자열의 모든 'a'를 'b'로 대체하여 새로운 문자열을 반환합니다.

---

### 문제 6: 두 부분으로 구성된 문제

(a) 문자열의 처음 세 글자만 남기는 함수 `shorten`을 작성하세요.

```python
def shorten(s):
    return s[:3]

# 예시 실행
print(shorten("banana"))  # 출력: "ban"
print(shorten("go"))  # 출력: "go"
```

**설명:** `shorten` 함수는 입력된 문자열의 처음 세 글자만 반환합니다. 문자열 길이가 3보다 짧으면 원래 문자열을 반환합니다.

(b) 문자열 리스트를 받아 각 문자열을 `shorten` 함수를 이용해 처리한 결과 리스트를 반환하는 함수 `shortened`를 작성하세요.

```python
def shortened(lst):
    return [shorten(s) for s in lst if len(s) > 3]

# 예시 실행
input_list = ['banana', 'go', 'hat', 'syrup', 'ground', 'a']
result = shortened(input_list)
print(result)  # 출력: ['ban', 'syr', 'gro']
```

**설명:** `shortened` 함수는 리스트의 각 문자열에 대해 길이가 3보다 큰 문자열만 `shorten` 함수를 적용하여 결과 리스트를 반환합니다.

---

### 문제 7: 1부터 100000까지의 숫자 중 각 자릿수가 오름차순인 정수 리스트를 생성하는 Python 코드를 작성하세요.

```python
result = []
for num in range(1, 100001):
    digits = str(num)
    if list(digits) == sorted(digits):
        result.append(num)

# 결과 출력
print(result)
```

**설명:** 숫자를 문자열로 변환하고, 각 자릿수를 비교하여 오름차순으로 정렬된 경우 리스트에 추가합니다.

---

### 문제 8: 주어진 함수에 대한 문서화 (docstring)를 작성하세요.

```python
def mystery(x, y):
    """
    주어진 리스트 x에서 중복되지 않는 요소들을 반환하는 함수.

    파라미터:
    x (list): 정수 리스트.
    y (int): 사용되지 않음.

    반환값:
    list: 중복되지 않는 요소들을 포함하는 리스트.

    예시:
    >>> mystery([1, 2, 2, 3, 4], 5)
    [1, 2, 3, 4]
    """
    z = []
    for i in range(x):
        if x[i] not in z:
            z.append(x[i])
    return z
```

**설명:** 함수 `mystery`는 입력된 리스트 `x`에서 중복되지 않는 요소들을 리스트로 반환합니다. `y` 파라미터는

 사용되지 않음을 명시합니다. 예시도 함께 제공하여 함수 사용법을 설명합니다.