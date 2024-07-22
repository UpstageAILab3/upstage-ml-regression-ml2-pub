# Title (Please modify the title)

## Team
<table>
  <tr>
    <td><img src="https://github.com/UpstageAILab3/upstage-ml-regression-ml2/assets/106630911/cc00f390-3789-4a05-8ace-035760a1df3f" width="200" ></td>
    <td><img src="https://github.com/UpstageAILab3/upstage-ml-regression-ml2/assets/106630911/a9f6008c-660a-49ae-9511-a2a89d38617e" width="200" ></td>
    <td><img src="https://github.com/UpstageAILab3/upstage-ml-regression-ml2/assets/106630911/7862e894-5fc7-416d-a6eb-8d319078bd58" width="200" ></td>
    <td><img src="https://github.com/UpstageAILab3/upstage-ml-regression-ml2/assets/106630911/22fe8a0c-78a8-44b1-ae09-071154098ed4" width="200" ></td>
    <td><img src="https://github.com/UpstageAILab3/upstage-ml-regression-ml2/assets/106630911/1b5b877c-eece-4e50-b9a0-a8ec43c36a88" width="200" ></td>
  </tr>
  <tr>
    <td align="center"><a href="https://github.com/UpstageAILab">전은지</a><br>팀장, 진행확인, 자료수집, 데이터 EDA, 데이터수집, 모델제안 및 이후결정</td>
    <td align="center"><a href="https://github.com/UpstageAILab">이수형</a><br>데이터수집, Feature Slection, 데이터 EDA, 모델 엔지니어링</td>
    <td align="center"><a href="https://github.com/UpstageAILab">서정민</a><br>데이터수집, 데이터 전처리, ,Feature Selection </td>
    <td align="center"><a href="https://github.com/UpstageAILab">이지윤</a><br>데이터수집, 파생 데이터 생성, 데이터 전처리</td>
    <td align="center"><a href="https://github.com/UpstageAILab">이승미</a><br>데이터수집, 데이터 전처리Feature Slection, 데이터 EDA</td>
  </tr>
</table>

## 1. Competition Info

### Overview
서울시 아파트 실거래가 매매 데이터를 기반으로 아파트 가격을 예측하는 모델을 개발합니다. 정확하고 일반화된 모델을 통해 아파트 시장의 동향을 미리 예측하고, 부동산 관련 의사결정을 돕고 효율적인 거래를 촉진하는 것이 목표입니다.

### Timeline
- **July 09, 2024**: Start Date
- **July 09 - 18, 2024**: Data Collection & Data EDA
- **July 16 - 19, 2024**: Model Engineering
- **July 19, 2024**: Final Submission Deadline

### Evaluation
$$
\text{RMSE} = \sqrt{\frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2}
$$

여기서:
- \( n \)은 데이터 포인트의 총 개수입니다.
- \( y_i \)는 실제 값입니다.
- \( \hat{y}_i \)는 예측 값입니다.

예측 값과 실제 값 간의 차이를 제곱한 후 평균을 내고, 그 평균의 제곱근을 구하여 계산합니다.

## 2. Components

### Directory
- `./code/`: 모델 실행에 사용되는 코드 위치
- `./code/eda/`: EDA에 사용된 코드 위치
- `./code/models/`: 모델 학습 후 저장된 모델 위치
- `./code/preprocessing/`: 전처리에 사용되는 코드 위치
- `./data/`: 모든 데이터 전처리 후 합쳐진 데이터셋 위치
- `./data/raw/`: 수집한 데이터의 원본 데이터 위치

## 3. Data Description

### Dataset Overview
- **첫 번째 데이터**: 국토교통부에서 제공하는 아파트 실거래가 데이터로, 아파트의 위치, 크기, 건축년도, 주변 시설 및 교통 편의성과 같은 다양한 특징들을 포함합니다. 데이터 크기는 1,118,822 x 52이며, 집값(Target)과 51개의 아파트 관련 변수를 제공합니다.
- **두 번째 데이터**: 평가 데이터로, 최종 모델 성능 검증을 위해 사용되며, Target을 제외한 51개의 아파트 변수를 제공합니다.
- **수집한 데이터**: GDP, 금리, 학원 수, 원생 수, 지하철 유동인구(승하차 수), 지하철 및 버스 정류장 좌표, 지하철 개통 날짜, 득표율, 초중고 좌표, 아파트 실거래 가격 지수, 경기 종합 지수

### EDA
- 그래프로 데이터 정보 확인
  - 전체 데이터의 분포와 Target 값과의 관계 분석
  - 범주형 데이터: 데이터 분포(바 그래프), Target 값 분포(바 그래프)
  - 연속형 데이터: 데이터 분포(히스토그램), Target 값 분포(산점도)
  - 연속형 데이터 간의 상관계수 히트맵
- 결측치 처리
  - 80만 개 이상의 결측치가 있는 feature 삭제
  - 좌표 X, Y가 비어 있는 경우 주소 데이터로 경도와 위도를 채움
  - 주소:
    - 시 + 구 + 도로명
    - 시 + 구 + 동 + 번지
  - 범주형 데이터: '-'
  - 기타 값 데이터: 0

### Feature Engineering
- 기존 데이터에서 파생 변수 생성
- ![스크린샷 2024-07-22 오전 11 17 50](https://github.com/user-attachments/assets/3aa8ad37-2884-4da4-956a-a71cf1256f73)
- ![스크린샷 2024-07-22 오전 11 15 14](https://github.com/user-attachments/assets/a1d4c4e4-2edd-44e5-9ed2-efed822185bd)
- ![스크린샷 2024-07-22 오전 11 15 45](https://github.com/user-attachments/assets/ff2397e7-d7c6-4c67-9594-04927fe3cdc5)

- 추가 데이터 사용
- ![스크린샷 2024-07-22 오전 11 19 34](https://github.com/user-attachments/assets/35335d95-03ec-470b-a53b-57a919c09311)


## 4. Modeling

### Model Description
- **모델 정보 및 선택 이유**: LGBM 모델을 사용하며, 성능이 뛰어나기 때문에 선택하였습니다.

### Feature Info
- **기존 변수**: '시군구', '번지', '아파트명', '전용면적', '계약년월', '계약일', '층', '건축년도', '등기신청일자', '거래유형', '좌표X', '좌표Y', 'target'
- **추가 변수**: '국내총생산(명목GDP)', '금리', '학원수', '학원생수', '총승객'
- **파생 변수**: '강남여부', '구', '동', '동_평균_target', '구_평균_target', '연도별평균', '동_년도_평균_target', '연식', '대장아파트_거리', 'bus_distances', 'subway_distances', '평당 가격', '매매 가격 상위 10% 동 여부', '매매 가격 상위 50% 동 여부'

### Modeling Process
- 모델 학습 및 테스트 과정 설명
- ![스크린샷 2024-07-22 오후 12 09 11](https://github.com/user-attachments/assets/1c3e786e-b70b-490e-a0e4-e0aa74d693a6)
- ![스크린샷 2024-07-22 오전 10 46 23](https://github.com/user-attachments/assets/46687595-9603-437d-8584-2449b57f2fea)
- ![스크린샷 2024-07-22 오전 10 46 54](https://github.com/user-attachments/assets/f7325b81-c6ba-4492-91d1-d2ed8c60d1bb)




## 5. Result

### Leader Board
- **Leaderboard [final]**
![1](https://github.com/user-attachments/assets/5d0544b3-78d1-4d53-9cd6-0bdab084bcad)

**순위 및 점수**: 최종 결과 12등 RMSE: 28295.7401

### Presentation
- [Presentation File](insert-your-presentation-file-link.pdf)

### Etc

#### Meeting Log
- [Meeting Log](https://www.notion.so/Regression-dacd070d20764a4a84cb70eb670f4205?pvs=4)
- [Meeting Log](https://www.notion.so/220c1f424a7c46daadb28d11bd2ad2a2?pvs=4)

## Reference
- Insert related references
