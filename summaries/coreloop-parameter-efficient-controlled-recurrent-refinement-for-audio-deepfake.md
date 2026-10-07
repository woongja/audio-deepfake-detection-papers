# CoRELoop: Parameter-Efficient Controlled Recurrent Refinement for Audio Deepfake Detection

> ⚠ AI-generated summary (local LLM, **Korean**, unverified) — auto-generated from the paper, not fact-checked. Verify against the source.

**arXiv:** https://arxiv.org/abs/2609.19818 · > **제출일:** 2026-09-17 · 2026

## 한 줄 요약

본 논문은 기존 SSL 기반 음성 디텍터의 첫 번째 패스 예측과 파라미터를 고정하고, Recurrent-depth refinement 모듈과 low-rank adapter를 추가하여 추가적인 성능 향상을 달성하는 CoReLoop라는 새로운 방법을 제안합니다.

## 문제 정의

음성 디딥페이크 탐지는 합성 또는 음성 변환으로 생성된 음성과 실제 음성을 구별하는 것을 목표로 합니다. 기존의 많은 디텍터는 self-supervised learning (SSL)을 활용하여 학습되지만, 실제 환경에서의 다양한 공격에 대한 일반화 능력이 부족하고, 새로운 공격에 대한 학습 데이터 확보가 어렵다는 문제가 있습니다.

## 제안 방법

본 논문에서는 기존 SSL 기반 디텍터의 첫 번째 패스 예측과 파라미터를 고정하고, Recurrent-depth refinement 모듈과 loop-specific low-rank adapter를 추가하는 CoReLoop라는 방법을 제안합니다. Recurrent-depth refinement 모듈은 입력 데이터를 순환적으로 처리하여 디텍터의 성능을 향상시키고, low-rank adapter는 refinement 모듈의 출력을 기존 디텍터의 최종 레이어에 효과적으로 통합합니다. 또한, adaptive inference를 통해 각 발화에 대한 refinement 깊이를 동적으로 조절하여 효율적인 처리를 가능하게 합니다.

## 실험·결과

CoReLoop는 14개의 크로스 도메인 테스트 세트에서 기존 SSL 기반 디텍터의 성능을 크게 향상시켰습니다. 특히, 24 레이어 모델에서 2회 패스 refinement를 사용했을 때 pooled EER이 4.85%에서 3.74%로 감소하는 상당한 성능 개선을 보였습니다. 약 1000만 개의 trainable 파라미터로 기존 디텍터의 성능을 유지하면서 추가적인 성능 향상을 달성했으며, adaptive inference를 통해 평균 1.18회 패스에서 3.73%의 pooled EER을 달성했습니다.

## 한계

본 연구는 기존 SSL 기반 디텍터의 첫 번째 패스 예측과 파라미터를 고정하는 방식으로, 새로운 공격에 대한 일반화 능력을 더욱 향상시킬 수 있는지는 명확하게 검증하지 않았습니다. 또한, Recurrent-depth refinement 모듈과 low-rank adapter의 최적화 및 하이퍼파라미터 튜닝에 대한 자세한 분석은 부족합니다.

---
_Part of [audio-deepfake-detection-papers](https://github.com/woongja/audio-deepfake-detection-papers) · AI-generated summary, unverified._
