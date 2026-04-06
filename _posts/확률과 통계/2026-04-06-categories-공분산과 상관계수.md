---
title: "Covariance, Correlation Coefficient"
excerpt: ""

categories:
  - 확률과 통계
tags:
  - [tag1, tag2]

permalink: /확률과 통계/Covariance, Correlation Coefficient

toc: true
toc_sticky: true

date: 2026-04-06
last_modified_at: 2026-04-06
---


# 공분산(Covariance)과 상관계수(Correlation Coefficient)

- 공분산(Covariance)과 상관계수(Correlation Coefficient)는

두 확률변수(또는 데이터)가 **함께 어떻게 변하는지**를 분석할 때 사용하는 대표적인 통계 지표이다.

즉, 두 변수 사이의 **방향성**과 **관계의 강도**를 파악하는 데 사용된다.

<div style="width: 100%;">
  <img 
    src="/assets/images/posts_img/확률과 통계/1d2df05a-39a7-46fb-80ca-d9c78fd2cc6a.jpg" 
    style="width: 100%; height: auto; display: block;"
  >
</div>
---

## 1. 공분산 (Covariance)

공분산은 두 변수가 함께 변하는 **방향(direction)** 을 나타내는 지표이다.

즉, 한 변수가 증가할 때 다른 변수도 함께 증가하는지,

혹은 감소하는지를 확인할 수 있다.

### 수식

모집단 공분산은 다음과 같이 정의된다.

$Cov(X, Y) = \frac{\sum_{i=1}^{n}(X_i - \bar{X})(Y_i - \bar{Y})}{n}$

표본 공분산의 경우 일반적으로 분모를 \(n-1\)로 사용한다.

$Cov(X, Y) = \frac{\sum_{i=1}^{n}(X_i - \bar{X})(Y_i - \bar{Y})}{n-1}$

---

### 의미

- **공분산 > 0**
    - $X$가 증가할 때 $Y$도 증가하는 경향이 있다.
    - 예: 키와 몸무게
- **공분산 < 0**
    - $X$가 증가할 때 $Y$는 감소하는 경향이 있다.
    - 예: 스마트폰 사용 시간과 수면 시간
- **공분산 ≈ 0**
    - 두 변수 사이에 뚜렷한 선형 관계가 없다.

---

### 한계점

공분산은 **단위(scale)에 매우 민감하다.**

예를 들어 키를 **cm**로 측정할지 **m**로 측정할지에 따라

값이 크게 달라질 수 있다.

즉,

> 값의 절대 크기만으로 관계의 강도를 직접 비교하기 어렵다. -> 상관계수를 사용
> 

---

## 2. 상관계수 (Correlation Coefficient)

상관계수는 공분산을 **표준화(normalization)** 한 값이다.

공분산의 단위 의존성 문제를 해결하기 위해

각 변수의 표준편차로 나누어 정규화한다.

대표적으로 **피어슨 상관계수(Pearson Correlation Coefficient)** 를 사용한다.

### 수식

$\rho = \frac{Cov(X, Y)}{\sigma_X \sigma_Y}$

- $\sigma_X$: $X$의 표준편차
- $\sigma_Y$: $Y$의 표준편차

---

### 의미

상관계수는 항상 **-1 ~ 1 범위**의 값을 가진다.

- **r = 1**
    - 완벽한 양의 선형 관계이다.
- **r = -1**
    - 완벽한 음의 선형 관계이다.
- **0 < r < 1**
    - 양의 선형 관계이다.
    - 1에 가까울수록 관계가 강하다.
- **1 < r < 0**
    - 음의 선형 관계이다.
    - 1에 가까울수록 관계가 강하다.
- **r = 0**
    - 선형 관계가 없다.

---

## 핵심 정리

한 문장으로 정리하면 다음과 같다.

> **공분산은 방향을 나타내고, 상관계수는 방향과 강도를 함께 나타낸다.**
> 

실무 데이터 분석에서는 대부분

**상관계수**를 더 자주 사용한다.

<div style="width: 100%;">
  <img 
    src="/assets/images/posts_img/확률과 통계/공분산과 상관계수.png" 
    style="width: 100%; height: auto; display: block;"
  >
</div>

