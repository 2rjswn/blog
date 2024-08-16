---
title: 스택 구현
published: 2024-07-01
tags: [Data Structure, Algorithm]
category: implementation
draft: false
---

# 스택 구현
```java
private static final int Bank = 5; //용량
    private Object[] arr; //값을 받을 배열
    private int top; //스택의 맨 위 요소 체크

    public Main() {
        this.arr = new Object[Bank];// 배열 생성
        this.top = -1;
    }
    public boolean isFull() {
        return top == arr.length -1;
    }
    public boolean isEmpty() {
        return top == -1;
    }
    private void resize() {//메소드 내에서만 사용하므로 private
        int arr_capacity = arr.length - 1;// 배열은 0부터 시작함으로 -1

        if (top == arr_capacity) {// 용량이 꽉찬 경우
            int new_capacity = arr.length * 2;//용량 두배
            arr = Arrays.copyOf(arr, new_capacity ); //배열 new_capacity 용량 설정
        }

        if (top < (arr_capacity / 2)) {
            int half_capacity = arr.length / 2;// 기존 용량의 반
            arr = Arrays.copyOf(arr, Math.max(half_capacity, Bank)); //half_capacity 와 기본 용량 중 큰걸 복사
        }
    }

    public Long push(Long value) {
        //1.배열 용량 검사
        if (isFull())
            resize();

        //2.원소 추가로 top++
        top++;

        //3.원소 추가
        arr[top] = value;   

        return value;
    }

    public Long pop() {
        //1.배열 확인
        if (isEmpty())
            throw new EmptyStackException();
        //2.arr원소 백업
        Long value = (Long) arr[top];
        //3.해당 위치 요소 삭제
        arr[top] = null;
        //4.top 감소
        top--;
        //빈 공간이 많으면 리사이징
        resize();

        return value;
    }
```
다른 블로그를 참고하며 구현했다 다음에 혼자 다시 만들어볼 예정