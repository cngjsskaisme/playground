1. 객관식 문제 풀이 설명

(a) ii. (ab?)(a.*c)
이 정규식은 'ab' 또는 'a'에 이어 임의의 문자가 0번 이상 나온 후 'c'가 오는 패턴을 매칭합니다. 따라서 'abc'를 매칭할 수 있습니다.

(b) i. It automatically closes the resource associated with it when execution leaves the block
with 블록은 파일, 네트워크 소켓 등의 리소스를 안전하게 활용할 수 있도록 해줍니다. with 블록을 벗어나면 자동으로 해당 리소스를 close합니다.

(c) iv. Dictionaries allow any type of data to be used to refer to stored data, rather than requiring an index number
딕셔너리는 인덱스 번호가 아닌 키(key)를 통해 값에 접근할 수 있습니다. 리스트는 인덱스로만 접근 가능합니다. 또한 딕셔너리의 키로는 숫자, 문자열 등 다양한 자료형을 사용할 수 있습니다.

2. 함수 작성 문제 풀이

(a) 문자열 길이가 3 이상이면 앞 3자리만 반환하고, 그렇지 않으면 원래 문자열을 반환하는 shorten 함수입니다.

```python
def shorten(str_input):
    """
    Returns the first 3 characters of the input string.
    If the string is shorter than 3 characters, returns the original string.

    Args:
        str_input (str): Input string to be shortened

    Returns:
        str: Shortened string or original string if shorter than 3 characters
    """
    if len(str_input) < 3:
        return str_input
    else:
        return str_input[:3]
```

(b) 문자열 리스트를 받아 문자열 길이가 3 이상인 경우에만 shorten 함수를 적용한 새 리스트를 반환하는 shortened 함수입니다.

```python
def shortened(str_list):
    result = []
    for s in str_list:
        if len(s) > 3:
            result.append(shorten(s))
        else:
            result.append(s)
    return result
```

3. 커맨드라인 인자를 사용하는 프로그램 작성

이 프로그램은 커맨드라인에서 두 개의 정수 인자를 받아 첫번째 인자부터 두번째 인자까지의 제곱의 합을 계산하여 출력합니다.

```python
import sys

if len(sys.argv) != 3:
    print('Bad input')
else:
    try:
        x = int(sys.argv[1])
        y = int(sys.argv[2])
        if x < 0 or y < 0:
            print('Bad input')
        else:
            sum = 0
            for i in range(x, y+1):
                sum += i**2
            print(sum)
    except ValueError:
        print('Bad input')
```

4. 파일에서 괄호 안 내용만 출력하는 프로그램 작성

이 프로그램은 'abc.txt' 파일을 읽어 각 라인에서 괄호 안에 있는 내용만 출력합니다.

```python
with open('abc.txt', 'r') as file:
    for line in file:
        start = line.find('(')
        end = line.find(')')
        if start != -1 and end != -1:
            print(line[start+1:end])
```

5. 문자열 리스트에서 3번 이상 등장하는 문자열 찾기

이 함수는 문자열 리스트를 받아 3번 이상 등장하는 문자열들만 모아 새 리스트로 반환합니다.

```python
def find_frequent_strings(str_list):
    freq = {}
    for s in str_list:
        if s in freq:
            freq[s] += 1
        else:
            freq[s] = 1
    
    result = []
    for s, count in freq.items():
        if count >= 3:
            result.append(s)
    
    return result
```

6. 숫자가 없는 첫번째 라인 번호 출력하는 프로그램

이 프로그램은 커맨드라인 인자로 파일명을 받아 숫자가 없는 첫번째 라인의 번호를 출력합니다.

```python
import sys
import re

filename = sys.argv[1]
with open(filename, 'r') as file:
    line_num = 1
    for line in file:
        if not re.search(r'\d', line):
            print(line_num)
            break
        line_num += 1
```

이 문제들은 파이썬 기초 문법, 함수 작성, 파일 입출력, 정규식 등 다양한 개념을 활용하고 있습니다. 각 문제를 주의 깊게 읽고 핵심 요구사항을 파악한 다음 적절한 코드를 작성하는 연습이 필요합니다.