---
title: "[논문 리뷰] Audio-Language Models for Audio-Centric Tasks: A Systematic Survey"
excerpt: "ALM 관련 Survey 논문 리뷰"

categories:
  - 논문리뷰
tags:
  - [ai, security, jailbreak, paper]

permalink: /논문리뷰/2501.15177

toc: true
toc_sticky: true

date: 2026-08-13
last_modified_at: 2026-08-13
---

Authors: Yi Su, Jisheng Bai, Qisheng Xu, Kele Xu, Yong Dou [cite: 1.1.4]
Conference / Journal: arXiv (2025) [cite: 1.1.6]
Link: https://arxiv.org/abs/2501.15177 [cite: 1.1.1]

---

>## Introduction

이 논문은 오디오-텍스트 데이터로 학습되어 음성, 음악, 일반 소리 등 오디오 중심의 멀티모달 콘텐츠를 처리하고 이해하는 '오디오-언어 모델(Audio-Language Models, ALMs)'에 대한 종합적인 서베이(Survey) 논문이다. ALM 기술의 발전 동향, 아키텍처, 그리고 학습 방법론론을 체계적으로 분류하고 분석하여 연구자들에게 명확한 기술적 로드맵을 제시한다 [cite: 1.1.4].

---

>## 연구 배경 및 문제 제기

**기존 연구의 한계:**
전통적인 지도 학습(Supervised learning) 방식은 미리 정의된 라벨(Predefined labels)에만 의존하여, 여러 소리가 겹치거나 복잡하게 얽혀 있는 실제 환경의 오디오 시나리오를 처리하는 데 한계가 있었다 [cite: 1.1.4]. 최근 자연어 지도 학습(Natural language supervision)을 활용한 ALM이 등장하여 강력한 제로샷(Zero-shot) 능력을 보여주고 있으나, 분야가 너무 빠르게 발전하여 이를 종합적으로 분석하고 정리한 체계적인 서베이 문헌이 매우 부족한 상황이었다 [cite: 1.1.4].

**저자들의 접근 방식:**
본 논문에서는 특정 소리 영역에 국한되지 않고, 일반적인 오디오 관점에서 음성(Speech), 음악(Music), 환경음(Sound)을 포괄하는 ALM 연구들을 체계적으로 리뷰했다 [cite: 1.1.1].
◦ 이를 위해 모델 아키텍처와 학습 목표(Training objectives) 등을 포함하는 통합된 분류 체계(Unified Taxonomy)를 구축했다 [cite: 1.1.1].

---

>## Methodology (※ 본 논문은 서베이로 분류 체계를 제안함)

### 발전 연대기

이 이미지는 2022년부터 2026년까지 오디오-언어 모델(Audio-Language Models, ALMs) 분야의 주요 기술적 이정표를 시각화한 타임라인이다.

<div style="width: 100%;">
  <img 
    src="/assets/images/posts_img/논문리뷰/2_1.png" 
    style="width: 100%; height: auto; display: block;"
  >
</div>

- 빨간색 다이아몬드 (Dataset): 모델 학습의 기초가 되는 오디오-텍스트 쌍 데이터셋 (예: AudioCaps, WavCaps)
- 노란색 사각형 (Audio-Language Pre-training): 범용적인 오디오 표현을 배우기 위한 사전 학습 모델 (예: CLAP, FLAP)
- 파란색 원 (Downstream Audio-Language Model): 특정 작업이나 복잡한 추론을 수행하는 응용 모델 및 Large Audio-Language Models(LALMs) (예: VALL-E, Qwen-audio)
- 초록색 삼각형 (Benchmark): 모델의 성능을 객관적으로 측정하기 위한 평가 지표 및 데이터셋 (예: AudioBench, AIR-Bench)
- 시간이 흐를수록 단순한 분류/검색 모델(노란색)보다 언어 모델의 지능을 활용하는 통합 모델(파란색)의 비중이 압도적으로 높아지고 있다.

---

>## 연구 분야의 전체적인 구조와 흐름

오디오-언어 모델(ALM)의 전반적인 연구 지형도(Research Landscape)를 모델 학습 관점에서 시각화한 다이어그램이다.


<div style="width: 100%;">
  <img 
    src="/assets/images/posts_img/논문리뷰/2_2.png" 
    style="width: 100%; height: auto; display: block;"
  >
</div>

- **(a): Pre-training**
    - 오디오 데이터와 언어 모델을 정렬(Alignment)하여 모델이 멀티모달(Multimodal) 인식 능력을 갖추도록 만드는 과정(대규모 데이터를 통해 오디오와 텍스트 간의 기본적인 상관관계를 학습)
- **(b): Transfer**
    - **Fine-tuning:** Pre-training된 모델을 각자의 사용에 맞게 단순 학습을 함(예: 1,000가지 소리를 구분하던 층 대신, '정상/비정상' 2가지만 구분하는 층으로 교체)
    - **LLM 결합:** 소리의 맥락을 파악하고 추론할 수 있게 한다(고차원적인 추론 가능)
- **(c): Datasets**
    - Audio-Caption (오디오 캡셔닝):
        - 형태: 오디오 파일 하나에 그 소리를 설명하는 문장이 붙어 있는 형태이다.
        - 예시: (강아지 소리 파일) + "강아지가 활기차게 짖고 있습니다."
        - 용도: 모델이 특정 소리가 어떤 단어와 연결되는지 기초 지식을 쌓는 데 쓰인다.
    - AQA (Audio Question Answering, 오디오 질문 답변):
        - 형태: 오디오 + 질문 + 답변으로 구성된 더 복잡한 데이터이다.
        - 예시: (여자가 말하고 개가 짖는 소리)
        - 질문: "무슨 소리가 들리니?"
        - 답변: "여자가 말한 뒤에 개가 짖는 소리가 들립니다."
        - 용도: 단순히 소리를 맞히는 것을 넘어, 소리의 순서, 횟수, 감정 등을 논리적으로 추론하는 법을 가르칠 때 사용한다. (LALM 학습에 필수적입니다.)
- **(c): Benchmarks**
    - 모델의 성능을 평가

---

>## alm의 4가지 구조

 Encoder와 LLM/Decoder를 어떤 식으로 조립하여 전체 시스템(alm)을 구성할 것인지를 보여주는 그림

<div style="width: 100%;">
  <img 
    src="/assets/images/posts_img/논문리뷰/2_4.png" 
    style="width: 100%; height: auto; display: block;"
  >
</div>

- **(a) Two Towers**
    - **특징:** 오디오와 텍스트를 위한 독립적인 Encoder가 각각 존재하며, 마지막 단계에서 두 임베딩을 공유된 공간(Joint Space)에 정렬한다. LLM을 붙이기 않았기에 간단한 추론(검색 및 분류때 사용)
    - **작동 방식:** 대표적으로 CLAP 모델이 이 방식을 사용하며, 오디오와 텍스트의 유사도를 계산하는 Contrastive Learning을 통해 학습한다.
    - **장점:** 대규모 검색(Retrieval)이나 제로샷 분류(Zero-shot Classification)에 매우 효율적이며, 미리 계산된 임베딩을 사용할 수 있어 추론 속도가 빠르다.
- **(b) Two Heads**
    - **특징:** 각각의 Encoder 위에 하나의 공통된 **Language Model (LM)**을 얹은 형태이다.
    - **작동 방식:** 오디오와 텍스트 표현을 프로젝션 레이어를 통해 LM이 이해할 수 있는 통합 공간으로 전달합니다. SALMONN이나 Qwen-audio와 같은 모델들이 여기에 해당한다.
    - **장점:** 기존 LLM의 강력한 추론 능력을 활용할 수 있어, 오디오 설명 생성(Captioning)이나 복잡한 질의응답(Audio QA)에 유리하다.
- **(c) One Head**
    - **특징:** 오디오와 텍스트를 구분하지 않고 하나의 **Unimodal Encoder**와 Decoder를 사용하여 초기 단계부터 통합적으로 처리하는 방식이다. 현재는 자주 쓰이는 방법이 아니며 아직 연구단계라고 보면 됨
    - **작동 방식:** 'Early-fusion' 접근법으로, 두 모달리티의 정보를 하나의 파라미터 공간에서 동시에 최적화한다.
    - **장점/단점:** 이론적으로는 가장 효율적인 통합 모델이 될 수 있으나, 서로 다른 성격의 데이터를 동시에 학습시켜야 하므로 수렴(Convergence)이 어렵다는 기술적 도전 과제가 있다.
- **(d) Cooperated Systems**
    - **특징:** **LLM Agent**가 중심이 되어 여러 특화된 오디오 모델들을 도구(Tools)처럼 사용하는 구조이다.
    - **작동 방식:** 사용자의 복잡한 명령을 LLM이 분석하여 "소리 분류 모델", "음원 분리 모델" 등을 적재적소에 호출합니다. AudioGPT가 대표적인 예이다.
    - **장점:** 단일 모델로는 해결하기 어려운 다단계의 복잡한 작업(예: 특정 소리를 찾아 분리하고 편집하기)을 수행하는 데 매우 유연하다.

---

### alm 학습 목적 및 단계

**Audio-Language Models(ALMs)**의 학습 단계별 주요 목적과 데이터 흐름을 보여주는 다이어그램이다.     크게 사전 학습(Pre-training)과 전이 학습(Transfer)의 두 단계로 나뉜다.

<div style="width: 100%;">
  <img 
    src="/assets/images/posts_img/논문리뷰/2_3.png" 
    style="width: 100%; height: auto; display: block;"
  >
</div>

### (a)Pre-training Objectives

- Language Pre-training (언어 사전 학습)
    - 방법: 거대한 텍스트 뭉치에서 단어에 마스킹을 하고, 문맥을 통해 빈칸을 맞히며 학습한다. (예: BERT, GPT 등)
    - 목적: 언어의 문법, 논리, 의미를 미리 깨우친 **'말 잘하는 뇌'**를 준비하는 과정입니다.
- Audio Pre-training (오디오 사전 학습)
    - 방법: 오디오의 스펙트로그램(이미지 형태의 소리 데이터)에 마스킹을 하고, 가려진 소리 파형을 복구하며 학습합니다. (예: AudioMAE)
    - 목적: 소리의 주파수 변화, 질감, 패턴을 완벽히 이해하는 **'성능 좋은 귀'**를 만드는 과정이다.
1. **독립 학습 (Single-modal):** 텍스트는 텍스트대로(문맥), 오디오는 오디오대로(마스크 복구) 각자의 본질을 깊게 공부한다. 
2. **교차 학습 (Cross-modal):** 오디오를 보고 텍스트 빈칸을 채우거나, 둘을 대조(Contrastive)하며 서로의 관계를 공부한다. 
- Contrastive Learning (대조 학습)
    - 방법: 위에서 각각 학습된 텍스트와 오디오를 가져와서, 서로 짝이 맞는 데이터끼리는 유사도를 높이고 짝이 아닌 데이터는 멀어지게 학습한다. (예: CLAP)
    - 목적: '뇌(언어)'가 알고 있는 개념과 '귀(오디오)'가 듣는 소리를 하나의 의미 공간으로 연결(Alignment)**하는 과정이다.

대조 학습의 성과물을 재료로 삼아 빈칸 채우기를 완성

### **(b) Task-Specific Fine-tuning**

사전 학습된 모델을 특정 문제 해결에 최적화하는 단계

- **Adaptive Modules:** 사전 학습된 모델 뒤에 추가적인 레이어를 붙여, 오디오 분류(Classification)나 검색(Retrieval) 같은 구체적인 작업을 수행한다.
- **Discriminative Tasks:** "이 소리는 개 짖는 소리인가?"와 같이 확률값(Class Prob.)을 예측하는 작업에 주로 쓰인다.

### (c) Generative Language Modeling (생성형 전이 학습)

최근 Large Audio-Language Models대규모 언어 모델(LLM)의 강력한 추론 능력을 오디오 처리와 결합하여 더욱 복잡한 오디오 작업이나 대화형 작업을 수행할 수 있도록 확장된 모델이다.에서 강조되는 방식으로, 지시어(Instruction)에 따라 답변을 생성한다.

- Instruction Tuning: "이 소리를 단어로 묘사해줘"라는 자연어 지시를 입력하면, 모델이 오디오를 이해하고 적절한 캡션(Caption)이나 설명을 텍스트로 내놓는다.
- LLM 활용: 거대 언어 모델의 추론 능력을 오디오 이해와 결합하여, 단순 인식을 넘어 소리에 대한 이유나 상황을 추론할 수 있게 한다.

---

>## Language-Queried Audio Source Separation (LASS)

복잡하게 섞인 소리 중에서 사용자가 "자연어 지시(Text Query)"를 통해 원하는 소리만 골라내는 기술이다.

<div style="width: 100%;">
  <img 
    src="/assets/images/posts_img/논문리뷰/2_5.png" 
    style="width: 100%; height: auto; display: block;"
  >
</div>

- **기본 개념**: 전통적인 오디오 분리는 '드럼', '보컬'처럼 미리 정의된 카테고리만 분리할 수 있었다. 반면 LASS는 "여자가 말하고 개가 짖는 소리"와 같이 구체적인 문장을 이해하여 타겟 소리를 추출한다.
- **작동 프로세스**:
    - **Text Query (입력)**: 사용자가 분리하고 싶은 소리를 자연어로 입력한다. (예: "A woman is speaking")
    - **Language Encoder**: 입력된 텍스트를 모델이 이해할 수 있는 벡터(Embedding) 형태로 변환한다.
    - **Mixture Audio (입력)**: 여러 소리가 섞여 있는 원본 오디오 파일이다.
    - **Separation Net (핵심 모듈)**: 텍스트 정보(조건)와 혼합 오디오를 결합하여, 전체 신호에서 텍스트가 묘사하는 부분만 남기고 나머지는 제거하는 마스킹(Masking) 또는 필터링 작업을 수행한다.
    - **Separated Audio (출력)**: 최종적으로 사용자가 요청한 소리만 깨끗하게 분리된 결과물이다.
- **활용 분야**: 오디오 편집, 배경 소음 제거(Speech Enhancement), 특정 악기 소리 추출 등 다양한 실무 시나리오에 적용될 수 있다.

---

>## 한계

논문에는 alm은 아래와 같은 보안 및 신뢰성 한계가 있다는 것을 언급하고 있다.

### 1. 입력 단계의 보안 취약점

외부 공격에 대한 방어이다.

- **프롬프트 주입(Prompt Injection):** 악의적으로 조작된 입력값을 통해 모델이 의도치 않은 동작이나 답변을 하도록 만드는 공격에 쉽게 노출된다.
- **위조 오디오(Spoofed Audio):** 딥페이크와 같이 정교하게 조작된 가짜 음성 데이터로 모델을 속이는 공격 역시 현재 ALM이 방어하기 까다로운 영역이다.

### 2. 모델 내부의 신뢰성 오류

모델이 오디오를 분석하고 해석하는 과정 자체에서 결함이 발생한다.

- **환각(Hallucination) 현상:** 실제로 오디오 파일에 존재하지 않는 소리를 마치 들은 것처럼 그럴듯하게 묘사하는 문제가 있다.
- **시간적 추론 오류:** 소리가 발생한 사건의 전후 관계나 순서를 잘못 파악하여 맥락에 맞지 않는 엉뚱한 결론을 내리기도 한다.

### 3. 개인정보 보호

개인정보를 유출할 가능성도 존재한다.

- **음성 지문(Voiceprint) 및 억양 저장:** 화자의 고유한 억양이나 생체 정보에 해당하는 음성 지문이 모델 처리 과정에서 암묵적으로 저장될 위험이 높다.
- **배경 소음의 배신:** 말소리 외에 함께 녹음된 '배경 소음'을 통해 사용자의 현재 위치나 은밀한 생활 습관까지 유추되고 노출될 수 있다.