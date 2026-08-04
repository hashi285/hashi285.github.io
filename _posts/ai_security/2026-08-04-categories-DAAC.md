---
title: "[논문 리뷰] 이미지 위변조 탐지를 위한 DAAC(Disagreement-Aware Adaptive Consensus) 기법 연구"
excerpt: "다중 에이전트 간의 판정 불일치를 학습 신호로 활용하는 DAAC 모델 리뷰"

categories:
  - AI Security
tags:
  - [ai, security, forgery detection, multi-agent, DAAC, paper]

permalink: /ai_security/DAAC

toc: true
toc_sticky: true

date: 2026-08-04
last_modified_at: 2026-08-04
---

>## 논문 개요

이번 논문은 이미지 위변조 탐지 모델들의 합의(Consensus) 방식을 개선한 **"이미지 위변조 탐지를 위한 DAAC(Disagreement-Aware Adaptive Consensus)에 관한 연구"** 입니다.

생성형 AI로 만들어진 가짜 이미지들은 형태가 매우 다양하여 단일 탐지 모델(Agent)만으로는 모든 위변조를 잡아내기 어렵습니다. 따라서 여러 특화된 모델들을 섞어 쓰는 '다중 전문 에이전트' 방식이 필요한데, 기존의 단순 평균이나 다수결 방식은 한계가 명확했습니다. 본 연구에서는 에이전트들 간의 **판정 불일치(Disagreement) 패턴 자체를 메타 특징으로 학습**하는 새로운 합의 기법인 **DAAC**를 제안합니다.

---

>## DAAC 모델의 특징

DAAC의 핵심 아이디어는 "누가 맞았는가"보다 **"어떻게 서로 다르게 판단했는가"**를 중요한 단서로 활용하는 것입니다. 

1.  **43차원 메타 특징 추출**: 주파수, 노이즈, 공간적 특징 등을 분석하는 4개의 서로 다른 전문 에이전트(CAT-Net, MVSS-Net, FatFormer, Mesorch)의 출력을 바탕으로, 개별 출력 결과(20개), 에이전트 쌍별 불일치(18개), 전체 집단 통계(5개)를 연결하여 총 43차원의 메타 특징 벡터를 생성합니다.
2.  **적응형 학습**: 도출된 43차원 불일치 패턴을 Logistic Regression(LR)이나 Gradient Boosting Machine(GBM)과 같은 메타 분류기에 입력하여, 어떤 상황에서 어떤 모델 조합을 신뢰해야 할지 모델이 스스로 학습하게 만듭니다.

---

>## 주요 실험 결과

*   **균형 잡힌 클래스 탐지**: 개별 에이전트들은 조작(Manipulated) 클래스나 AI 생성(AI-Generated) 클래스 중 특정 분야에서 F1 점수가 0이 나오는 등 구조적 맹점을 보였으나, DAAC는 모든 클래스에서 고르게 높은 성능을 달성했습니다.
*   **월등한 합의 성능**: DAAC-GBM 모델은 macro-F1 기준 0.861을 기록하여, 기존의 복합 합의 기법인 COBRA(0.266) 대비 **+0.595라는 압도적으로 우수한 성능 향상**을 이루어냈습니다. 
*   **우수한 일반화 성능**: 학습에 사용되지 않은 외부 데이터셋(OpenSDI 등 6개 조합)을 활용한 일반화 검증에서도 기존 방법보다 월등히 높은 안정성과 신뢰도를 보여주었습니다.
