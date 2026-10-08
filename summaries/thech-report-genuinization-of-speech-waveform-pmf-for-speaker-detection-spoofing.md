# Thech. Report: Genuinization of Speech waveform PMF for speaker detection spoofing and countermeasures

> Claude 분석 노트(wiki)의 한 줄 요약 — one-line summary from a Claude analysis note of the paper; verify against the source.

**arXiv:** https://arxiv.org/abs/2310.05534 · I. Lapidot et al. · 2023

## 한 줄

genuine speech와 spoofed speech는 waveform amplitude PMF가 크게 다르다. 이 논문은 spoofed speech의 PMF를 genuine 쪽으로 quantile normalization하는 genuinization을 제안한다. 이것이 ASVspoof 2019 baseline countermeasure(LFCC/CQCC-GMM)를 크게 흔드는 단순 시간영역 공격이자, 학습 데이터 증강 수단으로 쓰일 수 있음을 보인다.

---
_Part of [audio-deepfake-detection-papers](https://github.com/woongja/audio-deepfake-detection-papers) · AI-generated summary, unverified._
