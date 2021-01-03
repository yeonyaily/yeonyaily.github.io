---
title: "Study - Bubble Sort"
categories:
  - Baekjoon
---

### 버블 소트 (Bubble Sort)

##### 정의
서로 인접한 두 원소의 크기를 비교하여 순서대로 정렬하는 알고리즘이다.

##### 알고리즘
for(int i=n-1; i>0; i--){
        for(int j=0; j<i; j++){
            if(a[j]>a[j+1]){
                temp = a[j];
                a[j] = a[j];
                a[j] = temp;
            }
        }
    }
