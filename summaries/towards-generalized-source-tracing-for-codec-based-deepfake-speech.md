# Towards Generalized Source Tracing for Codec-Based Deepfake Speech

> ⚠ AI-generated summary (local LLM, **Korean**, unverified) — auto-generated from the paper, not fact-checked. Verify against the source.

**arXiv:** https://arxiv.org/abs/2506.07294 · Xuan-Bo Chen et al. · 2025

## 한 줄 요약

본 논문에서는 코덱 기반 딥페이크 음성에서 소스 트레이싱 성능을 향상시키기 위해 의미론적 정보와 음향적 정보를 결합한 SASTNet 모델을 제안하고, 다양한 실험을 통해 그 효과를 입증합니다.

## 문제 정의

기존의 코덱 기반 딥페이크 음성 소스 트레이싱 모델은 코덱 특이적인 특징과 음성 내용 간의 관계를 제대로 파악하지 못하여, 특히 unseen한 내용이나 다양한 코덱 환경에서 성능 저하를 겪는다는 문제가 있습니다.

## 제안 방법

본 논문에서는 이러한 문제를 해결하기 위해 Semantic Encoder와 Coarse-to-Fine Acoustic Encoder를 결합한 Semantic-Acoustic Source Tracing Network (SASTNet)을 제안합니다. Semantic Encoder는 음성의 의미론적 정보를 추출하고, Acoustic Encoder는 코덱 특이적인 음향 정보를 추출합니다. 이 두 정보를 Transformer 기반의 Fusion Transformer를 통해 통합하여 소스 트레이싱 예측을 수행합니다.

## 실험·결과

SASTNet은 CodecFake+ 데이터셋에서 다양한 소스 트레이싱 태스크(VQ, AUX, DEC)에서 기존 모델 대비 높은 F1 점수를 달성했습니다. 특히, CoSG 테스트에서 기존 모델 대비 50% 이상의 성능 향상을 보였으며, unseen real speech 감지에서 두드러진 성능 향상을 보였습니다. 또한, 다양한 코덱 환경에서도 높은 일반화 성능을 보여주었습니다.

## 한계

본 연구는 코덱 기반 딥페이크 음성 소스 트레이싱 성능 향상에 초점을 맞추었으며, 다른 형태의 딥페이크 탐지 및 분석에는 적용되지 않았습니다. 또한, SASTNet 모델의 복잡성으로 인해 계산 비용이 증가할 수 있다는 점이 한계로 지적됩니다.

---

## I Introduction

딥페이크 탐지는 주어진 음성이 실제 음성인지 딥페이크 음성인지 판별하는 작업입니다. 이 분야는 AVSspoof, ADD 등 다양한 데이터셋과 함께 여러 가지 어려움과 도전 과제를 제시해 왔습니다. 최근에는 단순히 딥페이크 음성을 탐지하는 것에서 벗어나, 그 소스(origin)를 추적하는 연구가 중요해지고 있습니다. 소스 추적은 딥페이크 음성의 기원이나 생성 알고리즘에 대한 중요한 통찰력을 제공하며, 특히 도메인 외 탐지 시나리오에서 매우 유용합니다. 예를 들어, ADD 2023의 Track 3은 딥페이크 음성의 기저 알고리즘을 식별하는 데 집중했으며, InterSpeech 2025에서는 딥페이크 소스 추적에 대한 특별 세션이 개최될 예정입니다.

소스 추적의 가장 간단한 접근 방식은 딥페이크 음성을 생성한 특정 공격 모델 ID로 매핑하는 것입니다. 일반화 성능을 높이기 위해, 이 분야는 다양한 속성을 기반으로 소스 추적을 수행하는 방향으로 발전해 왔습니다. 이러한 방법은 각 딥페이크 시스템을 고유한 범주로 취급하는 대신, 많은 딥페이크 파이프라인이 공통 요소를 공유한다는 점을 고려하여 시스템을 그룹화합니다. 이러한 속성에 집중함으로써, 훈련 중에 알 수 없었던 요소로 구축되었지만 훈련 중에 알려진 요소에서 파생된 딥페이크 알고리즘을 보다 효과적으로 추적할 수 있습니다. 전통적인 TTS(Text-to-Speech) 및 VC(Voice Conversion) 아키텍처에서 유래된 잘 정의된 속성(입력 유형, 음향 모델, 스피커 표현, 보코더 등)을 분류하는 연구가 활발히 진행되고 있습니다.

그러나 이러한 이전 연구들은 전통적인 TTS/VC 시스템에서의 소스 추적에 초점을 맞추고 있으며, 코덱 기반 음성 생성(CoSG) 모델에는 제한적으로 적용되었습니다. Xie 등은 소스 추적을 닫힌 집합 분류 문제로 정의하며, 알려진 CoSG 시스템 ID를 식별하고 이진 오프-도메인 탐지기를 사용하는 방법을 제시했습니다. 그러나 이 접근 방식은 여러 개의 알려지지 않은 생성기가 등장하는 경우에 실패합니다. 최근에는 코덱 기반 딥페이크 음성에 대한 연구가 증가하고 있지만, 기존 연구들은 여전히 제한적입니다. 예를 들어, Chen 등은 CodecFake+ 택소노미를 활용하여 코덱 속성 기반의 세 가지 소스 추적 태스크를 정의했습니다. 그들은 또한 코덱 기반 음성 생성 데이터로 훈련된 모델이 CoSG 생성 음성에서 unseen한 코덱 유형으로 인해 심각한 일반화 문제를 겪는다는 것을 보여주었습니다.

본 논문은 코덱 재합성 음성에 과적합되는 경향과 unseen한 음성 콘텐츠에 대한 일반화 문제에 초점을 맞추어, Semantic-Acoustic Source Tracing Network (SASTNet)을 제안합니다. SASTNet은 의미론적 특징 인코더와 코어-투-파인 음향 인코더를 결합하여, 콘텐츠 보존과 함께 코덱 특이적인 정밀한 음향 특징을 포착합니다. 이를 통해 CodecFake+에서 코덱 기반 딥페이크 소스 추적 성능을 크게 향상시킵니다. 코드베이스는 향후 연구를 지원하기 위해 공개될 예정입니다.

## II Background

신경 음성 코덱은 벡터 양자화, 보조 목표, 디코더 유형이라는 세 가지 축을 따라 "지문"을 남깁니다. 이 세 축은 대부분의 코덱 설계를 포괄하며, 코덱 기반 딥페이크에 대한 강력한 추적을 가능하게 합니다. Chen 등은 이러한 택소노미를 기반으로 CodecFake 소스 추적을 위한 세 가지 다중 클래스 분류 태스크를 정의했습니다.

* **벡터 양자화 분류 (VQ 태스크):** 모델이 다중 코북, 단일 코북 또는 스칼라 양자화를 사용하는 코덱으로 생성된 음성을 실제 음성인지 여부를 분류하는 4개 클래스 분류입니다.
* **보조 목표 분류 (AUX 태스크):** 모델이 의미론적 정제 또는 분리 목표를 사용하는 코덱으로 생성된 음성을 실제 음성인지 여부를 분류하는 3개 클래스 분류입니다.
* **디코더 유형 분류 (DEC 태스크):** 모델이 시간 또는 주파수 도메인 디코더를 사용하는 코덱으로 생성된 음성을 실제 음성인지 여부를 분류하는 3개 클래스 분류입니다.

추가적으로, 전통적인 딥페이크 방지 태스크인 이진 스푸프 탐지 (BIN 태스크)도 포함됩니다.

![Refer to caption](/html/2506.07294/assets/SASTNet_draft_v4.drawio.png)

그림 1: Semantic-Acoustic Source Tracing Network 개요.

## III Semantic-Acoustic Source Tracing Network

본 섹션에서는 Semantic-Acoustic Source Tracing Network (SASTNet)을 소개하고, 그 설계의 의도를 설명합니다. Chen 등은 이전 연구에서 자기 지도 학습 모델을 전처리 특징 추출기로 사용하고, 소스 추적을 위한 분류기를 사용했지만, 이들의 접근 방식은 종종 음향 정보에 치중하여 의미론적 단서를 간과하는 경향이 있었습니다.

본 연구에서는 효과적인 소스 추적을 위해서는 코덱 왜곡으로 인한 미세한 음향 패턴과 의미론적 일관성을 유지하는 것이 중요하다는 점을 인식합니다. 실제로 Kawa 등은 의미론적 특징과 음향적 특징을 결합하는 것이 딥페이크 특징을 더 잘 포착하는 데 도움이 된다는 것을 보여주었습니다.

코덱 왜곡으로 인한 음향 특징에만 의존하면, 말하는 내용이 변경될 때 발생하는 자연스러운 변화가 코덱 특징으로 오인될 수 있다는 중요한 사실을 간과하게 됩니다. 만약 언어적 내용과 무관한 음향 특징만 집중한다면, 다른 단어나 발음으로 인해 발생하는 자연스러운 변화가 코덱 특징으로 오인될 수 있습니다.

반대로, 의미론적 정보를 보존함으로써 네트워크는 입력 음성의 내용과 무관한 정보에 집중하고, 내용과 독립적인 미세한 음향 편차만을 식별할 수 있습니다.

그림 [1](#S2.F1 "Fig. 1 ‣ II Background ‣ Towards Generalized Source Tracing for Codec-Based Deepfake Speech") (a)는 SASTNet의 프레임워크를 보여줍니다. 입력 파형에 대해 SASTNet은 Section [II](#S2 "II Background ‣ Towards Generalized Source Tracing for Codec-Based Deepfake Speech")에서 정의된 태스크를 기반으로 코덱 소스 레이블을 예측합니다. SASTNet은 Semantic Encoder, 코어-투-파인 음향 Encoder라는 두 가지 전처리 인코더와 Semantic-to-Acoustic (SA), Acoustic-to-Semantic (AS), Fusion Transformer라는 세 가지 백엔드 분류기로 구성됩니다. 전처리 인코더는 각각 고수준 언어적 임베딩과 코덱 특이적인 정밀한 음향 특징을 추출합니다. 백엔드 분류기는 크로스-메커니즘 Transformer를 사용하여 의미론적 정보와 음향적 정보를 통합합니다. SA Transformer에서는 의미론적 특징이 쿼리로, 음향적 특징이 키와 값으로 사용됩니다. AS Transformer에서는 이 역할이 서로 바뀝니다. Fusion Transformer는 AS 출력과 SA 출력을 키와 값으로 사용하여 두 모달리티를 통합합니다. 마지막으로, AASIST 백엔드 모델은 융합된 표현을 사용하여 소스 추적 예측을 생성합니다. 각 블록의 자세한 설정은 다음 섹션에서 설명합니다.

## III-A Semantic Encoder

Semantic Encoder는 Whisper 모델을 활용하여 콘텐츠에 대한 의미론적 정보를 추출합니다.

## III-B Acoustic Encoder

Acoustic Encoder는 코덱 특이적인 음향 특징을 추출합니다.

## III-C Fusion Transformer

Fusion Transformer는 Semantic Encoder와 Acoustic Encoder에서 추출된 의미론적 정보와 음향적 정보를 통합하여 소스 추적 예측을 수행합니다.

## VI Conclusion

결론적으로, 본 연구에서는 코덱 재합성 음성으로 훈련된 모델이 침묵 영역에 과적합되고 unseen한 콘텐츠에 대한 일반화에 실패하는 경향이 있음을 보여주었습니다. 이러한 한계를 극복하기 위해 의미론적 정보와 음향적 정보를 결합한 SASTNet을 제안했으며, 다양한 실험을 통해 그 효과와 견고성을 입증했습니다.

---
_Part of [audio-deepfake-detection-papers](https://github.com/woongja/audio-deepfake-detection-papers) · summary auto-generated by a local LLM, unverified._
