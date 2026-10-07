# Exposing and Mitigating Neural Codec Vulnerabilities in Audio Deepfake Detection

> Claude 분석 노트(wiki)의 한 줄 요약 — one-line summary from a Claude analysis note of the paper; verify against the source.

**arXiv:** https://arxiv.org/abs/2610.07216 · Abdullah et al. · 2026

## 한 줄

SOTA ADD 모델은 정상적인 neural codec 압축만 거쳐도 크게 무너진다. 특히 CoRS로 학습한 모델이 가장 취약하다. 저자들은 이를 ANC-Spoof 데이터셋으로 드러내고, 원본과 codec 압축본의 표현을 맞추는 pairwise consistency 학습(PCL-NET)을 baseline 완화책으로 제안한다.

---
_Part of [audio-deepfake-detection-papers](https://github.com/woongja/audio-deepfake-detection-papers) · AI-generated summary, unverified._
