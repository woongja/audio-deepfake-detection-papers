# THE VICOMTECH AUDIO DEEPFAKE DETECTION SYSTEM BASED ON WAV2VEC2 FOR THE 2022 ADD CHALLENGE

> Claude 분석 노트(wiki)의 한 줄 요약 — one-line summary from a Claude analysis note of the paper; verify against the source.

**arXiv:** https://arxiv.org/abs/2203.01573 · J. M. Martín-Doñas et al. · 2022

## 한 줄

사전학습된 wav2vec2(XLS-53/XLS-128)를 동결한 채 24개 transformer 층 표현을 가중합해 경량 downstream 분류기에 넣고, FIR 필터와 partial-fake 증강으로 적응시킨 시스템이다. 이 시스템은 ADD 2022 Track 1에서 1위, Track 2에서 4위를 했다.

---
_Part of [audio-deepfake-detection-papers](https://github.com/woongja/audio-deepfake-detection-papers) · AI-generated summary, unverified._
