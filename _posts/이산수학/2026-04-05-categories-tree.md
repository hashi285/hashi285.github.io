---
title: "트리(Tree) 핵심 공식 & 정리"
excerpt: "tree"

categories:
  - 이산수학
tags:
  - [tag1, tag2]

permalink: /이산수학/트리(Tree) 핵심 공식 & 정리

toc: true
toc_sticky: true

date: 2026-06-06
last_modified_at: 2026-06-06
---


## 트리(Tree) 핵심 공식 & 정리

---

## 1. 기본 용어

| 용어 | 의미 |
| --- | --- |
| 정점(Vertex) = 노드(Node) | 트리를 구성하는 점 |
| 간선(Edge) | 노드와 노드를 연결하는 선 |
| 루트 정점(Root) | 부모가 없는 최상위 노드 |
| 내부 정점(Internal Vertex, (i)) | 자식을 1개 이상 가진 노드 |
| 단말 정점(Leaf Node, (l)) | 자식이 없는 노드 |
| 전체 정점 수 ((n)) | 트리 내 모든 노드 수 |

기본 관계식

n = l + i

---

## 2. Theorem 3 : 전체 정점 수

### 포화 m-가지 트리 (Full m-ary Tree)

내부 정점이 (i)개일 때

n = mi + 1

### 유도

- 내부 정점 하나는 정확히 (m)개의 자식을 가진다.
- 내부 정점이 (i)개이면 자식 노드는 총 (mi)개이다.
- 루트 노드 1개를 더하면 전체 노드 수가 된다.

n = mi + 1

---

## 3. Theorem 4 : 하나를 알면 나머지 구하기

기본식

n = mi + 1

n = l + i

두 식을 연립하여 모든 공식을 유도할 수 있다.

---

### (1) 전체 정점 수 (n)을 알고 있을 때

#### 내부 정점 수

$i=\frac{n-1}{m}$

#### 리프 노드 수

$l=\frac{(m-1)n+1}{m}$

---

### (2) 내부 정점 수 (i)를 알고 있을 때

#### 전체 정점 수

n=mi+1

#### 리프 노드 수

l=(m-1)i+1

---

### (3) 리프 노드 수 (l)을 알고 있을 때

#### 전체 정점 수

$n=\frac{ml-1}{m-1}$

#### 내부 정점 수

$i=\frac{l-1}{m-1}$

---

## 4. Theorem 5 : 높이(Height)와 리프 노드 수

높이가 (h)인 (m)-가지 트리에서

리프 노드 수를 (l)이라 하면

---

### (1) 리프 노드 수의 최대값

$l \le m^h$

#### 의미

높이가 (h)일 때 가질 수 있는 최대 리프 노드 수는

$m^h$

이다.

중간에 빈 자리가 있을 수 있으므로

$l \le m^h$

가 성립한다.

---

### (2) 높이의 하한

양변에 ($\log_m$)를 취하면

$h \ge \log_m l$

#### 의미

리프 노드 (l)개를 만들기 위해 필요한 최소 높이를 의미한다.

---

### (3) 포화 + 균형 트리의 높이

트리가 완전히 채워져 있고 균형을 이룰 경우

$h=\lceil\log_m l\rceil$

여기서

$\lceil x \rceil$

은 올림(Ceiling)을 의미한다.

---

### 예제

#### 문제

리프 노드가 5개인 포화 이진 트리의 높이는?

- (m=2)
- (l=5)

#### 풀이

$h=\lceil\log_2 5\rceil$

$\log_2 5 \approx 2.32$

$h=\lceil2.32\rceil=3$

#### 정답

$\boxed{h=3}$

<div style="width: 100%;">
  <img 
    src="/assets/images/posts_img/이산수학/tree.jpg" 
    style="width: 100%; height: auto; display: block;"
  >
</div>