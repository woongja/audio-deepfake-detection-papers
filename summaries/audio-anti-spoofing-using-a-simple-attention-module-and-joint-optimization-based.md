# Audio Anti-spoofing Using a Simple Attention Module and Joint Optimization Based on Additive Angular Margin Loss and Meta-learning

> Claude 분석 노트(wiki)의 한 줄 요약 — one-line summary from a Claude analysis note of the paper; verify against the source.

**arXiv:** https://arxiv.org/abs/2211.09898 · J. Hansen et al. · 2022

## 한 줄

이 논문은 RawNet2 기반 raw-waveform 탐지기에 세 가지를 더했다. 첫째는 residual block마다 넣은 SimAM attention, 둘째는 클래스별 weight와 margin을 다르게 준 AAM loss, 셋째는 relation network 기반 meta-learning이다. 이 셋을 함께 학습한 결과 ASVspoof2019 LA에서 pooled EER 0.99%를 얻었다.

---
_Part of [audio-deepfake-detection-papers](https://github.com/woongja/audio-deepfake-detection-papers) · AI-generated summary, unverified._
