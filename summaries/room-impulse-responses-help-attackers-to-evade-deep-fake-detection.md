# Room Impulse Responses Help Attackers to Evade Deep Fake Detection

> ⚠ AI-generated summary (local LLM, **Korean**, unverified) — auto-generated from the paper, not fact-checked. Verify against the source.

**arXiv:** https://arxiv.org/abs/2409.14712 · Hieu-Thi Luong et al. · 2024

## 한 줄 요약

본 연구는 조작된 음성 탐지 시스템의 취약점을 RIR을 활용한 공격으로 분석하고, 합성 RIR 데이터셋을 활용한 학습을 통해 탐지 시스템의 견고성을 향상시키는 방법을 제시합니다.

## 문제 정의

기존의 조작된 음성 탐지 시스템은 특정 유형의 조작 기법에 대해 높은 정확도를 보이지만, 실제 환경에서는 다양한 RIR의 영향을 받을 수 있어 취약합니다. 특히, 공격자는 RIR을 활용하여 조작된 음성을 더욱 현실적으로 만들어 탐지 시스템을 우회할 수 있습니다.

## 제안 방법

본 연구에서는 실제 RIR 데이터셋과 시뮬레이션된 RIR 데이터셋을 활용하여 다양한 특성을 가진 합성 RIR 데이터셋을 생성하는 방법을 제안합니다. 생성된 합성 RIR 데이터셋을 기존 학습 데이터에 추가하여 조작된 음성 탐지 모델을 학습시키는 방법을 통해 모델의 일반화 성능과 견고성을 향상시킵니다.

## 실험·결과

실험에서는 다양한 조작된 음성 데이터셋과 여러 조작된 음성 탐지 모델에 대해 RIR 추가 공격의 효과를 평가했습니다. 실험 결과, RIR을 추가한 조작된 음성은 기존 SOTA 시스템의 EER을 크게 증가시켰으며, 합성 RIR 데이터셋으로 학습된 모델은 이러한 공격에 대해 더 높은 견고성을 보였습니다. 특히, BR2 모델은 다양한 평가 세트에서 뛰어난 성능을 보이며, 기존 최고 성능 모델 대비 EER을 크게 감소시켰습니다.

## 한계

본 연구는 합성 RIR 데이터셋을 활용한 학습이 효과적임을 보였지만, 실제 환경의 다양한 RIR 특성을 모두 포괄하지 못할 수 있다는 한계가 있습니다. 또한, 합성 RIR 데이터셋 생성 과정에서 특정 RIR 특성에 편향될 가능성이 있으며, 이는 모델의 일반화 성능에 영향을 미칠 수 있습니다.

## 4 Experiments



## 4.4 Results

Table 1 presents the EERs of all detection systems on the evaluation sets. The first three rows display the results of the baselines, revealing System B outperforms System C on C1, but this trend is reversed in the pooled results. As anticipated, the EERs increase substantially when the systems are tested on reverberant fake speech, specifically with C1R1, which shows a significant improvement in bypassing detection systems, yielding a relative EER increase of 70.94% for System B and 112.23% for System C.

Overall, simply replacing fake samples with their reverberant counterparts can enhance the success rate of evading detection systems, effectively doubling it, with the use of recorded RIRs having a more profound impact than synthetic ones (12.71% higher in the case of System B). This suggests that recorded RIRs can create more realistic reverberant conditions, leading to a greater challenge for detection systems.

The subsequent three rows present the EERs of systems trained with recorded RIRs, revealing varying outcomes. Notably, the augmentation proves beneficial for AR1 and CR1, consistently improving their performance across all evaluation sets, but it appears to degrade the performance of BR1. One possible explanation is that BR1 was overfitted to a limited set of RIRs, leading to increased EER. Meanwhile, CR1 consistently outperforms System C across all evaluation sets, not just those with reverberant conditions, suggesting a more robust performance improvement.

This result indicates that RIR augmentation can be beneficial for training robust detection systems, but its effectiveness is contingent on a diverse set of RIRs, as limited RIRs can lead to overfitting and diminished performance.

The systems trained with either synthetic or simulated RIRs also yield varying results, but generally demonstrate beneficial performance improvements in most cases. Notably, BR2 achieves a SOTA performance across all evaluation sets, surpassing the previous best results. Specifically, BR2’s EER is 17.44% lower than System C’s on the pooled result, and it attains the lowest EERs on reverberant fake speech among all evaluated systems, demonstrating exceptional performance in this challenging condition.

The differences between systems trained with synthetic and simulated RIRs are negligible, with only a few exceptions. Overall, both synthetic and simulated RIRs enhance system performance, with a slight advantage observed for synthetic RIRs. This suggests that while both approaches are beneficial, synthetic RIRs may offer a marginally better improvement.

We conclude that leveraging a large-scale synthetic or simulated RIR dataset for augmentation can significantly enhance the robustness and resilience of fake speech detection systems, mitigating the need for extensive real-world RIR collections. Notably, BR2, trained with the large-scale synthetic RIRs, achieves outstanding performance, yielding the best results across all evaluation sets.

## 5 Discussion

(a) RawNet2
(b) Wav2Vec2 + AASIST
(c) Wav2Vec2 + Conformer

Figure 4: FAR (%) of the systems trained with recorded RIRs (top row), synthetic RIRs (middle row), and simulated RIRs (bottom row) at the EER threshold test on the C1R2 set, results are split by T60 and DRR values of augmented RIRs.

## 6 Conclusion

In this paper, we explored the potential of using RIRs to evade automatic fake speech detection systems. Our findings revealed that RIRs can significantly degrade the performance of SOTA models, doubling their EER. Although large-scale RIR datasets can enhance model robustness, their scarcity makes synthetic RIRs an attractive alternative, providing a cost-effective and scalable means of obtaining high-quality training data. Our experiments demonstrated that augmenting with synthetic RIRs significantly enhances model generalization. Notably, our top-performing system achieved substantial EER reductions: from 2.58% to 2.13% on the DF task and from 4.00% to 2.53% on the reverberant fake speech task. This approach is model-agnostic, making it versatile and widely applicable. Furthermore, our experiments suggest that while a large-scale simulated RIR dataset can be beneficial, a synthetic RIR dataset yields even better results. For deep fake detection, robustness is more crucial than benchmark EER, as it must detect new synthesized speech types and evolving audio manipulations.

---
_Part of [audio-deepfake-detection-papers](https://github.com/woongja/audio-deepfake-detection-papers) · summary auto-generated by a local LLM, unverified._
