# CRAF: Cross-View Residual-Aware Fusion for Deepfake Speech Detection

> ⚠ AI-generated summary (local LLM, **Korean**, unverified) — auto-generated from the paper, not fact-checked. Verify against the source.

**arXiv:** https://arxiv.org/abs/2609.13842 · Minh-Xuan Phan et al. · 2026

## 한 줄 요약

본 논문은 SSL(Self-Supervised Learning)과 ALM(Large Language Models)의 장점을 결합하여 디프페이크 음성 탐지 성능을 향상시키는 새로운 프레임워크 CRAF을 제안한다.

## 문제 정의

디프페이크 음성 기술의 발전으로 인해 음성 디테크션의 정확도가 중요한 문제로 부상하고 있다. 기존의 디테크션 방법들은 종종 디프페이크 음성의 미묘한 음향적 특징을 놓치거나, 다양한 공격에 대한 일반화 능력이 부족하다는 한계를 가진다.

## 제안 방법

본 논문에서는 CRAF(Cross-view Residual Aware Fusion for Deepfake Speech Detection)라는 새로운 프레임워크를 제안한다. CRAF은 Self-Supervised Learning (SSL)을 통해 얻은 음향적 특징과 Large Language Models (ALM)을 통해 얻은 고수준의 의미적 정보를 결합한다. 특히, ALM을 사용하여 SSL 표현을 보강하고, residual attention 메커니즘을 통해 cross-view 정보를 효과적으로 통합한다.

## 실험·결과

논문에서는 CRAF 프레임워크의 성능을 실험적으로 검증했지만, 구체적인 수치 결과는 제시되지 않았다.

## 한계

본 논문에서 제안하는 CRAF 프레임워크는 ALM을 활용하여 cross-view 정보를 통합하지만, ALM의 계산 비용이 높고, 특정 도메인에 대한 성능이 제한될 수 있다는 한계가 있다. 또한, 디프페이크 음성의 공격 기법이 발전함에 따라 CRAF의 성능이 저하될 가능성도 존재한다.

---
_Part of [audio-deepfake-detection-papers](https://github.com/woongja/audio-deepfake-detection-papers) · AI-generated summary, unverified._
