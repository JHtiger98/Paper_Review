# A Study on the Failure Prediction Model Using Sensor Data in Semiconductor Equipment and Deep Learning
### 반도체 장비 센서데이터와 딥러닝을 활용한 불량예측모델에 관한 연구
- [Link](https://www.kci.go.kr/kciportal/ci/sereArticleSearch/ciSereArtiView.kci?sereArticleSearchBean.artiId=ART002712106)
- Reference: 하승재, 김도연, 구교연 and 신용태. (2021). 반도체 장비 센서데이터와 딥러닝을 활용한 불량예측모델에 관한 연구. 한국IT정책경영학회 논문지, 13(2), 2375-2379.

----------
## 서론
반도체의 공정은 크게 8가지(웨이퍼 공정, 산화 공정, 포토 공정, 식각 공정, 박막 공정, 금속 공정, EDS 공정, 패키지 공정)로 구성되어 있다. 본 연구에서는 박막 공정에 대한 연구를 진행하였다. 박막(Thin film)은 1um이하의 매우 얇은 막을 말하며, 박막은 매우 미세하기 때문에 정교하고 세밀한 기술이 필요 하다. 본 연구에서는 반도체 박막공정의 센서 데이터로부터 시계열 특성을 파악하여 머신러닝 기법들을 이용하여 박막 공정에서의 품질 예측의 정확성, 정밀성, F1-score 등을 제시하고, 기존 반도체 박막 공정의 품질을 관리하는 FDC 시스템의 데이터와도 비교분석을 하고자 한다.

----------
## 관련 연구
본 연구 에서는 산업 제조과정에서 수집된 순차 센서 데이터의 이상을 탐지하기 위해 인코더-디코더 아키텍처를 활용하는 새로운 비지도 심층 학습 접근 방식을 제시한다. 이 접근 방식은 주어진 시간 단계에서 이상이 있는 지 여부를 감지할 뿐만 아니라 프로세스에서 다음에 일어날 일을 예측하도록 설계되었다. 이상 탐지의 목표는 정상 동작이라는 잘 정의된 개념을 따르지 않는 데이터의 패턴을 식별하는 것이다. 이상 징후와 결함을 조기에 감지하면 모델 제조를 위한 예방 유지 보수를 계획할 수 있으므로 프로세스 제어에 매우 중요하다.<br>
오토 인코더는 먼저 정상이거나 거의 결함이 없는 데이터에 대해 학습된다. 오토 인코더 모델에서 제공하는 재구성 오류는 잠재적인 이상을 나타내는 이상 점수로 자주 사용되며, 또한 이 접근법은 다변수 시계열의 이상 탐지를 위해 사용된다. 마찬가지로 예측 작업에 인코더-디코더 아키텍처를 사용할 수도 있으며, 시계열 데이터의 경우 신경망 예측 모델을 학습하여 과거 관찰에서 미래를 예측할 수 있다. 예측의 정답과 오답을 각각 오차행렬(Confusion Matrix)에 기재하여 정확도(Accuracy), 정밀도(Precision), 재현율(Recall), F1-score 등의 검증 지표를 계산 하였다.

----------
## 데이터 소개
### 데이터 수집과 전처리
센서데이터: 17개
입력데이터: 28,678(불량: 7)개
- **센서 구성표**
<img src="https://user-images.githubusercontent.com/121841464/232309690-4c70b88e-9c3d-428b-9e0f-70c8df169268.png" width="300">

반도체 박막공정의 센서 데이터는 동일한 레시피라도 데이터가 동일하지 않고, 다양한 노이즈가 존재하며, 정상 데이터 대비 비정상 데이터가 매우 적어 데이터의 불균형이 존재하는 특징이 있다. 이러한 데이터의 특성을 고려하여 제조공정에서 수집된 데이터는 분석을 위하여 다음과 같은 전처리를 수행하였다.<br>
> 1. 설비 및 레시피 별 자료를 분류하여 동일한 설비 및 레시피에 대해 실험을 진행
> 2. 제조공정의 시계열 데이터의 시간 차이를 표준화 후 분석 진행

- **데이터 구조**
<img src="https://user-images.githubusercontent.com/121841464/232309846-b5776107-28c3-4451-b2bb-a7819f6bb962.png" width="300">

### 예측 모델
센서로부터 측정되는 품질 이상여부 예측 모델링을 위하여 오토 인코더 알고리즘을 사용하였으며, 예측모델의 성과를 측정하기 위하여 MAE(Mean Absolute Error)를 사용하였다.

- **학습 모델**
<img src="https://user-images.githubusercontent.com/121841464/232311263-4179a6c7-905f-41c0-b59e-08b52a8e126d.png" width="500">

- **테스트 모델**
<img src="https://user-images.githubusercontent.com/121841464/232311352-e39ac65f-2fbb-4732-bfe4-d5b3ab7882f3.png" width="500">

----------
## 연구 결과
- **학습 과정에 따른 정확도**
<img src="https://user-images.githubusercontent.com/121841464/232312118-8386e46e-dd75-4a19-bea1-c93dc1a2061b.png" width="400">

- **원/복원 데이의 차이값 히스토그램**
<img src="https://user-images.githubusercontent.com/121841464/232312162-5349441d-aba2-427b-b4ac-35c586a26bdb.png" width="400">

- **정상 데이터 예시**
<img src="https://user-images.githubusercontent.com/121841464/232312352-23cef49e-2310-4cb2-a521-8cffdf794610.png" width="400">

- **비정상 데이터 예시**
<img src="https://user-images.githubusercontent.com/121841464/232312391-07d1181e-9e38-45c6-a644-8013e2de938b.png" width="400">

- **실제 불량 데이터 차이값 히스토그램**
<img src="https://user-images.githubusercontent.com/121841464/232312408-8fc9de32-3671-4e27-aa55-23f89498a5f6.png" width="400">

- **딥러닝 모델과 FDC의 예측결과**
<img src="https://user-images.githubusercontent.com/121841464/232312505-7ab656df-3a7d-4f22-a378-211a972d1dc0.png" width="400">
