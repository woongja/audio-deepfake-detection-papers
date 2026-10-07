# Language Orthogonalization for Zero-Shot Cross-Lingual Audio Deepfake Detection

> ⚠ AI-generated summary (local LLM, **Korean**, unverified) — auto-generated from the paper, not fact-checked. Verify against the source.

**arXiv:** https://arxiv.org/abs/2609.16458 · > **제출일:** 2026-09-15 · 2026

## 한 줄 요약

본 논문은 다국어 음성 데이터에서 언어적 혼란을 제거하여 음성 디프페이크 탐지의 정확도를 높이는 방법을 제안하며, 다양한 언어 간 전이에서 특히 뛰어난 성능을 보입니다.

## 문제 정의

음성 디프페이크 탐지 모델은 학습 시 사용되지 않은 언어의 음성을 인식하는 데 어려움을 겪습니다. 이는 음성 데이터가 언어 특성을 내포하고 있어, 학습된 모델이 특정 언어의 특징에 과도하게 의존하기 때문입니다. 특히, 학습 시 사용되지 않은 먼 언어 간의 전이에서 이러한 언어적 혼란이 심각하게 나타납니다.

## 제안 방법

본 논문에서는 다국어 음성 데이터의 언어적 혼란을 제거하기 위해 '언어 오र्थ고날라이제이션(Linguistic Orthogonalization)'이라는 방법을 제안합니다. 이 방법은 먼저 6개의 S3M을 사용하여 음성 데이터를 특징으로 추출하고, 이 특징들을 연속적인 언어 식별 임베딩(LI) 공간으로 매핑합니다. 이후, 이 매핑된 공간에서 언어적 혼란을 제거하기 위해 연속적인 언어 표현에서 해당 매핑된 부분을 차감합니다.

## 실험·결과

제안하는 방법은 6개의 S3M과 모든 실험 설정에서 일관되게 낮은 EER(Error Rate)를 달성했습니다. 특히, 먼 언어 간의 전이에서 더 큰 성능 향상을 보였으며, 이는 언어적 혼란 제거가 먼 언어 간의 전이 문제 해결에 효과적임을 시사합니다.

## 한계

본 연구는 6개의 South Asia 언어에 국한되어 실험되었으며, 다른 언어 집단이나 더 많은 언어에 대한 일반화 가능성은 아직 검증되지 않았습니다. 또한, 제안하는 방법이 모든 유형의 디프페이크 공격에 대해 동일한 성능을 보장하는지는 추가적인 연구가 필요합니다.

---
_Part of [audio-deepfake-detection-papers](https://github.com/woongja/audio-deepfake-detection-papers) · AI-generated summary, unverified._
