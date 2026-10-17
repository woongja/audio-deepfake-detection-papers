# Audio Deepfake Detection Papers

![papers](https://img.shields.io/badge/papers-1386-blue) ![updated](https://img.shields.io/badge/updated-2026--10--18-green)

A curated list of audio deepfake detection (anti-spoofing) papers,
organized by topic and year, with venues, citation counts, and arXiv links.
Generated from a personally maintained research corpus.

## Topics

- [SSL Front-Ends (wav2vec2 / WavLM / HuBERT)](topics/ssl-models.md) (211)
- [Spectral & Signal-Processing Front-Ends](topics/spectral-frontends.md) (499)
- [Detection Architectures & Encoders](topics/architectures.md) (177)
- [Adapters, LoRA & MoE](topics/adapters-lora-moe.md) (30)
- [LLM-Based Detection](topics/llm-based.md) (23)
- [Explainability & Attribution](topics/xai-explainability.md) (97)
- [Noise & Real-World Robustness](topics/noise-robustness.md) (119)
- [Generalization & OOD](topics/generalization-ood.md) (368)
- [Neural Codec Deepfakes](topics/codec-deepfake.md) (55)
- [Temporal Localization & Partial Spoof](topics/temporal-localization.md) (74)
- [Datasets & Corpora](topics/datasets.md) (106)
- [Data Augmentation & Curation](topics/data-augmentation.md) (91)
- [Evaluation, Metrics & Benchmarks](topics/evaluation-benchmarks.md) (103)
- [Speech Synthesis & Conversion (Attack Side)](topics/synthesis-attack-side.md) (3)
- [Surveys & Reviews](topics/surveys.md) (35)
- [Training Objectives & Losses](topics/training-objectives.md) (142)
- [Continual & Federated Learning](topics/continual-federated.md) (16)
- [Adversarial Attacks & Robustness Testing](topics/adversarial.md) (24)
- [Challenge Systems & Fusion](topics/systems-fusion.md) (47)
- [Transfer & Domain Adaptation](topics/transfer-adaptation.md) (49)
- [Cross-Domain & Multimodal](topics/cross-domain-multimodal.md) (74)

## Latest 30 Papers

_Date = arXiv submission date (falls back to YYYY-MM if unavailable)._

| Date | Title | First Author | Summary | Citations |
|---|---|---|---|---|
| 2026-10-13 | [An Initial Study of Physiological Markers for Deepfake Speech Detection](https://arxiv.org/abs/2610.18934) | Vojtěch Staněk et al. | [📝](summaries/an-initial-study-of-physiological-markers-for-deepfake-speech-detection.md) |  |
| 2026-10-13 | [Physics-Aware Deepfake Detection via Distance–Speech Consistency](https://arxiv.org/abs/2610.18485) | > **제출일:** 2026-10-13 | [📝](summaries/physics-aware-deepfake-detection-via-distancespeech-consistency.md) |  |
| 2026-10-13 | [What Do Deepfake Audio Detectors Hear? From Self-Supervised Models to Audio LLMs](https://arxiv.org/abs/2610.17617) | Wanying Ge et al. | [📝](summaries/what-do-deepfake-audio-detectors-hear-from-self-supervised-models-to-audio-llms.md) |  |
| 2026-10-12 | [Unsupervised Data Drift Monitoring for Deployed Deepfake Speech Detectors](https://arxiv.org/abs/2610.16826) | Lukáš Prokeš et al. | [📝](summaries/unsupervised-data-drift-monitoring-for-deployed-deepfake-speech-detectors.md) |  |
| 2026-10-12 | [QBFF: Deep Quantum Bottleneck for Automatic Speaker Verification Anti-Spoofing](https://arxiv.org/abs/2610.16390) | > **제출일:** 2026-10-12 | [📝](summaries/qbff-deep-quantum-bottleneck-for-automatic-speaker-verification-anti-spoofing.md) |  |
| 2026-10-12 | [Adaptive Compression and Targeted Perturbation: A Unified Framework for Generalized Audio Deepfake Detection](https://arxiv.org/abs/2610.16049) | Jianqiao Cui et al. | [📝](summaries/adaptive-compression-and-targeted-perturbation-a-unified-framework-for-generaliz.md) |  |
| 2026-10-07 | [Detection-Guided Adaptive Purification with Diffusion Models for Robust Audio Deepfake Detection](https://arxiv.org/abs/2610.10752) | Muhammed Salih Kayhan et al. | [📝](summaries/detection-guided-adaptive-purification-with-diffusion-models-for-robust-audio-de.md) |  |
| 2026-10-07 | [DuRe-ST: Dual-Relation Spectro-Temporal Modeling for Speech Deepfake Detection](https://arxiv.org/abs/2610.10121) | Shaole Li et al. | [📝](summaries/dure-st-dual-relation-spectro-temporal-modeling-for-speech-deepfake-detection.md) |  |
| 2026-10-07 | [Source-Directed Trajectory Perturbation at First-Order Cost for Domain Generalization in Speech Deepfake Detection](https://arxiv.org/abs/2610.10094) | Siqing Qin et al. | [📝](summaries/source-directed-trajectory-perturbation-at-first-order-cost-for-domain-generaliz.md) |  |
| 2026-10-05 | [Exposing and Mitigating Neural Codec Vulnerabilities in Audio Deepfake Detection](https://arxiv.org/abs/2610.07216) | Abdullah et al. | [📝](summaries/exposing-and-mitigating-neural-codec-vulnerabilities-in-audio-deepfake-detection.md) |  |
| 2026-10-04 | [Task-Aware Joint Pruning and Distillation for Efficient Audio Deepfake Detection](https://arxiv.org/abs/2610.05264) | Miao He et al. | [📝](summaries/task-aware-joint-pruning-and-distillation-for-efficient-audio-deepfake-detection.md) |  |
| 2026-10-03 | [Temporal Anchors and Editing Sensitivity in Partial Speech Spoofing: A Controlled Study](https://arxiv.org/abs/2610.04479) | Xiaosu Su et al. | [📝](summaries/temporal-anchors-and-editing-sensitivity-in-partial-speech-spoofing-a-controlled.md) |  |
| 2026-10-01 | [A Federated Deepfake Speech Detection Method Based on Layer-Wise Center-Guided Weighting Aggregation](https://arxiv.org/abs/2610.01259) | Yingjian Yu et al. | [📝](summaries/a-federated-deepfake-speech-detection-method-based-on-layer-wise-center-guided-w.md) |  |
| 2026-10-01 | [FedCFM: Federated Continual Domain Generalization for Fake Speech Detection via Conditional Flow Matching](https://arxiv.org/abs/2610.01242) | Yingjian Yu et al. | [📝](summaries/fedcfm-federated-continual-domain-generalization-for-fake-speech-detection-via-c.md) |  |
| 2026-09-30 | [On Evaluating Quantum Kernel Robustness for Low-Resource Cross-Corpus Audio Deepfake Detection](https://arxiv.org/abs/2610.00649) | Lisan Al Amin et al. | [📝](summaries/on-evaluating-quantum-kernel-robustness-for-low-resource-cross-corpus-audio-deep.md) |  |
| 2026-09-30 | [Collapse, Not Invariance: Diagnosing Auxiliary Objectives in Speech Anti-Spoofing](https://arxiv.org/abs/2610.00539) | Ksenia Lysikova et al. | [📝](summaries/collapse-not-invariance-diagnosing-auxiliary-objectives-in-speech-anti-spoofing.md) |  |
| 2026-09-30 | [SEAR: Spoofing Evidence-Grounded Audio Reasoning Benchmark for Audio Language Models](https://arxiv.org/abs/2609.39847) | Rong Wan et al. | [📝](summaries/sear-spoofing-evidence-grounded-audio-reasoning-benchmark-for-audio-language-mod.md) |  |
| 2026-09-30 | [SE-ADD: Self-Evolving Audio Deepfake Detection with Mistake-Driven Supervision](https://arxiv.org/abs/2609.39679) | Rong Wan et al. | [📝](summaries/se-add-self-evolving-audio-deepfake-detection-with-mistake-driven-supervision.md) |  |
| 2026-09-30 | [Neural Audio Codec for Robust Audio Deepfake Detection](https://arxiv.org/abs/2609.39651) | Jungwoo Kim et al. | [📝](summaries/neural-audio-codec-for-robust-audio-deepfake-detection.md) |  |
| 2026-09-29 | [Learning as Deepfakes Evolve: RF-Prompt for Continual Audio Deepfake Detection](https://arxiv.org/abs/2609.37586) | Yuankun Xie et al. | [📝](summaries/learning-as-deepfakes-evolve-rf-prompt-for-continual-audio-deepfake-detection.md) |  |
| 2026-09-28 | [GLAD: Global-Local Adaptive Detector for Robust Speech Deepfake Detection](https://arxiv.org/abs/2609.35411) | Zelin Zhao et al. | [📝](summaries/glad-global-local-adaptive-detector-for-robust-speech-deepfake-detection.md) |  |
| 2026-09-27 | [Domain-Adaptive Dual-Gating Mixture of Experts for Generalizable Speech Deepfake Detection](https://arxiv.org/abs/2609.33709) | Siqing Qin et al. | [📝](summaries/domain-adaptive-dual-gating-mixture-of-experts-for-generalizable-speech-deepfake.md) |  |
| 2026-09-27 | [DGS-MLDG: Domain Gradient Surgery Guided Meta-Learning for Domain Generalization in Speech Deepfake Detection](https://arxiv.org/abs/2609.33706) | Siqing Qin et al. | [📝](summaries/dgs-mldg-domain-gradient-surgery-guided-meta-learning-for-domain-generalization.md) |  |
| 2026-09-27 | [What Survives the Codec Shift: Pooled No-Vocals Residuals for Speech Deepfake Detection](https://arxiv.org/abs/2609.33375) | Jiajun Xu et al. | [📝](summaries/what-survives-the-codec-shift-pooled-no-vocals-residuals-for-speech-deepfake-det.md) |  |
| 2026-09-25 | [Tracing and Relearning Detection Evidence in Text-to-Speech Systems](https://arxiv.org/abs/2609.30983) | Eunji Shin et al. | [📝](summaries/tracing-and-relearning-detection-evidence-in-text-to-speech-systems.md) |  |
| 2026-09-24 | [VIETPRISM: A Large-Scale Vietnamese Speech and Deepfake Corpus with Diverse Dialects and Code-Switching](https://arxiv.org/abs/2609.30005) | > **제출일:** 2026-09-24 | [📝](summaries/vietprism-a-large-scale-vietnamese-speech-and-deepfake-corpus-with-diverse-diale.md) |  |
| 2026-09-24 | [Is Broader Better? A Controlled Study of Multilingual Coverage and Pretraining Objective in Frozen SSL Encoders for Speech Deepfake Detection](https://arxiv.org/abs/2609.29138) | > **제출일:** 2026-09-24 | [📝](summaries/is-broader-better-a-controlled-study-of-multilingual-coverage-and-pretraining-ob.md) |  |
| 2026-09-23 | [Spooftral: Can Voxtral Audio-Language Model Detect Speech Spoofing?](https://arxiv.org/abs/2609.28713) | > **제출일:** 2026-09-23 | [📝](summaries/spooftral-can-voxtral-audio-language-model-detect-speech-spoofing.md) |  |
| 2026-09-22 | [Boundary and Intra-Segment Learning for Partial Audio Deepfake Localization](https://arxiv.org/abs/2609.25822) | > **제출일:** 2026-09-22 | [📝](summaries/boundary-and-intra-segment-learning-for-partial-audio-deepfake-localization.md) |  |
| 2026-09-21 | [SPADE: A Multilingual Dataset for Speech Partial Deepfake Detection and Localization](https://arxiv.org/abs/2609.25197) | > **제출일:** 2026-09-21 | [📝](summaries/spade-a-multilingual-dataset-for-speech-partial-deepfake-detection-and-localizat.md) |  |

## Papers per Year

| Year | Papers |
|---|---|
| 2026 | 237 |
| 2025 | 305 |
| 2024 | 219 |
| 2023 | 149 |
| 2022 | 118 |
| 2021 | 85 |
| 2020 | 70 |
| 2019 | 70 |
| 2018 | 43 |
| 2017 | 38 |
| 2016 | 18 |
| 2015 | 23 |
| 2014 | 5 |
| 2013 | 4 |
| 2012 | 2 |

## About

Citation counts come from Semantic Scholar at collection time and lag reality.
Metadata is collected automatically and spot-checked, not exhaustively verified.
Some papers link to a per-paper summary page (📝). Those summaries are **auto-generated by a local LLM in Korean and are not verified** — always check the original paper.
Contributions and corrections are welcome via issues.

License: [CC0 1.0](LICENSE)
