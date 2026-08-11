# ⚾ KBO 투구 제구 성공 확률 예측 AI (LG Aimers 9기 Hackathon)

투구 직전의 경기 상황, 선수 이력, 과거 Trackman 로그 데이터를 활용하여 각 투구의 제구 성공 확률을 예측하는 AI 모델링 프로젝트입니다.

---

## 📋 Project Overview
- **주제**: 투구 단위 제구 성공 확률(`control_success = 1`) 예측
- **평가 지표**: Brier Skill Score
- **진행 기간**: 2026.08 ~ 
- **Notion 실험일지**: [노션 링크][(https://www.notion.so)](https://app.notion.com/p/LG-AIMERS-9-3b95b5453c4f80f9910ed60be093fbf6?source=copy_link)

---

## 🛠️ Project Structure
```text
├── src/                  # 학습 및 전처리 모듈
├── submit_builder/       # 제출용 패키징 (script.py, requirements.txt)
├── eda/                  # 데이터 분석 및 인사이트 탐색
└── README.md

---

## 📊 Experiment Results

| Exp ID | Model | Val Score | Public LB | Description |
| :--- | :--- | :---: | :---: | :--- |
| **Exp-001** | RandomForest | **415.57** | **549.64** | Baseline 파이프라인 구축 및 정상 제출 검증 완료 |
