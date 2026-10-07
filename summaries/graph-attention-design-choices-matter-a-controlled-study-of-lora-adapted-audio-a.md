# Graph Attention Design Choices Matter: A Controlled Study of LoRA-Adapted Audio Anti-Spoofing

> ⚠ AI-generated summary (local LLM, **Korean**, unverified) — auto-generated from the paper, not fact-checked. Verify against the source.

**arXiv:** https://arxiv.org/abs/2609.15650 · Haoyu Wang et al. · 2026

## 한 줄 요약

본 연구는 LoRA에 적합한 XLS-R-300M + AASIST2 음성 스푸핑 방지 시스템에서 그래프 어텐션 레이어의 세 가지 핵심 설계 요소(스코어링 대칭성, 온도 학습 가능성, 라우팅 세분성)를 체계적으로 분석하여, LearnT 브랜치가 가장 높은 성능을 보이며, 설계 요소 간의 상호작용이 중요함을 밝힙니다.

## 문제 정의

음성 스푸핑 방지 시스템은 최근 생성형 음성의 발달로 인해 실제 녹음과 구별하기 어려워지면서 심각한 위협에 직면하고 있습니다. 이러한 시스템은 일반적으로 self-supervised 학습 프론트엔드와 그래프 어텐션 기반 백엔드를 결합하는 방식을 사용하며, 최근에는 LoRA 스타일의 parameter-efficient fine-tuning 기법이 추가되고 있습니다. 그러나 이러한 시스템에서 그래프 어텐션 백엔드의 내부 설계 선택이 성능에 미치는 영향은 명확하게 규명되지 않았습니다.

## 제안 방법

본 연구에서는 LoRA에 적합한 음성 스푸핑 방지 시스템에서 그래프 어텐션 레이어의 설계 선택을 체계적으로 분석하기 위해, 세 가지 독립적으로 테스트 가능한 설계 차원(스코어링 대칭성, 온도 학습 가능성, 라우팅 세분성)을 정의했습니다. 각 차원은 해당 설계에 해당하는 residual branch로 구현되었으며, 동일한 실험 설정을 통해 각 변형과 그 조합을 평가했습니다.

## 실험·결과

다양한 평가 세트(ASVspoof 2019 LA, ASVspoof 2021 LA, DF21, WaveFake, In-the-Wild)에 걸쳐 5개의 랜덤 시드에 대해 실험을 진행한 결과, LearnT 브랜치가 가장 높은 평균 동일 오류율(EER)을 달성했습니다(Baseline 대비 16.1% 상대적 개선). GAtv2+MT 조합은 두 번째로 높은 평균 EER을 보였으며, 시드 수준 표준 편차가 가장 낮았습니다. 특히, 두 가지 개별적으로 유용한 브랜치를 함께 사용했을 때 성능이 크게 저하되는 경향을 보였습니다. LearnT은 In-the-Wild 평가 세트에서 Out-of-Domain EER을 13.24%에서 11.09%로 개선하는 등, Out-of-Domain 성능 향상에 기여하는 것으로 나타났습니다.

## 한계

본 연구는 LoRA에 적합한 XLS-R-300M + AASIST2 시스템 내에서 그래프 어텐션 레이어의 설계 선택에 국한됩니다. 또한, 실험 설정은 고정되어 있어 실제 환경에서의 다양한 조합이나 다른 모델 아키텍처에 대한 일반화 가능성은 제한적입니다.

---
_Part of [audio-deepfake-detection-papers](https://github.com/woongja/audio-deepfake-detection-papers) · AI-generated summary, unverified._
