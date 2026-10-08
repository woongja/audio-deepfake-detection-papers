# A Comparative Study on Recent Neural Spoofing Countermeasures for Synthetic Speech Detection

> Claude 분석 노트(wiki)의 한 줄 요약 — one-line summary from a Claude analysis note of the paper; verify against the source.

**arXiv:** https://arxiv.org/abs/2103.11326 · Xin Wang et al. · 2021

## 한 줄

ASVspoof 2019 LA에서 가변 길이 입력 처리 방식, loss function, front end를 조합해 6회씩 반복 학습·평가했다. 그 결과 random seed 하나만 바꿔도 같은 모델의 EER이 통계적으로 유의하게 달라졌다. 하이퍼파라미터가 없는 MSE for P2SGrad loss와 LFCC + LCNN-LSTM-sum 조합은 단일 run 최저 EER 1.92%를 냈다.

---
_Part of [audio-deepfake-detection-papers](https://github.com/woongja/audio-deepfake-detection-papers) · AI-generated summary, unverified._
