# Wine Quality Detection 🍷

와인의 물리화학적 성분을 활용해 **우수 와인 여부를 분류**하고, Logistic Regression과 Decision Tree의 성능을 비교한 머신러닝 실습 프로젝트입니다.

## 프로젝트 개요

- **주제:** 화학 성분 기반 레드 와인 품질 이진 분류
- **데이터:** UCI Wine Quality (Red Wine), 1,599개 샘플, 화학 성분 11개
- **분류 기준:** 품질 점수 7점 이상 = 우수 와인(1), 6점 이하 = 일반 와인(0)
- **목표:** 데이터 탐색, 표준화, 분류 모델 학습, 혼동 행렬 및 오분류 분석

## 개발 환경

- Python
- Pandas, NumPy
- Matplotlib
- scikit-learn
- Jupyter Notebook / Google Colab

## 데이터셋

- **출처:** [UCI Machine Learning Repository — Wine Quality](https://archive.ics.uci.edu/dataset/186/wine+quality)
- **사용한 파일:** `data/winequality-red.csv` (레드 와인 1,599개, 화학 성분 11개와 품질 점수 1개)
- **논문:** Cortez et al. (2009), *Modeling wine preferences by data mining from physicochemical properties*

[UCI Wine Quality Dataset](https://archive.ics.uci.edu/dataset/186/wine+quality)

원본 데이터는 `winequality-red.csv`를 사용합니다. 이 파일은 세미콜론(`;`)으로 구분되어 있으며, 마지막 `quality` 컬럼에 품질 점수가 기록되어 있습니다.

> 원본 레드 와인 데이터 파일은 이 저장소의 [`data/winequality-red.csv`](data/winequality-red.csv)에 포함되어 있습니다. 출처: [UCI Machine Learning Repository – Wine Quality](https://archive.ics.uci.edu/dataset/186/wine+quality).

## 분석 과정

1. **데이터 탐색(EDA):** 데이터 크기, 자료형, 결측치, 기초 통계량 확인 및 품질 점수/알코올 함량 분포 시각화
2. **데이터 전처리:** 품질 점수를 이진 분류 라벨로 변환하고 입력 특성(X)과 정답(y)을 분리
3. **데이터 분리 및 표준화:** 80:20 비율로 층화 분할하고, Logistic Regression 입력에 StandardScaler 적용
4. **모델 학습:** LogisticRegression과 DecisionTreeClassifier(`max_depth=5`) 학습
5. **성능 평가:** Accuracy, Precision, Recall, F1-score 및 혼동 행렬 분석

## 모델 성능 비교

| 모델 | Accuracy | Precision | Recall | F1-score |
|---|---:|---:|---:|---:|
| LogisticRegression | 0.8938 | 0.6957 | 0.3721 | 0.4848 |
| **DecisionTreeClassifier** | **0.9188** | **0.7297** | **0.6279** | **0.6750** |

### 오분류 분석

| 모델 | FP | FN |
|---|---:|---:|
| LogisticRegression | 7 | 27 |
| DecisionTreeClassifier | 10 | 16 |

- **FP:** 일반 와인을 우수 와인으로 잘못 분류한 경우
- **FN:** 우수 와인을 일반 와인으로 잘못 분류한 경우

## 결과 및 결론

DecisionTreeClassifier는 LogisticRegression보다 정확도, 정밀도, 재현율, F1-score 모두 높은 결과를 보였습니다. 따라서 이번 와인 품질 분류 실험에서는 DecisionTreeClassifier가 전반적으로 더 좋은 성능을 보였습니다.

다만 일부 오분류가 발생했으며, 향후 하이퍼파라미터 튜닝을 통해 성능 개선을 시도할 수 있습니다.

## 실행 방법

1. 이 저장소의 `WineQualityDetection.ipynb`를 Jupyter Notebook 또는 Google Colab에서 엽니다.
2. 저장소에 포함된 `data/winequality-red.csv`를 사용합니다.
3. 노트북과 같은 폴더에 `data/` 폴더를 유지합니다. Google Colab에서는 해당 폴더를 업로드하거나 읽기 경로를 환경에 맞게 수정합니다.
4. 위에서 아래 순서로 전체 셀을 실행합니다.

## 파일 구성

```text
WineQualityDetection/
├── data/
│   └── winequality-red.csv        # UCI 원본 레드 와인 품질 데이터
├── WineQualityDetection.ipynb    # EDA, 데이터 전처리, 모델 학습 및 평가
├── README.md                     # 프로젝트 소개 및 분석 결과
└── requirements.txt              # 사용 라이브러리
```

## 참고

- 데이터 출처: Cortez et al., Wine Quality, [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/186/wine+quality)
- 본 프로젝트는 학습 목적으로 수행한 이진 분류 실험입니다. 결과는 해당 데이터 분할과 모델 설정에 대한 평가입니다.
