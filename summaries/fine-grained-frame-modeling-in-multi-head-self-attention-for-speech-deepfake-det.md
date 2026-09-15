# Fine-Grained Frame Modeling in Multi-head Self-Attention for Speech Deepfake Detection

> ⚠ AI-generated summary (local LLM, **Korean**, unverified) — auto-generated from the paper, not fact-checked. Verify against the source.

**arXiv:** https://arxiv.org/abs/2602.04702 · Tuan Dat Phuong et al. · 2026

## 한 줄 요약

본 논문에서는 음성 디페이크 탐지에 효과적인 fine-grained 프레임 모델링(FGFM) 기법을 제안합니다. 이는 multi-head self-attention 메커니즘에서 중요한 미세한 시간적 특징을 포착하여 디페이크 신호의 특징을 더 정확하게 감지하는 데 기여합니다.

## 문제 정의

음성 디페이크 기술의 발전은 금융, 통신, 접근 통제 등 생체 인식 시스템에 심각한 위협을 가하며, 허위 정보 및 사회 공학 공격과 같은 광범위한 위험을 야기합니다. 기존의 음성 디페이크 탐지 방법들은 주로 전역적인 특징을 활용하여 디페이크 신호의 미세하고 국소적인 특징을 놓치는 경우가 많습니다.

## 제안 방법

본 논문에서는 multi-head self-attention (MHSA) 기반 음성 디페이크 탐지를 위해 fine-grained 프레임 모델링 (FGFM) 기법을 제안합니다. FGFM은 먼저 multi-head voting (MHV) 모듈을 통해 각 MHSA 헤드에서 가장 중요한 프레임을 선택하고, 선택된 프레임을 cross-layer refinement (CLR) 모듈을 통해 여러 레이어에 걸쳐 통합합니다. 또한, DAF (Dynamic Aggregation Feed-Forward) 모듈을 사용하여 fine-grained 프레임 정보를 분류 토큰에 효과적으로 통합하여 디페이크 신호의 미세한 특징을 더 잘 포착하도록 합니다.

## 실험·결과

본 논문에서는 ASRvspoof 2021 LA, DF, 그리고 In-the-Wild (ITW) 데이터셋에서 제안된 FGFM 모델의 성능을 평가했습니다. 실험 결과, FGFM 모델은 baseline 모델 대비 21LA에서 7.2%, 21DF에서 27.1%, ITW에서 21.1%의 상대적인 EER 감소를 보였습니다. 또한, 기존의 state-of-the-art 모델들과 비교하여 우수한 성능을 달성했으며, 특히 out-of-domain ITW 데이터셋에서 가장 높은 EER (6.64%)를 기록했습니다.

## 한계

본 연구는 fine-grained 프레임 모델링이 음성 디페이크 탐지에 효과적임을 보였지만, 실제 환경에서의 다양한 노이즈 및 변형에 대한 강건성 측면에서는 추가적인 연구가 필요합니다. 또한, MHV 모듈에서 선택하는 프레임 수에 대한 최적의 값은 데이터셋 및 모델 구조에 따라 달라질 수 있으며, 이에 대한 더 심층적인 분석이 필요합니다.

---

## 1 Introduction

음성 디페이크 기술의 발전은 금융, 통신, 접근 통제 등 생체 인식 시스템에 심각한 위협을 가하며, 허위 정보 및 사회 공학 공격과 같은 광범위한 위험을 야기합니다. 이러한 문제에 대응하기 위해 ASVspoof 시리즈 및 최근의 VSASV 2024 챌린지와 같은 다양한 연구들이 합성 음성 탐지 (SSD) 방법 개발을 촉진해 왔습니다. 이러한 방법들 중 transformer 기반 아키텍처, 특히 wav2vec 2.0 및 WavLM과 같은 사전 학습된 self-supervised 학습 모델을 활용하는 것이 현재 최첨단 기술로 자리 잡았습니다. 이는 multi-head self-attention (MHSA) 메커니즘 덕분인데, MHSA는 시간적 차원에 걸친 프레임 수준의 의존성을 포착하며, 각 attention head는 고유한 음향 패턴에 대한 민감도를 나타내므로 디페이크 신호의 특징을 감지하는 데 적합합니다.

그러나 MHSA는 attention 출력을 전역적으로 집계된 특징으로 취급하며, 합성 음성 탐지에 중요한 미세한 시간적 역학을 간과합니다. 일반적인 MHSA에서는 attention이 전체 시퀀스에 분산되어 있지만, 디페이크 신호의 미세한 이상 신호들을 강조하거나 우선순위를 부여하는 명시적인 메커니즘이 없으면 합성 음성에서 이러한 미세한 이상 신호들이 희석되거나 무시될 수 있습니다. 이전 연구들은 합성 디페이크가 불규칙한 전환이나 특정 음절과 같이 짧고 시간적으로 드문 지역에 나타날 수 있음을 보여주었습니다. 이러한 국소적인 이상 신호들은 프레임 수준 모델링이 너무 거칠거나 시퀀스 전체에 걸쳐 암묵적으로 평균화되는 경우 감지되지 않을 수 있습니다. 또한 최근 연구에서는 각 attention head가 서로 다른 유형의 음향 패턴을 포착하는 데 특화되어 있다는 점이 밝혀졌으며, 이는 head 수준 선택 또는 가중 메커니즘이 디페이크 신호에 대한 민감도를 높이는 데 도움이 될 수 있음을 시사합니다.

이러한 관찰에 따라 음성 디페이크 탐지를 위한 fine-grained 프레임 모델링 (FGFM) 접근 방식을 제안합니다. 제안된 FGFM은 먼저 multi-head voting (MHV) 모듈을 사용하여 각 MHSA head에서 가장 중요한 프레임을 선택하여 디페이크 감지에 유용한 미세한 프레임을 식별합니다. 선택된 프레임은 그런 다음 cross-layer refinement (CLR) 모듈을 통해 여러 레이어에 걸쳐 통합되어 분류 토큰을 풍부하게 만듭니다. MHV 및 CLR 모듈은 원래 시각적 분류 작업에 도입되었지만, 음성 디페이크 탐지에서 선택적 정보 모델링을 강화하는 데 적합하다는 점을 보여줍니다. 다양한 벤치마크에서 평가한 결과, 제안된 방법은 baseline 모델 대비 7.2%, 27.1%, 21.1%의 상대적인 EER 감소를 보이며, 합성 음성 디페이크 탐지에 효과적인 fine-grained 모델링이 중요하다는 것을 강조합니다.

## 2 Methodology

Figure [1](#S1.F1 "Figure 1 ‣ 1 Introduction ‣ Fine-Grained Frame Modeling in Multi-head Self-Attention for Speech Deepfake Detection")는 제안하는 Fine-Grained Frame Modeling (FGFM) 방법의 개요를 보여줍니다. 본문에서는 baseline인 XLSR-Conformer 모델과 제안하는 방법의 주요 구성 요소인 Multi-Head Voting (MHV) 및 Cross-Layer Refinement (CLR) 모듈에 대해 설명합니다.

## 2.1 The baseline model

본 연구의 baseline 모델은 사전 학습된 XLS-R 모델을 feature extractor (FE)로 사용하고 Conformer 모델을 결합한 XLSR-Conformer 모델입니다. 입력 신호 OO에 대해 FE는 TT-프레임 시퀀스 임베딩을 출력하며, 이는 선형 투영 레이어를 통해 DD차원 공간으로 투영됩니다. 학습 가능한 분류 토큰 XCLS는 투영된 입력 임베딩 Xseq에 선행하여 XX를 형성합니다. 이 입력 시퀀스는 LL MHSA 기반 Conformer 블록을 통과하며, 각 블록은 출력 표현 Xl을 생성합니다. 마지막으로 마지막 블록의 업데이트된 분류 토큰은 분류 헤드로 전달됩니다.

## 2.2 Multi-Head Voting (MHV) module

MHV 모듈은 각 MHSA 헤드에서 선택된 프레임을 통합하여 디페이크 신호의 특징을 더 잘 포착하는 데 사용됩니다. 각 헤드에서 선택된 프레임은 가중치를 부여한 후 합산되어 분류 토큰에 통합됩니다.

## 2.3 Cross-Layer Refinement (CLR) module

CLR 모듈은 여러 레이어에 걸쳐 정보를 통합하여 분류 토큰을 풍부하게 만듭니다. 이는 각 레이어의 출력을 연결하여 수행됩니다.

## 2.4 Dynamic Aggregation Feed-Forward (DAF) module

DAF 모듈은 fine-grained 프레임 정보를 분류 토큰에 효과적으로 통합하는 데 사용됩니다. 이는 각 프레임의 특징을 가중치 부여한 후 합산하여 수행됩니다.

## 2.5 Number of votes per head in MHV module

MHV 모듈에서 각 헤드당 선택하는 프레임 수는 16, 24, 32, 40으로 실험했습니다. 결과는 24 프레임이 최적의 성능을 보이며, 이는 디페이크 신호의 중요한 특징을 포착하면서 불필요한 노이즈를 줄이는 데 효과적임을 나타냅니다.

## 2.6 Key features that models focus on in speech

Figure [2](#S3.F2 "Figure 2 ‣ 3.3.3 Key features that models focus on in speech ‣ 3.3 Ablation studies ‣ 3 Experiments ‣ Fine-Grained Frame Modeling in Multi-head Self-Attention for Speech Deepfake Detection")는 MHV 모듈에서 선택된 프레임을 spectrogram와 비교하여 음성 신호의 특징을 보여줍니다. 빨간색 수직선은 MHV 모듈에서 선택된 프레임을 나타내며, 이는 디페이크 신호에서 중요한 음성 영역을 포착하고 침묵 또는 낮은 정보 영역을 피하는 데 효과적임을 보여줍니다.

## 3 Ablation studies

본 연구에서는 제안된 FGFM 프레임워크의 각 구성 요소의 기여도를 평가하기 위해 XLSR-Conformer baseline 모델을 기반으로 다양한 실험을 수행했습니다.

## 3.1 The effectiveness of each proposed module

먼저 DAF 모듈을 제거하고 MHV 모듈에서 직접 분류 헤드로 전달하는 경우를 실험했습니다. 결과는 21LA, 21DF, ITW 데이터셋에서 상대적인 EER이 각각 8.2%, 5.1%, 2.7% 감소했음을 보여줍니다. 이는 DAF 모듈이 fine-grained 프레임 정보를 분류 토큰에 효과적으로 통합하는 데 기여함을 나타냅니다. 두 번째로 MHV 모듈의 가우시안 커널 렌즈를 제거한 경우를 실험했습니다. 결과는 21LA, 21DF, ITW 데이터셋에서 상대적인 EER이 각각 15.6%, 8.0%, 5.1% 감소했음을 보여줍니다. 이는 가우시안 커널 렌즈가 선택된 프레임의 품질을 향상시키는 데 기여함을 나타냅니다.

## 3.2 The number of votes per head in MHV module

MHV 모듈에서 각 헤드당 선택하는 프레임 수를 16, 24, 32, 40으로 실험했습니다. 결과는 24 프레임이 최적의 성능을 보이며, 이는 디페이크 신호의 중요한 특징을 포착하면서 불필요한 노이즈를 줄이는 데 효과적임을 나타냅니다.

## 4 Conclusion

본 논문에서는 음성 디페이크 탐지에 효과적인 fine-grained 프레임 모델링 (FGFM) 기법을 제안했습니다. 실험 결과, 제안된 FGFM 모델은 baseline 모델 대비 21LA, DF, ITW 데이터셋에서 일관되게 우수한 성능을 보였습니다. 이는 선택적 정보 모델링이 음성 디페이크 탐지 모델의 강건성을 향상시키는 데 기여함을 보여줍니다.

## 5 Acknowledgement

본 연구는 베트남 교육훈련부의 CT2025.EA.BKA.04 프로젝트 지원을 받았습니다.

---
_Part of [audio-deepfake-detection-papers](https://github.com/woongja/audio-deepfake-detection-papers) · summary auto-generated by a local LLM, unverified._
