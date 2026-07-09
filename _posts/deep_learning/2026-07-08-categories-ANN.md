---
title: "ANN"
excerpt: "ANN"

categories:
  - Deep_Learning
tags:
  - [tag1, tag2]

permalink: /deep_learning/ANN

toc: true
toc_sticky: true

date: 2026-07-09
last_modified_at: 2026-07-09
---

>## ANN의 정의

ANN(Artificial Neural Network)은 딥러닝의 가장 기본이 되는 뼈대이다. 인강의 뇌를 구성하는 신경세포인 뉴런들이 전기신호를 주고바드며 정보를 처리하는 방식의 알고리즘이다.

---

>## ANN의 전체 구조

- **입력층 (Input Layer):** 학습할 데이터가 처음 들어오는 곳. (예: 이미지의 픽셀 값, 오디오 데이터 등)
- **은닉층 (Hidden Layer):** 입력된 데이터의 복잡한 패턴과 규칙을 실제로 학습하는 공간. 이 은닉층이 2개 이상 깊게(Deep) 쌓이면 '딥러닝'이 된다.
- **출력층 (Output Layer):** 최종적인 예측 결과를 내보내는 곳. (예: 분류된 클래스, 예측된 수치 등)

---

>## 단일 뉴런(노드)의 작동 원리

하나의 뉴런 안에서의 2단계 연산 

### 1. 선형 결합(Linear Comnination)

입력값x에 가중치 w를 곱하고 편향b를 더해 하나의 값으로 압축

$$
z=\sum_{i=1}^{n}w_ix_i+b
$$

### 2. 활성화 함수(Activation Funtion)

선형 결합으로 나온 결과값z를 그대로 다음 뉴런으로 넘기지 않고, 특정 함수(f)를 통과시켜 값을 변환한다. 대표적인 활성화함수(f)로는 ReLU, Sigmoid 등이 있다.

$$
a=f(z)
$$

이 활성화함수를 쓰는 이유는 신경망에 비선형성(non-linearity)을 부여하기 위함이다.

활성화함수가 없다면 아무리 층을 깊게 쌓아도 결국 단순한 1차 방정식의 연속에 불과하게 되어 복잡한 현실의 문제를 풀 수 없음

---

>## 기본 ANN의 한계와 발전

ANN은 모든 노드가 촘촘하게 연결된 완전연결계층(Fully Connected Layer)으로 이루어져 있다.

- 단점: 입력 데이터를 무조건 1차원 배열로 쫙 펴서(Flatten) 받아들여야 함.
- 문제: 2차원 이미지나 오디오 스펙트로그램을 1차원으로 길게 늘어뜨리면 픽셀이나 신호 간의 인접성, 즉 공간적 일관성(Spatial Consistency)이 완전히 깨져버림.
- 해결책 (발전): 공간 정보를 보존하며 지역적인 특징(Feature)을 효과적으로 추출하기 위해 합성곱 신경망(CNN)과 같은 특화된 구조가 등장하게 됨.