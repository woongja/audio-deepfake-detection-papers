# Investigating self-supervised front ends for speech spoofing countermeasures

> Claude 분석 노트(wiki)의 한 줄 요약 — one-line summary from a Claude analysis note of the paper; verify against the source.

**arXiv:** https://arxiv.org/abs/2111.07725 · Xin Wang et al. · 2021

## 한 줄

pre-trained self-supervised 음성 모델(Wav2vec 2.0, HuBERT)을 spoofing countermeasure(CM)의 front end로 쓰고, back end 구조·fine-tuning 여부·사전학습 모델 종류를 체계적으로 비교했다. 그 결과 fine-tuned W2V-XLSR가 미지 공격과 codec·도메인 불일치 조건에서 LFCC baseline보다 크게 일반화됨을 보였다.

---
_Part of [audio-deepfake-detection-papers](https://github.com/woongja/audio-deepfake-detection-papers) · AI-generated summary, unverified._
