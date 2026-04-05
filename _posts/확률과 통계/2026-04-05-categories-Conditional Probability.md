---
title: "Conditional Probability"
excerpt: ""

categories:
  - 확률과 통계
tags:
  - [tag1, tag2]

permalink: /확률과 통계/Conditional Probability

toc: true
toc_sticky: true

date: 2026-04-05
last_modified_at: 2026-04-05
---


# 조건부 확률 (Conditional Probability)

## 1. 정의 및 수식

사건 $A$가 일어날 확률이 $P(A) > 0$일 때, 사건 $A$가 일어났다는 조건 아래 사건 $B$의 확률을 **조건부 확률**이라고 한다.

수식은 다음과 같다.

$P(B \mid A) = \frac{P(A \cap B)}{P(A)}$

각 항의 의미는 다음과 같다.

- $P(B \mid A)$: 사건 $A$가 발생했을 때 사건 $B$가 발생할 확률
    - $P(A \cap B)$: 사건 $A$와 $B$가 동시에 발생할 확률
- $P(A)$: 조건이 되는 사건 $A$가 발생할 확률

여기서 | 기호는 **"given"**, 즉 "~라는 조건에서"라는 의미이다.

---

## 2. 핵심 개념: 표본 공간의 축소

조건부 확률의 핵심은 **전체 표본 공간이 조건 사건 $A$로 축소된다**는 점이다.

원래는 전체 집합 $S$에서 사건 $B$의 비율을 본다.

하지만 조건 $A$가 주어지면, 이제 전체 공간은 $S$가 아니라 **사건 $A$ 내부만 새로운 표본 공간**이 된다.

---

## 3. 핵심 요약

- 조건부 확률은 **조건이 주어진 상황에서의 확률**이다.
- 표본 공간이 전체가 아니라 **조건 사건 내부로 축소된다**.


<div style="display: flex; justify-content: center; gap: 10px;">
  <img src="/assets/images/posts_img/확률과 통계/조건부확률.jpg" style="width: 32%;">
</div>