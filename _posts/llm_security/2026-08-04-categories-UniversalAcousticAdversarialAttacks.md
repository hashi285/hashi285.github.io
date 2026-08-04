---
title: "[논문 리뷰] Universal Acoustic Adversarial Attacks for Flexible Control of Speech-LLMs"
excerpt: "Speech-LLM 모델에 대한 선택적, 보편적 음향 적대적 공격(Acoustic Adversarial Attacks)의 취약성을 다룬 논문 리뷰"

categories:
  - LLM Security
tags:
  - [ai, security, adversarial attack, speech-llm, paper]

permalink: /llm_security/UniversalAcousticAdversarialAttacks

toc: true
toc_sticky: true

date: 2026-08-04
last_modified_at: 2026-08-04
---

>## 논문 개요

이번에 다룰 논문은 이전 포스팅과 유사하게 음성을 이해하는 인공지능 모델(Speech-LLMs)의 취약성을 지적하는 연구입니다. 논문 제목은 **"Universal Acoustic Adversarial Attacks for Flexible Control of Speech-LLMs"** (arXiv:2505.14286) 입니다.

최근 텍스트 기반 거대 언어 모델(LLM)에 사전 학습된 음성 인코더를 결합하여, 다양한 음성 언어 처리 작업을 수행할 수 있는 Speech-LLM들이 활발히 개발되고 있습니다. 이 모델들은 강력하고 유연하지만, 역설적이게도 이러한 유연성 때문에 **적대적 공격(Adversarial Attacks)**에 더욱 취약해질 수 있습니다. 본 연구는 Speech-LLM에 대한 '보편적(Universal) 음향 적대적 공격'의 범위를 조사하여 그 심각성을 밝힙니다.

---

>## 보편적 음향 적대적 공격이란?

기본적인 공격 방식은 **고정된 범용 악성 오디오 조각(Universal adversarial audio segment)**을 사용자의 원래 음성 입력 앞에 덧붙이는(prepend) 형태입니다.

이러한 조작이 가해지면 모델은 다음과 같은 비정상적인 행동을 보이게 됩니다.
*   **응답 거부:** 아예 아무런 출력을 내놓지 못하게 만듭니다.
*   **작업 무시(Task Overriding):** 사용자의 원래 프롬프트(지시사항)를 무시하고, 공격자가 의도한 다른 작업을 수행하도록 만듭니다.

---

>## 선택적 활성화 (Selective Attack) 기법

이 논문에서 가장 흥미로운 점은 공격을 **선택적(Selective)**으로 만들 수 있다는 것입니다.

즉, 모든 음성에 대해 무조건 공격이 발동하는 것이 아니라 **특정 화자의 성별(Gender)**이나 **특정 사용 언어(Language)** 등 구체적인 속성이 감지될 때만 악성 트리거가 작동하도록 설정할 수 있습니다. 반대로 타겟이 아닌 속성의 음성 입력에 대해서는 모델이 정상적으로 응답하게 됩니다. 

이러한 방식은 공격자에게 타겟 모델의 출력에 대한 세밀한 제어(fine-grained control) 권한을 쥐어주는 것과 같아 매우 위협적입니다.

---

>## 실험 결과 및 시사점

연구진은 **Qwen2-Audio**와 **Granite-Speech** 모델을 대상으로 테스트를 진행했으며, 두 모델 모두에서 치명적인 보안 취약점을 발견했습니다. 이는 현재 개발되고 있는 다른 유사한 구조의 Speech-LLM들 역시 이러한 보편적 적대적 공격에 속수무책일 가능성이 높음을 시사합니다.

결론적으로, 다중 모달(Multi-modal) 환경을 지원하는 LLM을 안전하게 배포하기 위해서는, 강력하고 유연한 성능을 추구하는 것뿐만 아니라 오디오 입력에 섞여 들어오는 적대적 섭동(perturbation)에 대항할 수 있는 **더욱 견고한 학습(Robust training) 전략**이 필수적입니다.
