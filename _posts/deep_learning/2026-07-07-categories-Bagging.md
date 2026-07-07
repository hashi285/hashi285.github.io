---
title: "Bagging"
excerpt: "Bagging"

categories:
  - Deep_Learning
tags:
  - [tag1, tag2]

permalink: /deep_learning/Bagging

toc: true
toc_sticky: true

date: 2026-07-07
last_modified_at: 2026-07-07
---

>## Bagging의 기본 개념

Ensemble의 방식중의 하나. Bootstrap Aggregating의 줄임말로, Bootstrap와 Aggregating이라는 두가지 과정이 결합된 기법이다. 

단일 모델이 데이터에 너무 민감하게 반응하여 발생하는 Overfitting을 막는데 효과가 있다.

- Bootstrap: 원본 데이터 풀에서 중복을 허용하여 뽑기를 반복함으로써 원본과 크기는 같지만, 구성이 다른 데이터셋을 만들어내는 과정이다.
- Aggregation: 학습된 여러 모델이 각자의 예측값을 내놓으면, 이를 하나로 합쳐 최종 결론을 내린다.
    - Classification: Hard Voting(다수결 투표) 또는 Soft Voting(확률의 평균)으로 가장 많은 선택을 받은 정답을 고른다.
    - Regression: 모델들이 예측한 수치들의 평균을 낸다.
- Bagging의 효과: 여러 모델의 의견을 종합을 하기에 특정 모델이 튀는 예측을 하더라도 전체 결과는 안정적으로 유지된다. (모델의 Variance를 줄여준다.)

---

>## Bagging의 대표 Random Forest

Random Forest는 Decision Tree를 모아 만든 Forest이며, Bagging의 기본 원리를 따르는 대표적인 알고리즘이다.  

Random Forest는 일반적인 Bagging에 Feature의 무작위성이라는조건을 하나 추가를 하였다.

- 데이터의 무작위성: 수백 개의 Decision Tree가 각각 Bootstrap 방식으로 만들어진 서로 다른 데이터셋을 가지고 합습한다.
- Feature의 무작위성: 일반적인 트리는 가지를 칠 때 전체 변수 중 무작위로 일부 변수만 골라서 그 안에서만 최적의 분할을 찾는다.  하지만 Random Forest는 가지를 칠 때 젠체 변수 중 무작위로 일부 변수만 골라서 그 안에서만 최적의 분할을 찾는다.

---

>## 장단점

### Bagging의 장점

1. **과적합(Overfitting) 방지 및 안정성 증가**
    - 단일 모델은 학습 데이터의 미세한 노이즈(Noise)까지 외워버리는 경향이 있다. Bagging은 여러 모델의 평균/다수결을 내기 때문에, 특정 데이터에 지나치게 얽매이는 현상(높은 분산)을 크게 줄여주어 처음 보는 데이터에 대한 예측력을 높인다.
2. **이상치(Outlier)에 강함**
    - Bootstrap 과정에서 복원 추출을 하기 때문에, 극단적인 이상치가 모든 모델의 학습 데이터에 포함될 확률이 낮다. 또한, 다수결을 통해 튀는 결과값을 상쇄시키므로 안정적이다.
3. **병렬 처리(Parallel Processing) 가능**
    - Boosting 기법과 달리, 배깅에 속한 모델들은 서로의 학습 결과에 영향을 주지 않고 완전히 독립적이다. 따라서 여러 CPU 코어를 활용해 수백 개의 모델을 동시에 학습시킬 수 있어 학습 속도를 크게 단축할 수 있다.
4. **자체적인 성능 평가 가능 (OOB Score)**
    - 부트스트랩 추출 시 선택받지 못한 약 36.8%의 데이터(Out-of-Bag, OOB 데이터)를 마치 검증용 데이터(Validation Set)처럼 활용하여, 별도의 테스트셋 분리 없이도 모델의 성능을 자체 평가할 수 있습니다.

### Bagging의 단점

1. **해석력 저하 (Black Box 모델화)**
    - 단일 의사결정 나무는 스무고개처럼 결과를 도출한 과정(조건 분기)을 시각화하고 쉽게 설명할 수 있다(White Box). 하지만 배깅을 통해 수십~수백 개의 모델이 섞이게 되면, 왜 그런 최종 결과가 나왔는지 직관적으로 설명하기가 매우 어려워진다.
2. **높은 메모리 사용량과 예측 시간**
    - 한 개의 모델이 아닌 수백 개의 모델을 메모리에 저장해야 하므로 용량을 많이 차지한다. 또한, 새로운 데이터 하나를 예측할 때도 모든 모델을 거쳐야 하므로 단일 모델에 비해 실시간 예측(Inference) 속도가 느려질 수 있다.
3. **단순한 모델에는 효과가 미미함 (편향 감소 한계)**
    - 배깅은 모델의 '분산(Variance)'을 줄이는 데 특화되어 있다. 따라서 처음부터 너무 단순해서 학습조차 제대로 못 하는(편향이 높은) 모델을 배깅으로 묶는다고 해서 성능이 좋아지지는 않는다.


<div style="width: 100%;">
  <img 
    src="/assets/images/posts_img/deeplearning/randomforest.png" 
    style="width: 100%; height: auto; display: block;"
  >
</div>
