# Dacon Smart Shipping and Logistics - 비정상작동 분류

이 프로젝트는 Dacon에서 주최한 스마트 운송 및 물류 경진대회의 비정상작동 분류 문제를 해결하기 위한 머신러닝 프로젝트입니다.

## 📊 대회 개요

- **대회명**: 스마트 운송 및 물류 비정상작동 분류
- **목표**: 센서 데이터를 기반으로 장비의 비정상작동을 분류하는 모델 개발
- **평가 지표**: F1-Score (macro)

## 📁 프로젝트 구조

```
├── train.csv                      # 훈련 데이터 (21,686개 샘플)
├── test.csv                       # 테스트 데이터 (15,000개 샘플)
├── sample_submission.csv          # 제출 양식
├── submission.csv                 # 최종 제출 파일
├── baseline_submit.csv            # 베이스라인 제출 파일
├── [Baseline]_RadnomForest를 활용한 비정상작동 분류.ipynb
├── RadnomForest를 활용한 비정상작동 분류 with Optuna.ipynb
├── RadnomForest를_활용한_비정상작동_분류.ipynb
└── 비정상작동_분류_with_Optuna.ipynb
```

## 📈 데이터 설명

### 데이터 구조
- **특성 (Features)**: X_01 ~ X_52 (총 52개 센서 데이터)
- **타겟 (Target)**: 비정상작동 클래스 (0-20, 총 21개 클래스)
- **훈련 데이터**: 21,686개 샘플
- **테스트 데이터**: 15,000개 샘플

### 데이터 특징
- 센서 데이터는 0-1 범위의 정규화된 값
- 일부 센서는 20-100 범위의 값도 포함
- 결측치 없음
- 다중 클래스 분류 문제

## 🚀 모델링 접근법

### 1. 베이스라인 모델
- **알고리즘**: Random Forest Classifier
- **특징**: 기본 하이퍼파라미터 사용
- **파일**: `[Baseline]_RadnomForest를 활용한 비정상작동 분류.ipynb`

### 2. 하이퍼파라미터 최적화 모델
- **알고리즘**: Random Forest Classifier + Optuna
- **최적화**: Optuna를 사용한 하이퍼파라미터 튜닝
- **파일**: `비정상작동_분류_with_Optuna.ipynb`

### 3. 앙상블 모델
- **알고리즘**: Stacking Classifier
- **구성**: Decision Tree + Random Forest + Logistic Regression
- **파일**: `RadnomForest를 활용한 비정상작동 분류 with Optuna.ipynb`

## 📋 실행 방법

### 1. 환경 설정
```bash
pip install pandas numpy scikit-learn optuna
```

### 2. 베이스라인 모델 실행
```bash
jupyter notebook "[Baseline]_RadnomForest를 활용한 비정상작동 분류.ipynb"
```

### 3. 최적화 모델 실행
```bash
jupyter notebook "비정상작동_분류_with_Optuna.ipynb"
```

## 📊 결과

### 제출 파일
- `submission.csv`: 최종 제출 파일 (최적화된 모델 결과)
- `baseline_submit.csv`: 베이스라인 모델 제출 파일

### 예측 결과 예시
```
ID,target
TEST_00000,4
TEST_00001,5
TEST_00002,0
TEST_00003,0
TEST_00004,0
TEST_00005,1
TEST_00006,8
TEST_00007,12
TEST_00008,4
```

## 🔧 기술 스택

- **Python**: 3.x
- **라이브러리**:
  - pandas: 데이터 처리
  - numpy: 수치 계산
  - scikit-learn: 머신러닝 모델
  - optuna: 하이퍼파라미터 최적화
  - jupyter: 개발 환경

## 📝 주요 특징

1. **다중 클래스 분류**: 21개 클래스의 비정상작동 패턴 분류
2. **하이퍼파라미터 최적화**: Optuna를 활용한 자동 튜닝
3. **앙상블 기법**: 여러 모델의 조합으로 성능 향상
4. **재현 가능성**: random_state 고정으로 일관된 결과

## 🎯 향후 개선 방향

1. **특성 엔지니어링**: 도메인 지식 기반 특성 생성
2. **딥러닝 모델**: 신경망 기반 모델 실험
3. **교차 검증**: 더 robust한 모델 평가
4. **클래스 불균형 처리**: SMOTE, 가중치 조정 등

## 📞 문의

프로젝트 관련 문의사항이 있으시면 이슈를 등록해 주세요.

---

*이 프로젝트는 Dacon 스마트 운송 및 물류 경진대회를 위해 개발되었습니다.*
