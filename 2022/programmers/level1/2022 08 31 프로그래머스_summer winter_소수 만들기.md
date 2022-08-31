# 2022/08/31 프로그래머스_summer/winter_소수 만들기

[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/12977)

### **1. 문제 설명**

주어진 숫자 중 3개의 수를 더했을 때 소수가 되는 경우의 개수를 구하려고 합니다. 숫자들이 들어있는 배열 nums가 매개변수로 주어질 때, nums에 있는 숫자들 중 서로 다른 3개를 골라 더했을 때 소수가 되는 경우의 개수를 return 하도록 solution 함수를 완성해주세요.

---

### **2. 제한사항**

- nums에 들어있는 숫자의 개수는 3개 이상 50개 이하입니다.
- nums의 각 원소는 1 이상 1,000 이하의 자연수이며, 중복된 숫자가 들어있지 않습니다.

---

### **3. 입출력 예**

| nums | result |
| --- | --- |
| [1,2,3,4] | 1 |
| [1,2,7,6,4] | 4 |

---

### 4. 코드

```python
import math
import itertools as it

def find_prime(x):
        # 2부터 x의 제곱근까지의 모든 수를 확인하며
    for i in range(2, int(math.sqrt(x)) + 1):
        # x가 해당 수로 나누어떨어진다면
        if x % i == 0:
            return False # 소수가 아님
    return True # 소수임

def solution(nums):
    sum_prime = 0
    answer = list(map(sum, it.combinations(nums, 3)))
    for a in answer:
        if find_prime(a):
            sum_prime += 1
    return sum_prime
```