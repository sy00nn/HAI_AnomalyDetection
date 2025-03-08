# ⚙️ H Security Dataset 이상탐지 모델링
 `#DL/AI` `#Anomaly Detection`
 
 👩‍💻 **주요 역할**: 데이터 전처리, 모델링 및 최적화

 


  
## 📋 프로젝트 개요

- **데이터 환경**
    Hardware-In-the-Loop (HIL) 시뮬레이터 기반의 실제 산업 제어 시스템(ICS) 테스트베드
    
- **테스트베드 구성**
    증기-터빈 발전 및 양수-저장 수력 발전 모방(보일러 공정/터빈 공정/수처리 공정/HIL 시뮬레이션)
    
- **시계열 데이터**
    시간 연속성을 만족하는 데이터로, 여러 CSV 파일로 구성
    
- **공격 라벨**
    마지막 4개 열은 공격 여부를 나타내는 라벨 데이터 (정상: 0, 공격: 1)



## 🧩 평가지표

**TaPR (Temporal Precision and Recall):** 시계열 이상 탐지 성능 평가 지표
- **Temporal Precision**: 탐지된 이상 구간 중 실제 이상이 포함된 비율
- **Temporal Recall**: 실제 이상 구간 중 탐지된 비율
- **F1-Score**: Precision과 Recall의 균형을 평가하는 척도


  
## 🎯 모델링 결과

- **데이터 전처리**
    - **특징 생성**: 55만 개의 데이터에서 평균, 표준편차, 중앙값을 활용하여 비대칭도(skew) 계산
    - **결측값 처리**: NaN 값이 포함된 칼럼 제거
    - **스케일링**: RobustScaler를 사용한 데이터 정규화
    - **클래스 불균형 해결**: SMOTE 적용
- **모델링 및 최적화**
    - **모델 선택**: Autoencoder 기반 이상 탐지 모델
    - **하이퍼파라미터 최적화**: Optuna를 활용하여 모델의 하이퍼파라미터 최적화
    - **이상 탐지 기준**: 재구성 오류를 기준으로 95%, 98%, 동적 임계값 설정
- **결과**
    - **모델 성능**:  0.5327의 TaPR 성능 달성
