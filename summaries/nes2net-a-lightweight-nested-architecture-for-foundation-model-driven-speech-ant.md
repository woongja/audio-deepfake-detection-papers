# Nes2Net: A Lightweight Nested Architecture for Foundation Model Driven Speech Anti-Spoofing

> ⚠ AI-generated summary (local LLM, **Korean**, unverified) — auto-generated from the paper, not fact-checked. Verify against the source.

**arXiv:** https://arxiv.org/abs/2504.05657 · Tianchi Liu et al. · 2025

## 한 줄 요약

본 논문에서는 고차원 특징을 직접 처리하여 dimensionality reduction layer 없이도 뛰어난 성능과 효율성을 제공하는 새로운 back-end 아키텍처인 Nested Res2Net (Nes2Net)과 그 개선된 버전인 Nes2Net-X를 제안합니다.

## 문제 정의

Speech foundation models는 뛰어난 표현 능력을 제공하지만, 일반적으로 낮은 차원의 입력을 요구하는 downstream task 모델과의 호환성 문제가 있습니다. 이를 해결하기 위해 dimensionality reduction (DR) layer를 사용하는 방법이 있지만, 이는 모델 파라미터 증가, 계산 비용 증가, 정보 손실의 위험을 초래합니다. 따라서 high-dimensional feature를 효과적으로 처리하면서 이러한 문제점을 해결할 수 있는 효율적인 방법이 필요합니다.

## 제안 방법

본 논문에서는 high-dimensional feature를 직접 처리하는 Nested Res2Net (Nes2Net) 아키텍처를 제안합니다. Nes2Net은 hierarchical residual connections을 사용하여 다중 스케일 특징 추출과 특징 상호작용을 향상시키고, 고차원 정보를 보존합니다. 또한, 학습 가능한 가중치 기반 특징 융합을 추가한 Nes2Net-X는 특징 집합 과정을 더욱 강화합니다. 이러한 구조는 dimensionality reduction layer 없이도 high-dimensional feature의 정보를 효과적으로 활용하여 speech anti-spoofing task의 성능을 향상시킬 수 있도록 합니다.

## 실험·결과

본 논문에서는 CtrSVDD, ASVspoof 2021, ASVspoof 5, PartialSpoof, In-the-Wild 등 다양한 데이터셋에 대해 제안된 Nes2Net 및 Nes2Net-X 모델을 실험했습니다. 실험 결과, Nes2Net은 CtrSVDD 데이터셋에서 SOTA baseline 대비 22%의 성능 향상과 87%의 계산 비용 감소를 보였으며, In-the-Wild 데이터셋에서는 기존 SOTA 모델 대비 낮은 EER(5.52%)를 달성했습니다. AVSspoof 5 데이터셋에서는 AASIST baseline 대비 CLLR, miNDCF, EER 세 가지 지표 모두에서 10.9%의 성능 향상을 보였습니다. PartialSpoof 데이터셋에서는 기존 baseline 모델 대비 각각 36.6%, 25.6%의 성능 향상을 보이며, 특히 partial spoofing과 같이 어려운 조건에서도 우수한 성능을 입증했습니다.

## 한계

제안된 Nes2Net 및 Nes2Net-X 모델은 high-dimensional feature를 직접 처리하는 방식이므로, 모델의 복잡도가 증가할 수 있다는 잠재적인 한계가 있습니다. 또한, 학습 가능한 가중치 기반 특징 융합을 사용하는 Nes2Net-X의 경우, 추가적인 학습 과정이 필요할 수 있습니다. 향후 연구에서는 이러한 한계를 극복하고 모델의 효율성과 성능을 더욱 향상시키는 방향으로 발전할 필요가 있습니다.

## I Introduction

Speech foundation models (SFMs) such as wav2vec 2.0, HuBERT, and WavLM have significantly advanced various speech processing tasks by leveraging large-scale pre-training to capture complex acoustic and linguistic patterns. This has driven notable advances in automatic speech recognition (ASR), speaker verification (SV), and other speech applications.

Beyond traditional tasks, SFMs also show great promise in addressing critical security concerns, particularly speech anti-spoofing (also referred to as deepfake detection). With the growing sophistication of spoofing techniques, such as voice conversion, ensuring the reliability and security of speech-driven systems has become a pressing concern. Leveraging the rich representations of these foundation models could significantly improve the robustness and generalization capabilities of anti-spoofing systems.

While SFMs offer exceptional representations, their high-dimensional feature outputs present significant challenges for downstream tasks. Downstream models used in tasks like speech anti-spoofing typically require lower-dimensional features. To address this mismatch, a common approach is to introduce a dimensionality reduction (DR) layer, usually implemented as a fully connected (FC) layer for transforming high-dimensional features into lower-dimensional features. However, this conventional strategy presents notable drawbacks.

Since downstream classifiers are usually compact, the DR layer alone often consumes a substantial portion of the parameters and computational resources within the entire back-end model. Moreover, directly projecting high-dimensional features in a one-shot manner through an FC layer leads to the loss of important information, reducing the effectiveness of speech foundation models. These issues highlight the need for a more efficient and effective solution to bridge the dimensionality gap and fully utilize speech foundation models in downstream tasks.

To address these challenges, we propose Nested Res2Net (Nes2Net) to process high-dimensional features from speech foundation models, eliminating the need for a DR layer while preserving the richness of the original representations. By addressing key limitations of DR layers, such as excessive computational cost and information loss, Nes2Net offers a more efficient and effective solution. This design makes it particularly suitable for tasks requiring a balance of high performance and efficiency, such as speech anti-spoofing. The key contributions of this work can be summarized as follows:
* Novel Architecture: We introduce Nes2Net, a new approach that effectively addresses the limitations of DR layers. Nes2Net retains the expressive power of high-dimensional features while reducing model complexity.
* Enhanced Performance, Efficiency, and Generalization: Our method demonstrates significant improvements in efficiency, achieving performance improvements of 22% while reducing computational costs by 87% compared to the SOTA baseline on the CtrSVDD dataset. Further experiments conducted on four additional datasets across various scenarios demonstrate strong generalization capability and consistently superior performance.
* Reproducibility: To facilitate further research and application, we make our scripts and pre-trained models publicly available.

## II Related Work



## II-A Res2Net

Res2Net is a well-known architecture designed to extract multi-scale features. Unlike ResNet, Res2Net uses hierarchical residual connections within a single block, allowing it to capture patterns across varying receptive fields simultaneously.

This design offers proven advantages in speech-related tasks, such as SV and anti-spoofing, where capturing subtle variations and complex acoustic patterns is important. As shown in Fig. [1], Res2Net (highlighted using a light red block) can also serve as a classifier within a speech foundation model-based anti-spoofing system.

Its ability to extract multi-scale features has led to superior performance compared to conventional models, which motivates the design of Nested Res2Net in this work.

## II-B Traditional Speech Anti-Spoofing Models

Traditional speech anti-spoofing models have evolved to effectively detect speech deepfakes. For instance, the Channel-wise Gated Res2Net (CG-Res2Net) introduces a gating mechanism within the Res2Net architecture, enabling dynamic selection of channel-wise features to enhance generalization to unseen attacks. A widely recognized model among traditional approaches is AASIST, which employs spectro-temporal graph attention layers to capture both temporal and spectral artifacts, thereby achieving efficient and accurate detection.

Given AASIST’s SOTA performance and its wide adoption in recent anti-spoofing challenges, we consider it as our main baseline for evaluation.

Although traditional anti-spoofing models are characterized by their compact size and rapid inference capabilities, they typically rely on hand-crafted acoustic features, which limit their adaptability to diverse spoofing methods. With the rise of deepfakes and adversarial attacks, stronger and more flexible representations are needed.

## II-C Speech Foundation Models

Speech foundation models, often referred to as Self-Supervised Learning (SSL) models due to their typical pre-training on large amounts of unlabeled speech data using self-supervised learning techniques. Examples include wav2vec 2.0, HuBERT, and WavLM.

Unlike traditional acoustic feature-based approaches, which rely on hand-crafted features and are often task-specific, SSL models learn rich and generalized speech representations that can be effectively adapted to various downstream applications. This allows them to achieve superior performance in speech-related tasks, including speech anti-spoofing.

## II-D Speech Foundation Model-based Anti-spoofing

As discussed in the previous subsection, speech foundation models can capture more informative representations than traditional handcrafted or raw acoustic features. This makes them highly effective for speech anti-spoofing, as they generalize well across datasets and are more robust to unseen attacks. As a result, many recent anti-spoofing systems increasingly adopt these models.

## IV Experimental Setups



## V Results and Analysis

In this section, we provide an extensive validation of the proposed Nes2Net across a wide range of datasets. We begin by exploring the design motivation and development path of Nes2Net using the CtrSVDD dataset. These insights are further validated on ASVspoof 2021, ASVspoof 5, In-the-Wild, and PartialSpoof datasets. Our experimental setup covers a broad spectrum of scenarios to ensure comprehensive evaluation, including singing voice deepfakes, fully spoofed speech, adversarial attacks, partially spoofed speech, and real-world deepfake cases.

## V-E The results on the In-the-Wild dataset

TABLE VIII: Performance in EER (%) on the In-the-Wild dataset. Our result is reported as the format of ‘best (mean)’ across 3 runs.
| Front-end | Year | Back-end | EER |
| --- | --- | --- | --- |
| wav2vec 2.0 | 2022 | AASIST | 10.46 |
| 2024 | SLIM | 12.5 |
| 2024 | MoE | 9.17 |
| 2024 | Conforme | 8.42 |
| 2024 | TCM | 7.79 |
| 2024 | OCKD | 7.68 |
| 2024 | SLS | 7.08 |
| - | gMLP† | 0.35 (0.64) |
| - | 1D Res2Net† | 0.39 (0.43) |
| - | SE ResNet† | 0.31 (0.50) |
| - | Nes2Net | 0.24 (0.36) |
| - | Nes2Net-X | 0.20 (0.33) |

The In-the-Wild dataset represents real-world speech data with various acoustic conditions and spoofing types. We evaluate the performance of different models on this dataset to assess their robustness and generalization ability in realistic scenarios. The results show that Nes2Net-X consistently outperforms other models, achieving the lowest EER and demonstrating superior performance across different spoofing types and acoustic conditions.

## V-G The results on the PartialSpoof dataset

TABLE XI: Performance in EER (%) on the PartialSpoof dataset. The results are reported as the format of ‘best (mean)’ across 3 runs.
| | | | | |
| --- | --- | --- | --- | --- |
| Front-end | Dev | Eval | PartialSpoof | |
| wav2vec 2.0 | 2024 | gMLP | 0.35 | 0.64 |
| - | gMLP† | 0.39 (0.43) | 0.72 (0.80) |
| - | 1D Res2Net† | 0.35 | 0.73 |
| - | SE ResNet† | 0.31 (0.50) | 0.77 (0.78) |
| - | Nes2Net | 0.24 (0.36) | 0.53 (0.68) |
| - | Nes2Net-X | 0.20 (0.33) | 0.57 (0.64) |

The PartialSpoof dataset specifically focuses on evaluating the performance of models in the presence of partial speech manipulations, which are common in real-world spoofing attacks. The results demonstrate that Nes2Net and Nes2Net-X achieve significantly higher performance compared to baseline models, highlighting their ability to effectively handle subtle variations in speech signals.

## VI Conclusion

In this work, we propose Nested Res2Net (Nes2Net) and its enhanced variant, Nes2Net-X, as lightweight and dimensionality reduction (DR) layer-free back-end architectures designed for speech anti-spoofing in the foundation model era.

Unlike conventional approaches that rely on a DR layer to bridge the mismatch between high-dimensional features and downstream classifiers, our proposed architectures directly process these rich representations. This not only eliminates the computational and parameter burden introduced by DR layers but also avoids information loss, enhancing overall system efficiency and robustness.

Nes2Net incorporates a novel nested multi-scale design that enables more effective feature extraction and deeper cross-channel interactions without increasing model complexity. The improved Nes2Net-X further strengthens representation learning by introducing learnable weighted feature fusion, offering adaptive control over the feature aggregation process.

We conduct extensive evaluations across five representative datasets—CtrSVDD, ASVspoof 2021, ASVspoof 5, PartialSpoof, and In-the-Wild—covering a wide range of singing voice deepfakes, fully spoofed speech, adversarial attacks, real-world deepfakes, and partially spoofed speech. Across all scenarios, our models achieve SOTA performance, demonstrating superior generalization, compactness, and resilience under unseen and challenging conditions.

In summary, Nes2Net and Nes2Net-X offer a general-purpose, resource-efficient back-end for foundation model-based speech anti-spoofing, providing a practical yet powerful alternative to DR-dependent designs. To support future research and application, we make all source code and pre-trained models publicly available.

---
_Part of [audio-deepfake-detection-papers](https://github.com/woongja/audio-deepfake-detection-papers) · summary auto-generated by a local LLM, unverified._
