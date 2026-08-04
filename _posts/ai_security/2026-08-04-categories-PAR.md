---
title: "[논문 리뷰] 판정 결합 및 수정을 이용한 경량 이미지 위변조 탐지에 관한 연구 (PAR)"
excerpt: "생성형 AI 기반 이미지 위변조 탐지를 위한 PAR (Prediction Aggregation and Revision) 기법 논문 리뷰"

categories:
  - AI Security
tags:
  - [ai, security, forgery detection, lightweight model, paper]

permalink: /ai_security/PAR

toc: true
toc_sticky: true

date: 2026-08-04
last_modified_at: 2026-08-04
---

>## 논문 개요

이번에 살펴볼 논문은 **"판정 결합 및 수정을 이용한 경량 이미지 위변조 탐지에 관한 연구 (Lightweight Image Forgery Detection with Prediction Aggregation and Revision)"** 입니다.

생성형 AI 기술이 발전함에 따라 모바일이나 엣지 기기(Edge Device)에서의 실시간 위변조 탐지가 중요해지고 있습니다. 기존의 단일 경량 모델은 연산 효율은 좋으나 특정 위변조 패턴에 취약하다는 단점이 있습니다. 본 논문에서는 두 개의 경량 모델을 효율적으로 결합하여 성능을 높이되, 결합 시 발생할 수 있는 '역교정(정답을 오답으로 바꾸는 현상)' 문제를 억제하는 **PAR (Prediction Aggregation and Revision)** 기법을 제안합니다.

---

>## PAR 아키텍처의 2단계 구조

PAR 시스템은 크게 두 단계로 작동합니다.

### 1. 역신뢰도 가중 융합 (Prediction Aggregation)
기본 분류기(Base Classifier)와 보조 모델(Auxiliary Model)의 출력을 합쳐서 '판정 변경 후보'를 생성합니다. 이때 모델의 확신도(Confidence)가 낮을수록 가중치를 더 많이 부여하는 '역신뢰도 가중 융합' 방식을 사용하여 덜 확신하는 모델의 영향력을 높입니다.

### 2. 선택적 판정 되돌림 (Prediction Revision)
1단계의 결과가 기본 분류기의 원래 판정과 다를 때만 2단계 모듈(XGBoost 기반)이 활성화됩니다. 이 모듈은 해당 변경이 '해로운 변경(역교정)'인지 평가하고, 위험하다고 판단되면 원래 판정으로 되돌립니다.

---

>## 주요 실험 결과

본 연구는 MobileNetV2 등의 백본을 사용하여 실험을 진행했습니다.
*   **역교정 억제**: PAR 기법 적용 시 역교정을 49.5% ~ 76.7%까지 감소시켰습니다.
*   **성능 향상**: 기본 분류기 대비 전체 F1 점수가 약 0.71% 향상(F1 0.9652 달성)되었습니다.
*   **실시간 처리 가능성**: Raspberry Pi 5 환경에서 추론 시간을 측정했을 때 약 54ms의 속도를 보여, 실시간 엣지 탐지 시스템으로의 적용 가능성을 성공적으로 입증했습니다.
