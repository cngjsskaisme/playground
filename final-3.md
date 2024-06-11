### 문제 1: 올바른 답을 선택하세요.

1. **(a)** 리스트와 딕셔너리의 차이를 가장 잘 설명하는 것은 무엇입니까?
   - i. 리스트는 리스트 빌딩 패턴을 사용할 수 있지만, 딕셔너리에는 유사한 패턴이 없습니다.
   - ii. 딕셔너리는 사용자 정의 함수에 의해 생성된 데이터 대신 매칭된 정규 표현식에서 데이터를 추출하는 데 사용할 수 있습니다.
   - iii. 딕셔너리는 문자열만 저장합니다.
   - iv. 딕셔너리는 저장된 데이터를 참조하기 위해 인덱스 번호가 아닌 모든 유형의 데이터를 허용합니다.

   **답:** iv. 딕셔너리는 저장된 데이터를 참조하기 위해 인덱스 번호가 아닌 모든 유형의 데이터를 허용합니다.

   **설명:** 리스트는 순서가 있는 데이터를 인덱스로 참조하는 반면, 딕셔너리는 키를 사용하여 데이터를 참조할 수 있습니다.

2. **(b)** 2와 3을 명령줄 인수로 주어 실행된 Python 프로그램에서 5를 출력하는 것은 무엇입니까?
   - i. `print(sum(sys.argv))`
   - ii. `print(int(sys.argv[0] + int(sys.argv[1])))`
   - iii. `print(int(sys.argv[0]) + int(sys.argv[1]))`
   - iv. `print(int(sys.argv[1]) + int(sys.argv[2]))`
   - v. `print(int(sys.argv[1] + int(sys.argv[2])))`

   **답:** iv. `print(int(sys.argv[1]) + int(sys.argv[2]))`

   **설명:** 명령줄 인수는 문자열로 전달되므로 이를 정수로 변환한 후 더해야 합니다. 인수 `sys.argv[1]`과 `sys.argv[2]`를 더하면 2 + 3 = 5가 됩니다.

3. **(c)** 재귀에 대한 설명 중 틀린 것은 무엇입니까?
   - i. 루프로 할 수 있는 모든 것을 재귀로도 할 수 있습니다.
   - ii. 재귀 함수에는 최소한 하나의 정수 파라미터가 필요합니다.
   - iii. 재귀는 항상 함수 호출을 포함합니다.
   - iv. 팩토리얼 함수는 재귀로 쉽게 구현할 수 있습니다.

   **답:** ii. 재귀 함수에는 최소한 하나의 정수 파라미터가 필요합니다.

   **설명:** 재귀 함수는 반드시 정수 파라미터가 필요하지 않으며, 다른 유형의 파라미터를 사용할 수 있습니다.

---

### 문제 2: Python 코드를 작성하여 두 입력값 x와 y를 받아서 (x+y)/(x-y)를 출력하세요.

```python
def calculate(x, y):
    return (x + y) / (x - y)

# 예시 실행
x = 6.0
y = 4.0
result = calculate(x, y)
print(result)  # 출력: 5.0
```

**설명:** `calculate` 함수는 입력값 `x`와 `y`를 받아서 `(x + y) / (x - y)`를 계산하여 반환합니다. 예를 들어, `x`가 6이고 `y`가 4인 경우, 10 / 2 = 5가 됩니다.

---

### 문제 3: 파라미터로 정수 리스트를 받고, 음수인 숫자의 제곱을 반환하는 Python 함수를 작성하세요.

```python
def negative_squares(lst):
    """
    주어진 리스트에서 음수인 숫자의 제곱을 반환하는 함수.

    파라미터:
    lst (list of int): 정수 리스트

    반환값:
    list of int: 음수 숫자의 제곱 리스트

    예시:
    >>> negative_squares([-2, 17, 3, 0, 5, -1, -5])
    [4, 1, 25]
    """
    return [x**2 for x in lst if x < 0]

# 예시 실행
input_list = [-2, 17, 3, 0, 5, -1, -5]
result = negative_squares(input_list)
print(result)  # 출력: [4, 1, 25]
```

**설명:** `negative_squares` 함수는 리스트의 각 요소를 순회하면서 음수인 숫자의 제곱을 새로운 리스트로 반환합니다.

---

### 문제 4: 두 개의 명령줄 인수를 받아 특정 계산을 수행하는 Python 프로그램을 작성하세요.

```python
import sys

def main():
    x = int(sys.argv[1])
    y = int(sys.argv[2])
    total_sum = sum(i ** y for i in range(x))
    print(total_sum)

if __name__ == "__main__":
    main()
```

**설명:** 이 프로그램은 두 개의 명령줄 인수를 받아 각각 `x`와 `y`로 변환합니다. 0부터 `x-1`까지의 각 정수를 `y`제곱한 값을 더하여 출력합니다.

---

### 문제 5: 리스트와 양의 정수 n을 받아서 리스트의 처음 n개의 요소를 반환하는 Python 함수를 작성하세요.

```python
def take(lst, n):
    """
    주어진 리스트의 처음 n개의 요소를 반환하는 함수.

    파라미터:
    lst (list): 입력 리스트
    n (int): 반환할 요소의 수

    반환값:
    list: 처음 n개의 요소를 포함하는 새로운 리스트

    예시:
    >>> take([5, 'a', False], 2)
    [5, 'a']
    """
    return lst[:n]

# 예시 실행
result = take([5, 'a', False], 2)
print(result)  # 출력: [5, 'a']
```

**설명:** `take` 함수는 입력된 리스트의 처음 n개의 요소를 반환합니다. 원본 리스트는 수정되지 않습니다.

---

### 문제 6: 리스트와 두 정수를 받아 특정 값을 다른 값으로 대체하는 Python 함수를 작성하세요.

```python
def subst(lst, search, replace):
    """
    주어진 리스트에서 특정 값을 다른 값으로 대체하는 함수.

    파라미터:
    lst (list of int): 입력 리스트
    search (int): 찾을 값
    replace (int): 대체할 값

    반환값:
    list of int: 대체된 값을 포함하는 새로운 리스트

    예시:
    >>> subst([5, -3, 7, 9, -3, 1, -4, -3, -2], -3, 0)
    [5, 0, 7, 9, 0, 1, -4, 0, -2]
    """
    return [replace if x == search else x for x in lst]

# 예시 실행
result = subst([5, -3, 7, 9, -3, 1, -4, -3, -2], -3, 0)
print(result)  # 출력: [5, 0, 7, 9, 0, 1, -4, 0, -2]
```

**설명:** `subst` 함수는 리스트에서 특정 값을 찾아 대체한 새로운 리스트를 반환합니다. 원본 리스트는 수정되지 않습니다.

---

### 문제 7: 두 양의 정수를 받아 범위 내의 모든 2의 거듭제곱을 반환하는 Python 함수를 작성하세요.

```python
def pow2(x, y):
    """
    주어진 범위 내의 모든 2의 거듭제곱을 반환하는 함수.

    파라미터:
    x (int): 범위의 하한값 (포함)
    y (int): 범위의 상한값 (포함)

    반환값:
    list of int: 범위 내의 2의 거듭제곱 리스트

    예시:
    >>> pow2(4, 20)
    [4, 8, 16]
    """
    result = []
    power = 1
    while power < x:
        power *= 2
    while power <= y:
        result.append(power)
        power *= 2
    return result

# 예시 실행
result = pow2(4, 20)
print(result)  # 출력: [4, 8, 16]
```

**설명:** `pow2` 함수는 범위 내의 2의 거듭제곱을 계산하여 리스트로 반환합니다.

---

### 문제 8: 리스트가 두 개의 같은 길이의 절반으로 구성되어 있는지 확인하는 Python 함수를 작성하세요.

```python
def is_halves(lst):
    """
    리스트가 두 개의 같은 길이의 절반으로 구성되어 있는지 확인하는 함수.

    파라미터:
    lst (list of int): 입력 리스트

    반환값:
    bool: 리스트가 두 절반으로 구성되어 있으면 True, 아니면 False

    예시:
    >>> is_halves([4, 4, 4, 2, 2, 2])
    True
    >>> is_halves([])
    True
    >>> is_halves([1,

 1, 1, 9, 9, 8])
    False
    >>> is_halves([4, 4, 4, 4, 4, 2, 2, 2])
    False
    """
    length = len(lst)
    if length % 2 != 0:
        return False
    half = length // 2
    return lst[:half] == [lst[0]] * half and lst[half:] == [lst[half]] * half

# 예시 실행
print(is_halves([4, 4, 4, 2, 2, 2]))  # 출력: True
print(is_halves([]))  # 출력: True
print(is_halves([1, 1, 1, 9, 9, 8]))  # 출력: False
print(is_halves([4, 4, 4, 4, 4, 2, 2, 2]))  # 출력: False
```

**설명:** `is_halves` 함수는 리스트가 두 개의 같은 길이의 절반으로 구성되어 있는지 확인합니다. 각 절반의 요소가 동일하면 `True`를 반환하고, 그렇지 않으면 `False`를 반환합니다.

---

### 문제 9: 두 정수를 입력받아 첫 번째 정수의 배수 중 "좋은" 숫자만 출력하는 Python 프로그램을 작성하세요.

```python
import sys

def main():
    a = int(sys.argv[1])
    b = int(sys.argv[2])
    good_numbers = good([i for i in range(0, b) if i % a == 0])
    print(good_numbers)

if __name__ == "__main__":
    main()
```

**설명:** 이 프로그램은 두 개의 정수를 입력받아 첫 번째 정수의 배수 중 "좋은" 숫자만 출력합니다. `good` 함수는 이미 정의되어 있다고 가정합니다.

---

### 보너스 문제: 텍스트 파일의 각 줄에서 가장 큰 정수에 해당하는 문자열을 출력하는 Python 프로그램을 작성하세요.

```python
import sys

def find_largest_string(filename):
    max_int = None
    result_str = None
    with open(filename, 'r') as file:
        for line in file:
            parts = line.strip().split(',')
            for part in parts:
                try:
                    number = int(part)
                    string = parts[1] if parts.index(part) == 0 else parts[0]
                    if max_int is None or number > max_int:
                        max_int = number
                        result_str = string
                except ValueError:
                    continue
    if result_str:
        print(result_str)

# 예시 실행
find_largest_string('input.txt')
```

**설명:** `find_largest_string` 함수는 주어진 파일에서 각 줄을 읽어 가장 큰 정수에 해당하는 문자열을 출력합니다. 각 줄은 쉼표로 구분된 두 개의 필드를 가지고 있습니다.