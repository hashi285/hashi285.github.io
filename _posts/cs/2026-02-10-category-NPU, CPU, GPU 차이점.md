---
title: "NPU, CPU, GPU 차이점"
excerpt: "NPU, CPU, GPU 차이점"

categories:
  - CS
tags:
  - [tag1, tag2]

permalink: /cs/NPU, CPU, GPU 차이점


toc: true
toc_sticky: true

date: 2026-02-10
last_modified_at: 2026-02-10
---

>### 기본 개념

### CPU

- 순차적인 작업에 특화
- 소수의 고성능 코어
- 복잡한 제어 흐름(if, loop)등 에 최적

### GPU

- 병렬적인 작업에 특화
- 수천 개의 경량 코어
- 메모리 대역

### NPU

- MAC 연산(acc = acc + (a × b))에 특화
- 스케줄링이 없음

---

>### CPU, GPU, NPU 차이점

| 구분 | CPU | GPU | NPU |
| --- | --- | --- | --- |
| 설계 목적 | 제어 | 병렬 계산 | AI 추론 |
| 병렬 방식 | 제한적 | 스레드 병렬 | MAC 병렬 |
| 스케줄링 | OS 기반 | 하드웨어/드라이버 | 거의 없음 |
| 연산 유닛 | 범용 ALU | 범용 SIMD | MAC 전용 |
| 유연성 | 매우 높음 | 높음 | 낮음 |
| 전력 효율 | 낮음 | 중간 | 매우 높음 |

---

>### 사용 위치

### CPU

- 파이프라인 오케스트레이션
- 전처리/후처리(if/loop가 많음)

### GPU

- 딥러닝 학습
- 연구용 추론
- 범용 수치 계산

### NPU

- 온디바이스 AI
- 실시간 추론
- 대량 배포 서비스

---

>### 결론

- CPU는 **“생각하고 결정하는 장치”**
- GPU는 **“많이 동시에 계산하는 장치”**
- NPU는 **“AI 계산만 효율적으로 흘려보내는 장치”**