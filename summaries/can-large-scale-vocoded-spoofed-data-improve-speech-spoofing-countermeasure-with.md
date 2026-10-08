# Can large-scale vocoded spoofed data improve speech spoofing countermeasure with a self-supervised front end?

> Claude 분석 노트(wiki)의 한 줄 요약 — one-line summary from a Claude analysis note of the paper; verify against the source.

**arXiv:** https://arxiv.org/abs/2309.06014 · Xin Wang et al. · 2024

## 한 줄

VoxCeleb2를 4종 neural vocoder로 vocoding해 9,000시간 이상의 spoofed 데이터를 만들고, 이 데이터로 SSL front end를 continual self-supervised training한 뒤 pre-trained SSL과의 feature 차이를 student SSL에 distillation하면 unseen test set에서 CM 성능이 좋아진다는 연구다.

---
_Part of [audio-deepfake-detection-papers](https://github.com/woongja/audio-deepfake-detection-papers) · AI-generated summary, unverified._
