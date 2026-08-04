---
title: "[논문 리뷰] AudioJailbreak: Jailbreak Attacks against End-to-End Large Audio-Language Models"
excerpt: "최근 발표된 대형 오디오-언어 모델(LALM) 대상의 새로운 오디오 탈옥(Jailbreak) 공격인 'AUDIOJAILBREAK' 논문 리뷰"

categories:
  - LLM Security
tags:
  - [ai, security, jailbreak, paper]

permalink: /llm_security/AudioJailbreak

toc: true
toc_sticky: true

date: 2026-08-04
last_modified_at: 2026-08-04
---

>## 논문 개요

이번에 리뷰할 논문은 대형 오디오-언어 모델(Large Audio-Language Models, LALMs)을 대상으로 한 새로운 형태의 탈옥(Jailbreak) 공격을 다룬 **"AudioJailbreak: Jailbreak Attacks against End-to-End Large Audio-Language Models"** (arXiv:2505.14103) 이다.

최근 LALM에 대한 탈옥 공격이 연구되고 있지만, 기존 연구들은 공격자가 사용자 프롬프트를 완전히 조작할 수 있는 환경(Strong adversary)에만 국한되어 있었고 그 효과나 적용 범위가 제한적이었다. 이 논문에서는 텍스트 탈옥 기법이 TTS(Text-to-Speech)를 거쳐 오디오 모델에 쉽게 적용되지 않는다는 점을 밝히고, 보다 진보된 형태의 오디오 공격인 **AUDIOJAILBREAK**를 제안한다.

---

>## AUDIOJAILBREAK의 4가지 주요 특징

기존 공격 방식과 달리 AUDIOJAILBREAK는 다음 4가지의 강력한 특성을 갖는다.

### 1. 비동기성 (Asynchrony)
탈옥을 위한 악성 오디오 섭동(perturbation)이 사용자의 프롬프트와 시간 축에서 정확히 일치할 필요가 없다. 즉, 사용자 프롬프트 뒤에 접미사 형태로 붙이는 것만으로도 공격이 성공한다.

### 2. 보편성 (Universality)
단일 공격 섭동을 생성할 때 여러 프롬프트를 함께 고려함으로써, 하나의 악성 오디오 클립만으로도 다양한 질문과 프롬프트에 대응하는 범용적인 탈옥이 가능하다.

### 3. 은밀성 (Stealthiness)
악성 오디오 내에 숨겨진 탈옥 의도를 은폐하기 위한 다양한 전략을 도입하여, 방어 시스템이나 사용자가 악의적인 목적을 쉽게 알아채지 못하게 만든다.

### 4. Over-the-air 강건성 (Robustness)
오디오가 공기 중으로 재생될 때 발생하는 잔향(reverberation) 효과를 섭동 생성 과정에 포함시켜, 스피커로 재생된 소리가 마이크로 입력되는 물리적 환경(Over-the-air)에서도 공격이 유효하다.

---

>## 위협 모델의 확장 (Weak Adversary)

기존 연구들은 사용자의 입력을 공격자가 완전히 통제하는 강한 공격자(Strong adversary) 상황만을 가정했다. 그러나 AUDIOJAILBREAK는 공격자가 사용자 프롬프트 전체를 조작할 수 없는 **약한 공격자(Weak adversary)** 시나리오에서도 적용 가능한 매우 실용적인 공격 기법이다.

---

>## 실험 결과 및 의의

연구진은 현재 존재하는 가장 강력한 LALM들을 대상으로 광범위한 실험을 진행했다. 특히, 제안된 AUDIOJAILBREAK 방식은 약한 공격자(Weak adversary) 시나리오에서도 **OpenAI의 GPT-4o-Audio**를 성공적으로 탈옥시켰으며, **Meta의 Llama-Guard-3**와 같은 안전 장치마저 우회하는 높은 성공률을 보여주었다.

이 논문은 LALM에 대한 오디오 기반 탈옥 공격이 실제로 심각한 보안 위협이 될 수 있음을 증명하며, 향후 더욱 현실적인 위협 환경(약한 공격자 환경 등)에 대비하여 모델의 강건성(Robustness)을 높여야 한다는 중요한 시사점을 던져준다.
