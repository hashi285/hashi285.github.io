---
title: "Activation function"
excerpt: "Activation function(활성화함수)"

categories:
  - Deep_Learning
tags:
  - [tag1, tag2]

permalink: /deep_learning/Activation function

toc: true
toc_sticky: true

date: 2026-07-27
last_modified_at: 2026-07-27
---

>## 기본 개념

딥러닝모델이 복잡한 패턴을 학습할 수 있게 만들어주는 함수

Activation function을 써야 모델이 선형적인 한계를 벗어나 고차원적인 데이터를 학습할 수 있다.

입력된 데이터가 Weight와 곱해지고, Bias와 더해진 이후 다음 노드에 넘겨지기 전에 Activation function을 한번 통과를 한 이후 전해진다.

---

>## 선형 변환의 한계

활성화함수의 존재 목적은 신경망에 비선형성을 추가하기 위함이다. 

만약 활성화함수가 없어 비선형성을 추가할 수 없다면 은닉층을 많이 쌓아도 결국 수식은 다음과 같아진다.

$$
f(f(f(x))) = W_3(W_2(W_1x)) = (W_3W_2W_1)x = W'x
$$

<div style="width: 100%;">
  <img 
    src="/assets/images/posts_img/deeplearning/활성화함수.jpg" 
    style="width: 100%; height: auto; display: block;"
  >
</div>
이해하기 쉽도록 위의 그림을 추가를 했다. 

행렬 곱셈의 결합 법칙에 의해 $W_4, W_3, W_2, W_1$  행렬 4개를 곱하면 결국 새로운 모양의 거대한 행렬 1개($W'$)(그림에서는 $Z$)가 나온다.

위 그림은 모델에 비선형성을 추가하지 않았을 경우 은닉층이 아무리 깊어도 결국 은닉층이 깊지 않은 모델과 수학적으로는 동일한 모델이라는 것을 보여준다.

아래의 그림은 선형경계와 비선형 경계를 비교한 그림이다.

<div style="width: 100%;">
  <img 
    src="/assets/images/posts_img/deeplearning/선형 비선형 비교.png" 
    style="width: 100%; height: auto; display: block;"
  >
</div>

선형 변환($Wx$)은 시각적으로 말하면 '공간을 반듯하게 늘리거나, 줄이거나, 회전시키는 것'만 가능하다. 즉, 수백 번 선형 변환을 반복해도 '직선은 무조건 직선'으로 남기 때문에 오른쪽처럼 데이터가 분포되어있는 경우는 선형변환만으로는 데이터를 제대로 분류를 할 수 없다. 이때 필요한 것이 Activation function이며, Activation function로 인해 생겨난 비선형성은 위와 같이 선을 구부려주는 역할을 하게 된다. 

---

>## Activation function 종류

대표적인 Activation function 3가지이다.

### **Sigmoid (시그모이드)**

- **수식:** $f(x) = \frac{1}{1 + e^{-x}}$
- **작동 방식:** 모든 입력값을 0과 1 사이의 부드러운 곡선 형태로 변환한다.
- **특징:** 값이 0에서 1 사이이므로 '확률'을 표현하기에 좋다. 주로 이진 분류(Binary Classification) 모델의 **마지막 출력층**에서 사용된다.
- **장단점:** 은닉층에 사용할 경우 층이 깊어질수록 역전파(Backpropagation) 과정에서 오차의 기울기가 0에 수렴해버려 학습이 되지 않는 **기울기 소실** 문제가 매우 심각하게 발생한다. 이 때문에 현대의 깊은 신경망 은닉층에서는 거의 쓰지 않는다.

### **Tanh (하이퍼볼릭 탄젠트)**

- **수식:** $f(x) = \frac{e^x - e^{-x}}{e^x + e^{-x}}$
- **작동 방식:** 시그모이드와 형태는 비슷하지만, 출력 범위가 -1에서 1 사이이다.
- **특징:** 데이터의 중심을 0으로 맞춰주기 때문에(Zero-centered), 시그모이드보다 최적화 과정이 안정적이고 빠르다. 하지만 여전히 양 끝단에서는 미분값이 0에 가까워지므로 기울기 소실 문제에서 완전히 자유롭지는 않다.

### **ReLU (Rectified Linear Unit)**

- **수식:** $f(x) = \max(0, x)$
- **작동 방식:** 입력값이 0보다 크면 그대로 통과시키고, 0 이하면 0으로 만든다.
- **특징:** 딥러닝 은닉층에서 가장 기본적으로 쓰이는 표준 함수이다.
- **장단점:** 계산이 매우 단순하여 학습 속도가 빠르고, 딥러닝의 고질적인 문제인 **기울기 소실(Vanishing Gradient)** 문제를 크게 완화시켜 준다. 다만, 음수 입력 시 미분값이 0이 되어 해당 뉴런의 가중치 업데이트가 영구적으로 멈춰버리는 **'죽은 렐루(Dying ReLU)'** 현상이 발생할 수 있다.

<div style="width: 100%;">
  <img 
    src="/assets/images/posts_img/deeplearning/활성화함수 비교.png" 
    style="width: 100%; height: auto; display: block;"
  >
</div>

주요 활성화 함수 비교. 출처: Aitude