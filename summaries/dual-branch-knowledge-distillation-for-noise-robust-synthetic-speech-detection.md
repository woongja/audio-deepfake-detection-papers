# Dual-Branch Knowledge Distillation for Noise-Robust Synthetic Speech Detection

> Claude 분석 노트(wiki)의 한 줄 요약 — one-line summary from a Claude analysis note of the paper; verify against the source.

**arXiv:** https://arxiv.org/abs/2310.08869 · Cunhang Fan et al. · 2023

## 한 줄

DKDSSD는 clean teacher와 noisy student 두 branch를 함께 학습한다. student 쪽에서는 speech enhancement 결과와 원래 noisy 특징을 interactive fusion으로 섞고, response-based online knowledge distillation과 joint training을 더해 noisy 환경에서도 synthetic speech를 잘 탐지하게 한다.

---
_Part of [audio-deepfake-detection-papers](https://github.com/woongja/audio-deepfake-detection-papers) · AI-generated summary, unverified._
