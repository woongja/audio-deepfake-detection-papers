# Synthetic speech detection in Brazilian Portuguese through accent-related features

> ⚠ AI-generated summary (local LLM, **Korean**, unverified) — auto-generated from the paper, not fact-checked. Verify against the source.

**arXiv:** https://arxiv.org/abs/2609.23807 · > **제출일:** 2026-09-20 · 2026

## 한 줄 요약

본 연구는 브라질 포르투갈어의 지역 방언 다양성이 TTS 모델의 성능에 미치는 영향을 분석하고, 합성 음성과 자연어 음성을 구별하기 위한 새로운 음성 특징 추출 및 분류 방법을 제안하며, 다양한 데이터셋에서 높은 정확도와 일반화 성능을 입증합니다.

## 문제 정의

기존의 TTS 모델은 브라질 포르투갈어의 지역 방언 다양성을 제대로 반영하지 못하며, 이는 합성 음성 콘텐츠에 대한 사용자들의 신뢰도와 만족도에 부정적인 영향을 미칩니다. 특히, 합성 음성 데이터만으로 학습된 모델은 자연어 음성 데이터와 다른 특징을 가지는 합성 음성을 효과적으로 구별하기 어렵습니다. 또한, 합성 음성 데이터의 특징은 지역 방언 간의 차이를 숨기거나 왜곡하여 합성 음성 감지 작업을 더욱 어렵게 만듭니다.

## 제안 방법

본 연구에서는 브라질 포르투갈어의 지역 방언 특징을 효과적으로 추출하기 위해 ZIPA(Zeppelin-based Phoneme Alignment) 및 Formants 특징을 활용하는 새로운 음성 특징 추출 방법을 제안합니다. 추출된 특징은 합성 음성과 자연어 음성을 구별하기 위한 분류 모델에 입력됩니다. 또한, 합성 음성 데이터만으로 학습된 모델의 성능 저하 문제를 해결하기 위해 double leave-one-dataset-out 교차 검증 전략을 적용하여 모델의 일반화 성능을 평가합니다.

## 실험·결과

본 연구에서는 BRSpeechDF, FakeBRAccent, MLAAD-pt 등 다양한 데이터셋을 사용하여 제안된 방법의 성능을 평가했습니다. 실험 결과, 제안된 특징 집합은 자연어 음성 데이터만 사용한 실험 대비 성능 저하를 보였으나, 여전히 높은 정확도를 달성했습니다. 특히, 합성 음성 데이터만 사용한 MLAAD-pt 데이터셋에서는 거의 완벽한 정확도를 보였으며, 이는 제안된 특징이 합성 음성 데이터의 특징을 효과적으로 감지함을 시사합니다. 또한, double leave-one-dataset-out 교차 검증 전략을 통해 다양한 데이터셋에서 높은 일반화 성능을 입증했습니다.

## 한계

본 연구는 합성 음성 데이터만으로 학습된 모델의 성능 저하 문제를 해결하기 위해 double leave-one-dataset-out 교차 검증 전략을 적용했지만, 여전히 일부 데이터셋에서는 성능 향상이 미미한 결과를 보였습니다. 또한, 제안된 방법은 특정 지역 방언에 대한 성능이 다른 지역 방언에 비해 다소 낮을 수 있으며, 이는 추가적인 연구를 통해 개선될 필요가 있습니다. 마지막으로, 본 연구는 음성 특징 추출 및 분류 방법에 초점을 맞추었으며, 실제 TTS 시스템에 적용하기 위한 추가적인 연구가 필요합니다.

---
_Part of [audio-deepfake-detection-papers](https://github.com/woongja/audio-deepfake-detection-papers) · AI-generated summary, unverified._
