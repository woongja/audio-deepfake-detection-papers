# Audio Deepfake Detection Papers

![papers](https://img.shields.io/badge/papers-1420-blue) ![updated](https://img.shields.io/badge/updated-2026--11--26-green)

A curated list of audio deepfake detection (anti-spoofing) papers,
organized by topic and year, with venues, citation counts, and arXiv links.
Generated from a personally maintained research corpus.

## Topics

- [SSL Front-Ends (wav2vec2 / WavLM / HuBERT)](topics/ssl-models.md) (252)
- [Spectral & Signal-Processing Front-Ends](topics/spectral-frontends.md) (616)
- [Detection Architectures & Encoders](topics/architectures.md) (259)
- [Adapters, LoRA & MoE](topics/adapters-lora-moe.md) (31)
- [LLM-Based Detection](topics/llm-based.md) (27)
- [Explainability & Attribution](topics/xai-explainability.md) (121)
- [Noise & Real-World Robustness](topics/noise-robustness.md) (145)
- [Generalization & OOD](topics/generalization-ood.md) (496)
- [Neural Codec Deepfakes](topics/codec-deepfake.md) (85)
- [Temporal Localization & Partial Spoof](topics/temporal-localization.md) (85)
- [Datasets & Corpora](topics/datasets.md) (145)
- [Data Augmentation & Curation](topics/data-augmentation.md) (124)
- [Evaluation, Metrics & Benchmarks](topics/evaluation-benchmarks.md) (157)
- [Speech Synthesis & Conversion (Attack Side)](topics/synthesis-attack-side.md) (11)
- [Surveys & Reviews](topics/surveys.md) (37)
- [Training Objectives & Losses](topics/training-objectives.md) (200)
- [Continual & Federated Learning](topics/continual-federated.md) (18)
- [Adversarial Attacks & Robustness Testing](topics/adversarial.md) (43)
- [Challenge Systems & Fusion](topics/systems-fusion.md) (134)
- [Transfer & Domain Adaptation](topics/transfer-adaptation.md) (67)
- [Cross-Domain & Multimodal](topics/cross-domain-multimodal.md) (88)

## Latest 30 Papers

_Date = arXiv submission date (falls back to YYYY-MM if unavailable)._

| Date | Title | First Author | Summary | Citations |
|---|---|---|---|---|
| 2026-11-24 | [File Size as a Potential Dataset Bias in Audio-Visual Deepfake Data](https://arxiv.org/abs/2611.32979) | > **제출일:** 2026-11-24 | [📝](summaries/file-size-as-a-potential-dataset-bias-in-audio-visual-deepfake-data.md) |  |
| 2026-11-24 | [Perfect Scores, Misplaced Explanations: A Controlled Study of Explainability in Audio Deepfake Detection](https://arxiv.org/abs/2611.32593) | David Combei et al. | [📝](summaries/perfect-scores-misplaced-explanations-a-controlled-study-of-explainability-in-au.md) |  |
| 2026-11-24 | [Do Layer Rankings Survive Silence Trimming? The Silence Shortcut in Frozen WavLM Representations for Audio Deepfake Detection](https://arxiv.org/abs/2611.32457) | Nur Elabid et al. | [📝](summaries/do-layer-rankings-survive-silence-trimming-the-silence-shortcut-in-frozen-wavlm.md) |  |
| 2026-11-23 | [Ultrasound Watermark: Real-time Acoustic Watermarking against Voice Scams on Smartphones](https://arxiv.org/abs/2611.30106) | Renzhi Hao et al. | [📝](summaries/ultrasound-watermark-real-time-acoustic-watermarking-against-voice-scams-on-smar.md) |  |
| 2026-11-23 | [Which Layer to Trust? Layer Selection in Frozen Speech Encoders for Singing-Voice Deepfake Detection under Signal Corruption](https://arxiv.org/abs/2611.29871) | Benjamin Hurt et al. | [📝](summaries/which-layer-to-trust-layer-selection-in-frozen-speech-encoders-for-singing-voice.md) |  |
| 2026-11-23 | [Characterizing Frozen SSL Encoders and Backends for Cross-Domain Speech Deepfake Detection](https://arxiv.org/abs/2611.29865) | Benjamin Hurt et al. | [📝](summaries/characterizing-frozen-ssl-encoders-and-backends-for-cross-domain-speech-deepfake.md) |  |
| 2026-11-22 | [SWIFT: A Handcrafted, Arithmetic-Minimal FPGA Engine for Real-Time Audio Deepfake Detection](https://arxiv.org/abs/2611.29315) | Chirantan Banerjee et al. | [📝](summaries/swift-a-handcrafted-arithmetic-minimal-fpga-engine-for-real-time-audio-deepfake.md) |  |
| 2026-11-21 | [MOZAIC: An Audio-Video Deepfake Benchmark for Telling What Is Fake](https://arxiv.org/abs/2611.31301) | > **제출일:** 2026-11-21 | [📝](summaries/mozaic-an-audio-video-deepfake-benchmark-for-telling-what-is-fake.md) |  |
| 2026-11-21 | [Spoof Localization as Boundary Regression](https://arxiv.org/abs/2611.29085) | Yixuan Xiao et al. | [📝](summaries/spoof-localization-as-boundary-regression.md) |  |
| 2026-11-21 | [Training Speech Deepfake Detectors against Worst-Case Filters: Gains, Costs and Limits](https://arxiv.org/abs/2611.28718) | Ali Alavi | [📝](summaries/training-speech-deepfake-detectors-against-worst-case-filters-gains-costs-and-li.md) |  |
| 2026-11-20 | [Benchmarking Neural Defend ARCAS 290M: A Foundation Model for AI-Generated Audio Detection](https://arxiv.org/abs/2611.27784) | Sivashankar Selvarajan et al. | [📝](summaries/benchmarking-neural-defend-arcas-290m-a-foundation-model-for-ai-generated-audio.md) |  |
| 2026-11-20 | [Neural Defend ARCAS Ranks #1 in Global Audio Deepfake Detection – ARCAS on the Podonos Independent Leaderboard](https://arxiv.org/abs/2611.27215) | Sivashankar Selvarajan et al. | [📝](summaries/neural-defend-arcas-ranks-1-in-global-audio-deepfake-detection-arcas-on-the-podo.md) |  |
| 2026-11-19 | [Towards Robust Partial-Edit Deepfake Localization: An Edit- and Generator-Conditioned Analysis](https://arxiv.org/abs/2611.26903) | > **제출일:** 2026-11-19 | [📝](summaries/towards-robust-partial-edit-deepfake-localization-an-edit-and-generator-conditio.md) |  |
| 2026-11-17 | [Robust DOA Estimation for GNSS-like Signals Under Jamming: A Rotation-Enhanced SWN-MUSIC Approach](https://arxiv.org/abs/2611.22574) | > **제출일:** 2026-11-17 | [📝](summaries/robust-doa-estimation-for-gnss-like-signals-under-jamming-a-rotation-enhanced-sw.md) |  |
| 2026-11-16 | [Progressive Layer-wise Supervision: Deep-to-Shallow Supervision Annealing for Efficient and Robust Speech Deepfake Detection](https://arxiv.org/abs/2611.20630) | Hoan My Tran et al. | [📝](summaries/progressive-layer-wise-supervision-deep-to-shallow-supervision-annealing-for-eff.md) |  |
| 2026-11-09 | [Which Acoustic Features Survive Compression? Tracker-Estimated First-Formant Statistics for Codec-Robust Audio Deepfake Detection](https://arxiv.org/abs/2611.13258) | Yash Sukhdeve et al. | [📝](summaries/which-acoustic-features-survive-compression-tracker-estimated-first-formant-stat.md) |  |
| 2026-11-09 | [MUTE: Multi-Level Alignment Uncoupling Against Talking-Head Exploitation for Voice Protection](https://arxiv.org/abs/2611.11989) | Donghyun Kim et al. | [📝](summaries/mute-multi-level-alignment-uncoupling-against-talking-head-exploitation-for-voic.md) |  |
| 2026-11-08 | [When Normality Shifts: Multi-Level WavLM Modeling for Open-World Audio Deepfake Detection](https://arxiv.org/abs/2611.11465) | Daniel Niekurzak et al. | [📝](summaries/when-normality-shifts-multi-level-wavlm-modeling-for-open-world-audio-deepfake-d.md) |  |
| 2026-11-05 | [Conflict-Aware Meta-Learning for Generalizable Speech Deepfake Detection](https://arxiv.org/abs/2611.08758) | > **제출일:** 2026-11-05 | [📝](summaries/conflict-aware-meta-learning-for-generalizable-speech-deepfake-detection.md) |  |
| 2026-11-05 | [LABBA: LLM-Assisted Behavioral Biometric Authentication](https://arxiv.org/abs/2611.08343) | > **제출일:** 2026-11-05 | [📝](summaries/labba-llm-assisted-behavioral-biometric-authentication.md) |  |
| 2026-11-04 | [GraphSeal: Graph-Augmented Speech Deepfake Detection via Temporal-Spectral Artifact Propagation](https://arxiv.org/abs/2611.06171) | Lee Seung-woo et al. | [📝](summaries/graphseal-graph-augmented-speech-deepfake-detection-via-temporal-spectral-artifa.md) |  |
| 2026-11-03 | [CLRM: Cross-Layer Relation Modeling for Audio Deepfake Detection](https://arxiv.org/abs/2611.05678) | Yangyang Qu et al. | [📝](summaries/clrm-cross-layer-relation-modeling-for-audio-deepfake-detection.md) |  |
| 2026-11-03 | [VeriSpoof: Beyond Real or Fake with One Audio LLM](https://arxiv.org/abs/2611.04634) | Yang Xiao et al. | [📝](summaries/verispoof-beyond-real-or-fake-with-one-audio-llm.md) |  |
| 2026-11-03 | [Detector-Guided Adversarial Vocoder Training for Text-to-Speech Synthesis](https://arxiv.org/abs/2611.04511) | Jiayan Cui et al. | [📝](summaries/detector-guided-adversarial-vocoder-training-for-text-to-speech-synthesis.md) |  |
| 2026-11-02 | [ReplayFactor: Replay-Aware Dual-Attribute Learning for Practical Speech Deepfake Detection](https://arxiv.org/abs/2611.02628) | Miao He et al. | [📝](summaries/replayfactor-replay-aware-dual-attribute-learning-for-practical-speech-deepfake.md) |  |
| 2026-10-31 | [Pop Goes the Verifier: Phoneme-Targeted Data Poisoning of Voice Liveness Detection](https://arxiv.org/abs/2611.01095) | Eshaq Jamdar et al. | [📝](summaries/pop-goes-the-verifier-phoneme-targeted-data-poisoning-of-voice-liveness-detectio.md) |  |
| 2026-10-25 | [ASR-Protected Fusion and Reference-Anchored Policy Optimization for Joint ASR and Word-Level Speech Anti-Spoofing](https://arxiv.org/abs/2610.34156) | Xueping Zhang et al. | [📝](summaries/asr-protected-fusion-and-reference-anchored-policy-optimization-for-joint-asr-an.md) |  |
| 2026-10-24 | [AV-FABLE: Audio-Visual Manipulation Forensics in Long-Form Videos](https://arxiv.org/abs/2610.33413) | > **제출일:** 2026-10-24 | [📝](summaries/av-fable-audio-visual-manipulation-forensics-in-long-form-videos.md) |  |
| 2026-10-20 | [Media Intelligence Platform: Multimodal Detection of Synthetic and Manipulated Content](https://arxiv.org/abs/2610.27974) | David Fischinger et al. | [📝](summaries/media-intelligence-platform-multimodal-detection-of-synthetic-and-manipulated-co.md) |  |
| 2026-10-20 | [RealComm: Benchmarking and Adapting Audio Deepfake Detection over Real Communication Channels](https://arxiv.org/abs/2610.27459) | Li Wang et al. | [📝](summaries/realcomm-benchmarking-and-adapting-audio-deepfake-detection-over-real-communicat.md) |  |

## Papers per Year

| Year | Papers |
|---|---|
| 2026 | 274 |
| 2025 | 304 |
| 2024 | 217 |
| 2023 | 146 |
| 2022 | 124 |
| 2021 | 82 |
| 2020 | 70 |
| 2019 | 70 |
| 2018 | 44 |
| 2017 | 38 |
| 2016 | 17 |
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
