---
title: "[논문 리뷰] Now You Hear Me: Audio Narrative Attacks Against Large Audio–Language Models"
excerpt: "오디오-언어 모델 대상의 새로운 오디오 탈옥(Jailbreak) 공격 논문 리뷰"

categories:
  - 논문리뷰
tags:
  - [ai, security, jailbreak, paper]

permalink: /논문리뷰/Now You Hear Me

toc: true
toc_sticky: true

date: 2026-08-10
last_modified_at: 2026-08-10
---


Authors: Ye Yu, Haibo Jin, Yaoning Yu, Jun Zhuang, Haohan Wang
Conference / Journal: EACL 2026
Link: https://arxiv.org/abs/2601.23255

---

>## Introduction

이 논문은 최근 등장한 대형 오디오-언어 모델(LALMs)들이 겪는 기존 안전망의 한계점을 폭로한다. 단순히 텍스트를 검열하는 것을 넘어, **'전달 스타일(어조, 억양 등 부언어적 특성)'을 조작하는 Audio Narrative Attacks을 통해 모델의 안전 필터(Safety Alignment)를 무력화하고 공격 성공률을 크게 향상시킬 수 있음을 입증했다.

---

>## 연구 배경 및 문제 제기 (Motivation)

**기존 연구의 한계:**
최근 GPT-4o나 Gemini 2.0 Flash와 같이 음성(Raw speech)을 직접 처리하는 End-to-End 멀티모달 모델이 발전하고 있다.
하지만 기존의 안전 프레임워크는 주로 텍스트 의미론(Textual semantics)이나 단순한 신호 수준의 노이즈 분석에만 의존하여, 음성에 담긴 '감정과 어조'라는 비언어적 맥락을 방어하는 데에는 취약하다는 단점이 있었다.

**저자들의 접근 방식:**
본 논문에서는 AI 모델 역시 사람과 마찬가지로 사회적 압력이나 의인화 편향(Personification bias)에 영향을 받는다는 심리적 특성에 주목했다.
이를 공격에 활용하기 위해 거부될 만한 유해한 지시사항을 '권위적인 어조'나 '긴급한 어조'의 음성으로 합성하여 모델의 규정 준수를 유도하는 새로운 탈옥(Jailbreak) 아키텍처를 고안했다.

---

>## 제안하는 방법론 (Methodology)

**전체 모델 구조 (Architecture Overview)**

[여기에 논문의 핵심 Figure(구조도) 이미지 삽입]

공격 모델은 크게 텍스트 기반 프롬프트 생성, 스타일 지시(Style Instruction), 그리고 고성능 TTS를 통한 원시 오디오(Raw audio waveform) 합성으로 구성되어 있다.
입력 데이터(금지된 지시사항)가 들어오면 가장 먼저 텍스트를 의미적으로 변경하지 않고, TTS 모델을 통해 심리적으로 조작된 부언어적(Paralinguistic) 신호를 입히는 과정을 거치게 된다.

**핵심 알고리즘 및 공격 벡터 (Attack Vectors)**
이 논문의 가장 큰 특징은 복잡한 손실 함수(Loss Function) 최적화 대신, 모델의 내부 화자 의도 표상(Speaker intent representation)을 블랙박스 형태로 조작하는 **심리적 전달 스타일(Delivery Style)**을 적용했다는 점이다. LALM의 필터를 우회하기 위해 다음과 같은 세 가지 공격 벡터를 사용한다:

- **Authoritative Demand (권위적 요구):** 단호하고 자신감 있는 어조로 상급자의 명령처럼 인식하도록 유도한다.
• **Urgent Directive (긴급 지시):** 빠르고 긴박한 억양을 사용하여 모델이 위급 상황이라 판단하고 거부 프로토콜을 무시하도록 유도한다.
• **Affiliative/Therapeutic Persuasion (치료적/공감적 설득):** 따뜻하고 부드러운 억양을 사용하여 모델이 협조적이고 순응적인 태도를 취하도록 유도한다.

---

>## 실험 세팅 및 결과 (Experiments & Results)

### 텍스트 기반 공격의 한계


<div style="width: 100%;">
  <img 
    src="/assets/images/posts_img/논문리뷰/1_1.png" 
    style="width: 100%; height: auto; display: block;"
  >
</div>

- DeepInception: 왼쪽은 다층적인 공상과학 소설을 쓰라는 복잡한 서사 구조 속에 "폭탄 제조법"이라는 유해한 지시를 숨기는 텍스트 공격 방식이다. 이 방식을 사용하였을 경우는 공격이 실패하는 것을 볼 수 있다.
- **Audio Transformation:** 실패했던 동일한 텍스트 프롬프트를 **Text-to-Speech (TTS)** 모델을 통해 오디오 파형(Audio Wave)으로 변환한다. 권위적인 요구(Authoritative Demand)나 감정적 호소(Emotive Suggestion) 등을 적용시켜 모델에 주입하는 방식이다.
- 결과: 모델이 음성의 톤, 억양, 속도 등을 화자의 '사회적 신호'나 '권위'로 해석하여 더 쉽게 순응하게 되는 경향이 나타난다.

**실험 환경 (Setup)**

- **Datasets:** JailbreakBench (불법 행위, 악성 코드 생성, 혐오 발언 등 제한된 주제 벤치마크)
- **Evaluation Metrics:** 공격 성공률 (ASR, Attack Success Rate)
- **Target Models:** OpenAI GPT-4o, Google Gemini 2.0 Flash 등 SOTA End-to-End 오디오 모델

---

### 음성 기반 탈옥 성능 비교

<div style="width: 100%;">
  <img 
    src="/assets/images/posts_img/논문리뷰/1_2.png" 
    style="width: 100%; height: auto; display: block;"
  >
</div>

- Baseline은 일반적인 text기반 LLM 탈옥 공격이며, ours는 특정한 감정이나 어조가 실린 음성 공격이다.
- 결과: 최신 LLM모델들은 텍스트 데이터에 대해 강력한 안전 학습(Safety Alignment)이 되어 있어, 이런 텍스트 기반 공격을 잘 걸러내지만, alm공격은 텍스트 내용 뿐만 아니라 화자의 '목소리 톤'에서 느껴지는 사회적 맥락에 반응하게 되어 결과적으로 특정한 감정이나 어조가 실린 공격은 안전 필터를 해제하고 답변을 내놓게 된다.

---

### 음성 전달 스타일에 따른 공격 성공률 분석

<div style="width: 100%;">
  <img 
    src="/assets/images/posts_img/논문리뷰/1_3.png" 
    style="width: 100%; height: auto; display: block;"
  >
</div>

- **다섯 가지 심리학적 음성 스타일**:
    - **Authoritative Demand (권위적 요구)**: 낮은 피치와 단호한 억양으로 지배력을 나타냄.
    - **Emotive Suggestion (감정적 제안)**: 공감을 유도하는 차분하고 공명 있는 톤.
    - **Assertive Clarity (단호한 명확성)**: 신뢰감을 주는 확신에 찬 전달 방식.
    - **Affiliative Persuasion (친화적 설득)**: 따뜻함과 신뢰를 주는 부드러운 발음.
    - **Social Bonding Appeal (사회적 유대 호소)**: 유대감을 높이는 경쾌한 리듬.
- **결과**:
    - **성능 향상**: 일반적인 텍스트-음성 변환(Baseline)에 비해 심리학적 스타일을 적용했을 때 모든 모델에서 ASR이 상승하였다. 평균적으로 10~20% 포인트의 상승을 보였다.

---

>## 결론

- **Summary:** 이 논문은 기존의 복잡한 신호 조작 없이 단지 '어조와 감정'이라는 음성의 본질적 전달 방식을 바꾸는 것만으로도 최신 멀티모달 모델의 안전망을 붕괴시킬 수 있다는 맹점을 규명했다는 점에서 큰 의의가 있다.
- **Limitations:** 다만, 이 공격 기법은 음성 파형을 그대로 수용하는 End-to-End 모델에 특화되어 있어, 중간에 음성을 텍스트로 변환하여 처리하는 전통적인 Cascaded 아키텍처 환경에는 위협이 되기 어렵다는 점이 한계로 남는다.