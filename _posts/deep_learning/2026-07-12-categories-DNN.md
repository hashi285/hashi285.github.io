---
title: "DNN"
excerpt: "DNN"

categories:
  - Deep_Learning
tags:
  - [tag1, tag2]

permalink: /deep_learning/DNN

toc: true
toc_sticky: true

date: 2026-07-12
last_modified_at: 2026-07-12
---

>## DNN기본 개념

DNN은 입력층과 출력층 사이에 다수의 은닉층이 포함된 인공신경망이다. 여기서 Deep(심층)이라는 단어는 은닉층의 깊이가 깊다는 것을 의미한다. 

### ANN과의 차이점

보통 좁은 의미에서 과거의 'ANN'이라 부를 때는 은닉층이 1개 이하인 얕은 신경망(Shallow Neural Network)을 지칭하며, 이것이 깊어진 것이 DNN이다.

- ANN: 머신러닝 기법
- DNN: 딥러닝 기법

| **구분** | **전통적인 ANN (얕은 신경망)** | **DNN (심층 신경망)** |
| --- | --- | --- |
| **은닉층 수** | 1개 (또는 없음) | 2개 이상 (수십~수백 개) |
| **특징 추출 (Feature)** | 사람이 직접 중요 데이터를 가공해 주어야 함 | 층이 깊어지며 모델이 스스로 특징을 학습함 |
| **필요 데이터 양** | 비교적 적은 데이터로도 동작 가능 | 엄청난 양의 빅데이터(Big Data) 필수 |
| **연산 요구량** | 낮음 (CPU 연산으로도 충분) | 매우 높음 (GPU/TPU 가속기 필수) |

---

>## DNN의 핵심 구조와 연산

<div style="width: 100%;">
  <img 
    src="/assets/images/posts_img/deeplearning/DNN.png" 
    style="width: 100%; height: auto; display: block;"
  >
</div>

출처: hombrelogo / Getty Images

DNN은 노드(Node)라고 불리는 인공 뉴런들이 층별로 촘촘하게 연결된 형태를 가집니다. 가장 기본적인 형태는 모든 노드가 다음 층의 모든 노드와 연결되는 **완전 연결 신경망(Fully Connected Network, FCN)** 또는 다층 퍼셉트론(MLP)입니다.

각 노드에서는 아래와 같은 연산이 일어난다.

1. **가중합(Weighted Sum):** 이전 층의 출력값($x_i$)에 가중치($w_i$)를 곱하고 편향($b$)을 더한다.
    1. $z = \sum_{i=1}^{n} w_i x_i + b$
2. **활성화 함수(Activation Function):** 가중합의 결과값을 비선형 함수(ReLU, Sigmoid, Tanh 등)에 통과시켜 다음 층으로 전달한다.
    1. $a = f(z)$

이러한 비선형성(Non-linearity)이 층층이 쌓이면서, DNN은 단순한 선형 방정식으로는 풀 수 없는 매우 복잡한 데이터의 분포와 패턴을 수학적으로 근사할 수 있게 된다.

---

>## DNN의 학습 메커니즘

DNN은 데이터의 정답과 모델의 예측값 사이의 오차를 줄이는 방향으로 파라미터를 스스로 업데이트한다. 

| **과정** | **설명** |
| --- | --- |
| **순전파 (Forward Propagation)** | 데이터가 입력층에서 출력층까지 순차적으로 통과하며 최종 예측값을 계산한다. |
| **손실 계산 (Loss Calculation)** | 예측값과 실제 정답(Label) 간의 차이를 손실 함수(Cross-Entropy 등)로 수치화한다. |
| **역전파 (Backpropagation)** | 순전파와 반대로 출력층에서 다시 입력층 방향으로 거슬러 올라가며, 각 가중치가 오차에 미친 영향력(기울기)을 연쇄 법칙(Chain Rule)으로 계산한다. |
| **파라미터 최적화 (Optimization)** | 경사 하강법(Gradient Descent) 등을 이용해 오차를 최소화하는 방향으로 가중치를 미세하게 조정한다. |