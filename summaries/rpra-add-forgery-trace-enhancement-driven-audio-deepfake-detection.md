# RPRA-ADD: Forgery Trace Enhancement-Driven Audio Deepfake Detection

> ⚠ AI-generated summary (local LLM, **Korean**, unverified) — auto-generated from the paper, not fact-checked. Verify against the source.

**arXiv:** https://arxiv.org/abs/2506.00375 · Ruibo Fu et al. · 2025

## 한 줄 요약

본 논문에서는 위장 흔적 인식 강화, 특징 공간 차이 증대, 위장 흔적 집중 주의 메커니즘을 포함하는 RPRA-ADD 프레임워크를 제안하며, 다양한 오디오 도메인에서 우수한 디페이크 감지 성능을 입증합니다.

## 문제 정의

오디오 디페이크 기술의 발전으로 인해 오디오 디페이크 감지(ADD)는 중요한 연구 과제로 부상했습니다. 기존 ADD 방법들은 학습 데이터 분포에 크게 의존하며, 위조 패턴의 변화나 다양한 오디오 유형(스피치, 사운드, 노래 등)에 대한 일반화 능력이 부족한 한계를 가지고 있습니다. 또한, 실제와 위조 오디오 간의 본질적인 특징 차이를 효과적으로 포착하지 못하거나, 위장 흔적에 대한 집중도가 낮은 문제점이 존재합니다.

## 제안 방법

본 논문에서는 이러한 문제점을 해결하기 위해 RPRA-ADD(Reco**c**nstruction-Perception-Reinforcement-Attention) 프레임워크를 제안합니다. 이 프레임워크는 위장 흔적 인식 능력 강화를 위한 Global-Local Foigery Perception (GFLP) 모듈, 실제와 위조 오디오 간의 특징 공간 차이 증대를 위한 Multi-stage Dispersed Enhancement Loss (MDEL), 그리고 위장 흔적에 대한 주의 집중을 강화하기 위한 Fake Trace Focused Attention (FFTA) 메커니즘으로 구성됩니다.

## 실험·결과

본 연구진은 RPRA-ADD의 성능을 검증하기 위해 AVSpoof 2019, AVSpoof 2021, CodecFake, FakeSound 등 다양한 벤치마크 데이터셋에서 실험을 수행했습니다. 실험 결과, RPRA-ADD는 기존의 SOTA 모델 대비 20% 이상의 성능 향상을 보였으며, 특히 FakeSound 데이터셋에서 우수한 성능을 나타냈습니다. 또한, 스피치, 사운드, 노래 등 다양한 오디오 도메인에 걸쳐 Cross-domain 평가에서도 일관되게 최상의 성능을 달성했습니다.

## 한계

본 연구에서 제안된 RPRA-ADD 프레임워크는 다양한 오디오 도메인에서 우수한 성능을 보였지만, 여전히 새로운 형태의 위조 기술이나 극단적인 노이즈 환경에서는 성능 저하가 발생할 수 있습니다. 또한, 모델의 복잡성으로 인해 계산 비용이 증가할 수 있으며, 실제 환경에서의 실시간 적용을 위해서는 추가적인 최적화 작업이 필요할 수 있습니다.

## I Introduction

In recent years, with the rapid development of deepfake technology, deeplake audio has become increasingly realistic and harder to distinguish. Deeplake audio technology brings serious challenges to industries like entertainment and news. It has also been misused for fraud, misinformation, and other harmful activities, posing a serious threat to public safety. As a result, audio deeplake detection (ADD) has become an urgent research topic. However, despite the progress achieved by existing ADD methods, generalization remains a significant challenge—both within the same audio type (e.g., across different speech datasets) and across different types of audio, such as sound and singing. Existing studies show that the effectiveness of features directly determines the detection capability, , . The feature module serves as the foundation of ADD systems, as it captures subtle artifacts introduced by audio forgeries and enables the learning of discriminative representations for reliable detection .
Early efforts focusing on feature design in ADD can be broadly divided into two main categories: (1) Handcrafted Spectral Feature-Based Methods: Traditional approaches often leverage domain knowledge to design acoustic features such as Mel-Frequency Cepstral Coefficients (MFCCs), Linear Frequency Cepstral Coefficients (LFCCs), and Constant-Q Transform (CQT) features , , , , , , , , , , , , , . These features are derived from time-frequency representations of audio signals and offer advantages in computational efficiency and interpretability. However, they rely on manually designed feature selection, and these features are typically designed for specific audio types, making them difficult to adapt to diverse audio content and new forgery techniques cite LFCC-LCNN. (2) Sync-Based Temporal Feature Methods: Recent advancements have introduced deep learning models that extract features directly from raw audio waveforms using SyncNet-based architectures. Models such as AASIST, RawNet2, and RawGAT-ST , , , , employ parameterized sync functions to learn band-pass filters, enabling the capture of discriminative patterns from temporal and spectral cues inherent in audio signals. While these methods provide strong modeling capabilities, they often overfit to specific forgery patterns seen during training, which limits their generalization to unseen attacks. When faced with new forgery patterns outside the training set, both handcrafted and learnable features tend to rely too heavily on surface-level statistical cues, without establishing robust reference points grounded in the intrinsic properties of genuine audio.
To address these limitations, recent advancements in self-supervised learning (SSL), exemplified by models such as Wav2vec and WavLM, , , , , , , , , , , , , , have shown promise by learning universal audio representations through large-scale unsupervised pre-training. Unlike traditional handcrafted or task-specific learnable features, SSL-based representations are trained on vast amounts of unlabeled audio data, allowing them to capture general and transferable acoustic patterns. These representations can then be fine-tuned for downstream tasks, . However, despite their strong representational capacity, existing SSL models are primarily optimized for speech recognition or speaker identification. As a result, their effectiveness in detecting subtle artifacts introduced by audio generation techniques remains limited. Furthermore, directly applying SSL models without adaptation may still lead to suboptimal performance when facing highly dynamic or cross-domain forgery scenarios. This motivates the need to further explore how to enhance the task-awareness and artifact sensitivity of SSL representations in the context of ADD.
In this paper, we propose the RPRA-ADD, an integrated Reconstruction-Perception-Reinforcement-Attention networks based forgery trace enhancement-driven robust audio deepfake detection framework. To enhance the ability to perceive forgery traces, we propose the Global-Local Forgery Perception (GFLP) module. This module extracts global spectral forgery traces through intra-band and inter-band attention and captures local time-frequency features using depthwise separable convolutions, ultimately dynamically merging dual-stream characteristics via a gating mechanism, enabling the capture of subtle forgery traces.
To enhance our method’s ability to distinguish the inherent feature differences between real and fake audio, and achieve further feature disentanglement, we design the Multi-stage Dispersed Enhancement Loss (MDEL). In the decoder, MDEL applies a contrastive dispersal strategy to features at different levels, expanding the distribution difference between real and fake audio. Furthermore, to strengthen this approach’s focus on forgery traces, we propose the Fake Trace Focused Attention (FFTA) mechanism, which generates attention weights through reconstruction discrepancy matrices, enhancing the detection of forgery traces. We achieve State-of-the-Art (SOTA) performance on several benchmark datasets, including AVSpoof 2019, AVSpoof 2021, CodecFake, and FakeSound, achieving over 20% performance improvement. Furthermore, our method also attains SOTA results in rigorous 3×3 cross-domain experiments across Speech, Sound, and Singing, demonstrating strong generalization capability across diverse audio domains.

## I-B Experimental Setup

In our experiments, we primarily use EER as the evaluation metric. For the AVSpoof 2019 dataset, we additionally report the minimum normalized tandem detection cost function (min t-DCF), aligning with other baseline methods. The min t-DCF evaluates the performance of a tandem system consisting of the proposed ADD model and a specific AVS system. For both EER and min t-DCF, lower values indicate better detection performance. In the experiments on the FakeSound dataset, we follow the original protocol and adopt Accuracy (ACC) as the evaluation metric. For cross-domain scenarios, we employ EER to provide a more comprehensive assessment.

## V Experimental Results



## V-A In-domain ADD Evaluations

We conducted training and testing on the 19LA speech dataset, with the F1 score as the evaluation metric, as shown in Table [V]. FakeSound includes three test sets: Easy, Hard, and Zero-shot, with increasing difficulty. The human-annotated F1 scores generally range from 0.5 to 0.6, demonstrating that this is a challenging task. We compared the baseline models in the dataset, including wavLM and EAT. Our method achieved SOTA performance on all three test sets, demonstrating the robustness of our approach in the sound domain.
We trained and tested our proposed method on the SingFake singing voice dataset and compared its performance with methods from the SVDD challenge. Some of these methods leveraged additional data, ensemble systems, and data augmentation techniques, while others did not explicitly mention the training strategies used in the SVDD challenge, which we denote as ”NA” in the table. In contrast, our method relies solely on a single system, without using data augmentation or additional data, yet still achieved competitive results: SOTA performance on A10 and A13 forgery techniques, and near-optimal performance on A09.

## V-B Cross-domain ADD Evaluations

For the CodecFake A3 evaluation, as shown in Table [VI]. We regard it as a highly challenging task. Similar to CodecFake, we utilized the 19LA speech dataset for training without incorporating sound data or applying any data augmentation techniques. Although our method achieved the lowest EER at 29.9%, the relatively high value can be attributed to the substantial domain differences between speech and sound. The distribution of speech data is relatively homogeneous, primarily comprising human vocal recordings captured under specific acoustic conditions. In contrast, sound data presents a much more diverse distribution, including natural sounds, mechanical noises, and music. While real sound data is included in the pre-training dataset, the absence of forged sound data during the training phase limits the model’s ability to adapt to such cases. Consequently, the model faces difficulties in generalizing to the broad variability inherent in sound data, resulting in suboptimal performance.
Notably, XLSR-AASIST demonstrates superior performance when trained on singing or environmental sound data and tested on speech. This can likely be attributed to the strong pre-trained speech representations embedded in the XLSR model, which provide a significant advantage in handling speech-related tasks. Nevertheless, despite this specific strength, RPRA-ADD maintains consistent superiority across most in-domain and cross-domain scenarios, as well as in key average performance metrics, thereby demonstrating its overall robustness and superior generalization capability.

## VI Conclusion

In conclusion, we have proposed a novel RPRA-ADD framework for robust audio deepfake detection. Extensive experiments on various datasets and cross-domain evaluations demonstrate that our method consistently achieves state-of-the-art performance, outperforming existing approaches in terms of accuracy and generalization ability. The proposed framework effectively addresses the challenges posed by diverse audio domains and evolving forgery techniques, making it a promising solution for real-world audio security applications.

---
_Part of [audio-deepfake-detection-papers](https://github.com/woongja/audio-deepfake-detection-papers) · summary auto-generated by a local LLM, unverified._
