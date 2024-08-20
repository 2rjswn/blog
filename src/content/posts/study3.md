---
title: 다이나믹 프로그래밍
published: 2024-08-20
tags: [Algorithm]
category: study
draft: false
---
# 동적 프로그래밍
복잡한 문제를 작은 문제들로 분해하여 해결하는 알고리즘 기법이다.      
분할정복과 비슷하다는데 차이점은 같은 계산을 여러번 해야할 때 한번만 계산하고 메모이제이션하여 재활용을 한다는 점이다.         
## 동적 프로그래밍의 조건
- 최적 부분 구조 : 큰 문제의 최적해는 작은 하위 문제들의 최적해를 결합하여 얻어진다. 
- 중복되는 하위 문제 : 하위 문제들을 반복해서 사용할 때 동적 프로그램을 적용 할 수 있다. 
## 메모이제이션
함수의 실행 결과를 캐시에 저장해 같은 문제가 다시 발생했을 때 저장된 값을 불러와서 재활용 하는 기법이다.         
### 메모이제이션의 조건
1. 중복되는 하위 문제가 있어야한다.
2. 작은 함수들이 최적화 하여 큰 문제를 최적화 할 수 있어야한다.
3. 함수가 동일한 입력에 항상 동일한 출력을 반한해야 한다.
## 동적 프로그래밍 접근법
1. Bottom-Up        
작은 문제들을 먼저 해결 한 후 그 결과를 이용해 더 큰 문제를 해결하는 방식
2. Top-Down (메모이제이션)          
하위 문제의 답이 이미 계산되었는지 확인 후 없다면 계산하여 저장하고 있다면 동일한 하위 문제가 필요할 때 저장된 값을 불러온다.
## 예시
피보나치 수열을 재귀함수로 계산하면 같은 값에 대한 계산이 반되기 때문에 비효율적이다. 그리고 피보나치 수의 인덱스가 커질수록 중복 계산이 많아져 성능이 떨어진다 하지만 동적 프로그램을 사용하면 성능을 향상시킬 수 있다.    
``` Java
public static int fibTopDown(int n, Map<Integer, Integer> memo) {
        if (memo.containsKey(n)) {// 이미 계산 되었는지 확인
            return memo.get(n);
        }

        if (n < 2) {
            memo.put(n, n);
        } else {
            memo.put(n, fibTopDown(n - 1, memo) + fibTopDown(n - 2, memo));//값을 계산하고 저장
        }

        return memo.get(n);
    }

    public static void main(String[] args) {
        int n = 10;
        Map<Integer, Integer> memo = new HashMap<>();// 메모리제이션을 하기위해 Map생성
        int result = fibTopDown(n, memo);
        System.out.println(result);
    }
```
