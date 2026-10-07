# IMFD: End-to-end Multi-Face Forgery Detection through Instruction-based Large Vision-Language Models

> ⚠ AI-generated summary (local LLM, **Korean**, unverified) — auto-generated from the paper, not fact-checked. Verify against the source.

**arXiv:** https://arxiv.org/abs/2609.19693 · > **제출일:** 2026-09-17 · 2026

## 한 줄 요약

본 논문은 instruction-based Large Vision-Language Model (LVM)을 활용하여 다수의 얼굴을 포함하는 이미지에서 forgery된 얼굴을 검출하는 새로운 방법(IMFD)을 제안하며, instruction에 얼굴 위치 정보를 포함시키는 것이 성능 향상에 효과적임을 실험적으로 입증한다.

## 문제 정의

딥페이크 이미지의 급증은 디지털 미디어에 대한 신뢰를 저해하고 있으며, 특히 다수의 얼굴이 포함된 이미지에서의 forgery 검출은 기존의 binary classification 방식으로는 어려움이 있다. 기존의 forgery 검출 방법들은 얼굴의 위치 정보나 주변 맥락을 고려하지 않는 경우가 많아 성능이 제한적이며, 이는 다양한 각도와 크기로 삽입된 forgery된 얼굴을 식별하는 데 어려움을 야기한다.

## 제안 방법

본 논문에서는 instruction-based LVM을 기반으로 하는 다단계 파이프라인(IMFD)을 제안한다. IMFD는 입력 이미지와 텍스트 instruction을 받아, instruction을 통해 이미지 내 얼굴의 위치를 파악하고, 각 검출된 얼굴에 대해 독립적으로 forgery 여부를 분류한다. 핵심 아이디어는 instruction에 얼굴 bounding box 정보를 명시적으로 포함시켜 모델이 얼굴 위치를 더 정확하게 인식하고, forgery 검출에 집중하도록 유도하는 것이다.

## 실험·결과

IMFD는 OpenForensics 데이터셋을 사용하여 실험되었다. 실험에서는 instruction의 세부 내용(total number of people 포함 여부)과 입력 이미지 해상도를 변경하여 성능을 평가했다. 실험 결과, instruction에 얼굴 bounding box 정보를 포함시키는 것이 forgery 검출 성능 향상에 효과적이었으며, 입력 이미지 해상도가 증가함에 따라 F1 score와 F1a score가 꾸준히 증가하는 것을 확인했다. 또한, Grad-CAM 분석 결과 IMFD는 forgery된 얼굴에 더 집중하는 경향을 보였다.

## 한계

본 연구는 instruction에 얼굴 bounding box 정보를 포함시키는 것이 효과적이라는 것을 보여주지만, instruction의 내용이 제한적일 수 있으며, 복잡한 장면이나 다양한 포즈의 얼굴이 포함된 이미지에서는 여전히 어려움을 겪을 수 있다. 또한, instruction-based 방법은 모델의 크기와 계산 비용이 높을 수 있다는 단점이 있다.

---
_Part of [audio-deepfake-detection-papers](https://github.com/woongja/audio-deepfake-detection-papers) · AI-generated summary, unverified._
