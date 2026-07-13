---
title: "Chain Rule"
excerpt: "Chain Rule"

categories:
  - Deep_Learning
tags:
  - [tag1, tag2]

permalink: /deep_learning/Chain Rule

toc: true
toc_sticky: true

date: 2026-07-13
last_modified_at: 2026-07-13
---

>## 직관적인 예시

톱니바퀴 3개(A, B, C)가 맞물려 돌아가는 상황을 보자.

- A가 1바퀴 돌면 B는 2바퀴 돈다.
- B가 1바퀴 돌면 C는 3바퀴 돈다.

만약 A가 1바퀴 돌 때 맨 끝에 있는 C는 몇 바퀴를 돌까?

$2 * 3 = 6$바퀴 돌게 될 것이다. A가 B에 미치는 영향과 B가 C에 미치는 영향을 단순히 곱하면 전체 영향력을 구할 수 있다. 

이것이 Chain Rule의 본질이다. 즉, 연결된 연쇄 반응의 전체 변화율은, 각 단계별 변화율의 곱과 같다.

>## 기본 개념

Chain Rule은  합성함수의 미분법과 같다. (겉미분 X 속미분 사용)

예를 들어, $y = (2x + 1)^3$ 이라는 식이 있다. 이 식은 두 가지 함수가 결합되어 있다.

- **속(안쪽) 함수:** $x$를 두 배 하고 1을 더한다. $\rightarrow u = 2x + 1$
- **겉(바깥쪽) 함수:** 어떤 값을 세제곱한다. $\rightarrow y = u^3$
- $y = (2x + 1)^3$ 의 미분값 = (속 함수 미분값) X (겉 함수 미분값) =  $2 \cdot  3(2x + 1)^2$ =  $6(2x + 1)^2$

체인룰은 이렇게 복잡하게 얽힌 함수를 한 번에 미분할 수 없으니, 바깥쪽부터 하나씩 미분해서 곱하자는 아이디어이다.

>## 수학적 정의

수학에서는 이를 함수 $f$ 안에 함수 $g$가 들어있는 **합성함수** $y = f(g(x))$의 미분으로 정의한다.

$u = g(x)$ 라고 하면, $y = f(u)$ 가 된다. 

이때 처음 입력값 $x$가 맨 마지막 결과값 $y$에 미치는 영향은 다음과 같이 구한다

$$
\frac{\partial y}{\partial x} = \frac{\partial y}{\partial u} \cdot \frac{\partial u}{\partial x}
$$

$y$값을 구하기 위해서 $x$값을 이용해 $u$를 구하고, $u$를 이용하여 $y$를 구하는 것이 체인룰이라고 보면 된다.

데이터가 $x \rightarrow u \rightarrow y$ 라는 징검다리를 순서대로 밟고 지나가기 때문에, 미분(변화율)을 구할 때도 이 징검다리 각각의 변화율을 구해서 곱해주는 것이다.

- $\frac{\partial u}{\partial x}$: 첫 번째 징검다리의 변화율 ($x$가 변할 때 $u$가 얼마나 변하는가)
- $\frac{\partial y}{\partial u}$: 두 번째 징검다리의 변화율 ($u$가 변할 때 $y$가 얼마나 변하는가)