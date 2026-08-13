# ⚾ KBO 투구 제구 성공 확률 예측 AI (LG Aimers 9기 Hackathon)

투구 직전의 경기 상황, 선수 이력, 과거 Trackman 로그 데이터를 활용하여 각 투구의 제구 성공 확률을 예측하는 AI 모델링 프로젝트입니다.

---

## 📋 Project Overview
- **주제**: 투구 단위 제구 성공 확률(`control_success = 1`) 예측
- **평가 지표**: Brier Skill Score
- **진행 기간**: 2026.08 ~ 
- **Notion 실험일지**: [노션 링크](https://app.notion.com/p/LG-AIMERS-9-3b95b5453c4f80f9910ed60be093fbf6?source=copy_link)

---

## 🛠️ Project Structure
```text
├── src/                  # 학습 및 전처리 모듈
├── submit_builder/       # 제출용 패키징 (script.py, requirements.txt)
├── eda/                  # 데이터 분석 및 인사이트 탐색
└── README.md

```

## 📊 Experiment Results

| Exp ID | Model | Val Score | Public LB | Description |
| :--- | :--- | :---: | :---: | :--- |
| **Exp-001** | RandomForest | **415.57** | **549.64** | Baseline 파이프라인 구축 및 정상 제출 검증 완료 |

```
## 📊 Data Overview & Key Insights

### 1. Dataset Summary
- **Train Data**: 1,475,092 rows × 49 columns (2019 ~ 2024 KBO Season)
- **Test Data**: 2025 KBO Season
- **Target (`control_success`)**: Binary (1: 제구 성공 52.38%, 0: 제구 실패 47.62%)

### 2. Key EDA Insights & Preprocessing Strategy
| 구분 | 분석 내용 (Insight) | 전처리 및 모델링 반영 |
| :--- | :--- | :--- |
| **Target Distribution** | 성공률 52.38%로 클래스 균형 양호 | 별도의 Oversampling 없이 Brier Skill Score 최적화 집중 |
| **Time Horizon** | 연도별 시계열 데이터 (Train: ~24년 / Test: 25년) | Data Leakage 방지를 위해 **2024년 시즌을 Validation Set으로 분리** |
| **Missing Values** | 과거 이력 피처(`asof_`)에서 약 2.9만 건 NaN 발생 | 신인/이력 부족 선수로 판단하여 **비율/누적 변수 NaN = 0 대치** |
| **Feature Scale** | 상황 변수(0~3)와 누적 수치(15,000+) 간 스케일 차이 큼 | 대용량 및 다양한 스케일 처리에 강한 **Tree-based Model(LightGBM) 채택** |
