---
title: "케라스 라이브러리"
excerpt: "케라스 라이브러리에 대해 알아보자"

categories:
  - Deep_Learning
tags:
  - [tag1, tag2]

permalink: /deep_learning/케라스 라이브러리

toc: true
toc_sticky: true

date: 2025-05-20
last_modified_at: 2025-05-20
---
# MLP와 케라스 라이브러리

- 미니 배치의 개념을 이해한다.
- 학습률의 개념을 이해한다.
- 케라스 라이브러리로 MLP를 구현해본다.
- 케라스 라이브러리를 살펴본다.
- 하이퍼 매개변수에 대하여 살펴본다.

## 미니배치

**몇 개의 샘플을 처리한 후에 가중치를 변경할 것인가? 크게 2가지 방법이 있다.** 

1. 하나의 샘플을 처리한 후에 바로 가중치를 변경하는 방법 
- 온라인 학습
- 확률적 경사 하강법
1. 풀 배치 학습 
- 모든 샘플을 모두 처리한 후에, 모델의 가중치를 변경하는 방법

---

### (1) 배치 경사 하강법 (Batch Gradient Descent)

- **전체 데이터**를 한 번에 사용하여 손실 함수의 기울기를 계산
- 장점: 정확한 기울기를 계산
- 단점: 데이터가 클 경우 계산이 **매우 느림** ⏳, 메모리 부족

### (2) 확률적 경사 하강법 (Stochastic Gradient Descent, **SGD**)

- **데이터 샘플 하나**만 가지고 기울기 계산 후 바로 가중치 업데이트
- 장점: 계산 빠름, 실시간 학습 가능
- 단점: **손실 함수가 요동치듯 불안정**, 수렴이 느리거나 불안정

```python
# SGD 구현 예시 (PyTorch 스타일)
for epoch in range(num_epochs):
    for x, y in dataset:  # x, y는 하나의 샘플
        pred = model(x)
        loss = loss_fn(pred, y)
        optimizer.zero_grad()
        loss.backward()
        optimizer.step()

```

### (3) 미니 배치 경사 하강법 (Mini-Batch Gradient Descent)

- *데이터를 일정 크기의 배치(batch)**로 나누어 학습
- 일반적으로 가장 **실용적이고 널리 사용됨**
- 장점:
    - 계산 효율성과 메모리 균형
    - 수렴 안정성 향상
    - GPU 병렬 처리에 적합
- 배치 크기 예: 16, 32, 64, 128

```python

# Mini-Batch SGD 예시 (PyTorch)
for epoch in range(num_epochs):
    for X_batch, y_batch in dataloader:  # 배치 단위
        pred = model(X_batch)
        loss = loss_fn(pred, y_batch)
        optimizer.zero_grad()
        loss.backward()
        optimizer.step()

```

### 각 방법들의 비교

- 결국에 샘플을 전부 처리를 하면, 시간이 오래 걸리고, 반대로 하나의 샘플마다 모델의 매개변수를 업데이트를 하면 잡음에 취약해 질 수 있다.
- 따라서 미니 배치는 온라인 학습의 장점인 “빠른 모델 업데이트와 메모리 효율성”과 풀 배치 학습의 장점인 “정확한 모델 업데이트와 계산 효율성”의 적절한 타협점이라 보면 된다.