# Low-rank Adaptation Method for Wav2vec2-based Fake Audio Detection

> Claude 분석 노트(wiki)의 한 줄 요약 — one-line summary from a Claude analysis note of the paper; verify against the source.

**arXiv:** https://arxiv.org/abs/2306.05617 · Chenglong Wang et al. · 2023

## 한 줄

wav2vec2 XLSR 기반 fake audio detector의 Transformer self-attention에 LoRA를 넣었다. 학습 파라미터를 317M에서 1.6M으로 줄였고, ASVspoof2019 LA eval에서 full fine-tuning(EER 1.13%)과 비슷한 EER 1.30%를 얻었다.

---
_Part of [audio-deepfake-detection-papers](https://github.com/woongja/audio-deepfake-detection-papers) · AI-generated summary, unverified._
