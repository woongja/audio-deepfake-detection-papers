# GenTraceBench: A Benchmark for Tracing Audio Deepfakes Across Pre- and Post-training Stages

> ⚠ AI-generated summary (local LLM, **Korean**, unverified) — auto-generated from the paper, not fact-checked. Verify against the source.

**arXiv:** https://arxiv.org/abs/2609.21738 · > **제출일:** 2026-09-18 · 2026

## 한 줄 요약

본 논문은 음성 생성 모델의 전처리 및 후처리 단계에서 다양한 변수를 적용하여 음성 디피케 탐지 모델의 견고성을 평가하기 위한 통제된 벤치마크인 GenTraceBench를 제안합니다.

## 문제 정의

현대의 텍스트 음성 변환(TTS) 시스템은 주로 전처리 및 후처리 단계에서 고정된 상태로 개발되며, 학습 데이터의 구성 변화가 모델에 미치는 영향에 대한 체계적인 평가가 부족합니다. 특히, 학습 데이터의 변화가 모델의 성능에 미치는 영향과 음성 디피케 탐지 모델의 견고성 사이의 관계에 대한 이해가 필요합니다.

## 제안 방법

본 논문에서는 음성 생성 모델의 전처리 및 후처리 단계에서 다양한 변수를 적용하여 모델의 견고성을 평가하기 위한 GenTraceBench라는 통제된 벤치마크를 제안합니다. 이 벤치마크는 5가지 대표적인 음성 생성 아키텍처를 사용하며, 학습 데이터의 구성, 프롬프트, 스피커 식별자 등을 변경하여 다양한 시나리오를 실험합니다.

## 실험·결과

GeniTraceBench는 5가지 음성 생성 아키텍처(총 16가지 변형)를 대상으로 전처리 및 후처리 단계에서 다양한 변수를 적용한 실험을 수행했습니다. 실험 결과, W2V-BERT 모델에서 프롬프트와 스피커 식별자를 모두 변경했을 때, 학습 데이터 구성 변화로 인한 드리프트가 줄어드는 효과를 확인했습니다. 또한, 학습 데이터 구성 변화가 발생해도 모델의 성능은 크게 영향을 받지 않는다는 것을 입증했습니다.

## 한계

본 연구는 통제된 환경에서 다양한 변수를 적용하여 모델의 견고성을 평가했지만, 실제 환경에서 발생할 수 있는 다양한 요인들을 모두 반영하지 못할 수 있습니다. 또한, 제안된 벤치마크는 음성 디피케 탐지 모델의 견고성을 평가하는 데 초점을 맞추고 있으며, 다른 측면의 평가에는 미흡할 수 있습니다.

---
_Part of [audio-deepfake-detection-papers](https://github.com/woongja/audio-deepfake-detection-papers) · AI-generated summary, unverified._
