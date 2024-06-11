---

### 문제 1: 올바른 답을 선택하세요.

1. **(a)** `abc` 문자열을 매칭할 수 있는 정규 표현식은 무엇입니까?
   - i. `[a-z]*cc+`
   - ii. `(ab?)(a.*c)`
   -

파일에 포함된 문제들을 풀고 각각의 해답을 한국어로 설명하겠습니다.

---

### 문제 1: 올바른 답을 선택하세요.

1. **(a)** `abc` 문자열을 매칭할 수 있는 정규 표현식은 무엇입니까?
   - i. `[a-z]*cc+`
   - ii. `(ab?)(a.*c)`
   - iii. `(az*)+.*`
   - iv. `ab+(bc)?`

   **답:** ii. `(ab?)(a.*c)`

   **설명:** `(ab?)(a.*c)`는 `abc` 문자열을 매칭할 수 있습니다. `ab?`는 `a` 또는 `ab`를 매칭하고, `a.*c`는 `a`로 시작하고 `c`로 끝나는 문자열을 매칭합니다.

2. **(b)** Python에서 `with` 블록의 사용을 가장 잘 설명하는 것은 무엇입니까?
   - i. 블록을 벗어날 때 자동으로 관련된 리소스를 닫습니다.
   - ii. 파일 이름 대신 파일 내용과 함께 정규 표현식을 사용할 수 있습니다.
   - iii. `sys.argv` 리스트를 채워서 명령줄 인수에서 파일 이름을 읽을 수 있게 합니다.
   - iv. 프로그래머가 오류 처리 코드를 포함할 필요가 없도록 파일에서 잘못된 입력을 다시 읽는 과정을 자동화합니다.

   **답:** i. 블록을 벗어날 때 자동으로 관련된 리소스를 닫습니다.

   **설명:** `with` 블록은 파일이나 네트워크 연결과 같은 리소스를 자동으로 닫아줍니다.

3. **(c)** 리스트와 딕셔너리의 차이를 가장 잘 설명하는 것은 무엇입니까?
   - i. 리스트는 리스트 빌딩 패턴을 사용할 수 있지만, 딕셔너리에는 유사한 패턴이 없습니다.
   - ii. 딕셔너리는 사용자 정의 함수에 의해 생성된 데이터 대신 매칭된 정규 표현식에서 데이터를 추출하는 데 사용할 수 있습니다.
   - iii. 딕셔너리는 문자열만 저장합니다.
   - iv. 딕셔너리는 저장된 데이터를 참조하기 위해 인덱스 번호가 아닌 모든 유형의 데이터를 허용합니다.

   **답:** iv. 딕셔너리는 저장된 데이터를 참조하기 위해 인덱스 번호가 아닌 모든 유형의 데이터를 허용합니다.

   **설명:** 리스트는 순서가 있는 데이터를 인덱스로 참조하는 반면, 딕셔너리는 키를 사용하여 데이터를 참조할 수 있습니다.

---

### 문제 2: 두 부분으로 구성된 문제

(a) 문자열의 처음 세 글자만 남기는 함수 `shorten`을 작성하세요. 

```python
def shorten(s: str) -> str:
    """
    주어진 문자열의 처음 세 글자만 반환하는 함수.
    
    파라미터:
    s (str): 입력 문자열
    
    반환값:
    str: 처음 세 글자를 포함하는 문자열 또는 원래 문자열
    
    예시:
    >>> shorten('banana')
    'ban'
    >>> shorten('go')
    'go'
    """
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

### 문제 3: 두 개의 명령줄 인수를 받아서 특정 계산을 수행하는 Python 프로그램을 작성하세요.

```python
import sys

def main():
    if len(sys.argv) != 3:
        print("Bad input")
        return

    try:
        x = int(sys.argv[1])
        y = int(sys.argv[2])
        if x < 0 or y < 0:
            raise ValueError
    except ValueError:
        print("Bad input")
        return

    total_sum = sum(i ** y for i in range(x + 1))
    print(total_sum)

if __name__ == "__main__":
    main()
```

**설명:** 이 프로그램은 두 개의 명령줄 인수를 받아 각각 `x`와 `y`로 변환합니다. `x`와 `y`가 양의 정수인 경우, 0부터 `x`까지의 각 정수를 `y`제곱한 값을 더하여 출력합니다. 인수가 잘못된 경우 "Bad input"을 출력합니다.

---

### 문제 4: `abc.txt` 파일의 각 줄에서 괄호 사이의 문자열을 추출하여 출력하는 Python 프로그램을 작성하세요.

```python
def extract_parentheses(filename):
    with open(filename, 'r') as file:
        for line in file:
            start = line.find('(') + 1
            end = line.find(')')
            if start != -1 and end != -1:
                print(line[start:end])

# 예시 실행
extract_parentheses('abc.txt')
```

**설명:** `extract_parentheses` 함수는 주어진 파일에서 각 줄의 괄호 사이에 있는 문자열을 추출하여 출력합니다. `start`와 `end`를 사용하여 괄호 위치를 찾고, 해당 부분 문자열을 출력합니다.

---

### 문제 5: 문자열 리스트에서 최소 3번 이상 나타나는 문자열을 반환하는 Python 함수를 작성하세요.

```python
def find_frequent_strings(lst):
    from collections import Counter
    count = Counter(lst)
    return [item for item, freq in count.items() if freq >= 3]

# 예시 실행
input_list = ['cart', 'hat', 'hat', 'apple', 'hat', 'banana', 'cart', 'hat', 'apple', 'cart']
result = find_frequent_strings(input_list)
print(result)  # 출력: ['cart', 'hat']
```

**설명:** `find_frequent_strings` 함수는 `Counter`를 사용하여 리스트에서 각 문자열의 빈도를 계산하고, 빈도가 3 이상인 문자열만 반환합니다.

---

### 문제 6: 텍스트 파일의 각 줄을 읽어 첫 번째로 숫자를 포함하지 않은 줄의 번호를 출력하는 Python 프로그램을 작성하세요.

```python
import sys

def find_first_non_numeric_line(filename):
    with open(filename, 'r') as file:
        for line_number, line in enumerate(file, 1):
            if not any(char.isdigit() for char in line):
                print(line_number)
                return

# 예시 실행
find_first_non_numeric_line(sys.argv[1])
```

**설명:** `find_first_non_numeric_line` 함수는 파일의 각 줄을 읽으면서 숫자를 포함하지 않은 첫 번째 줄의 번호를 출력합니다. `enumerate`를 사용하여 줄 번호를 추적하고, 숫자가 없는 줄을 찾으면 해당 번호를 출력합니다.

---