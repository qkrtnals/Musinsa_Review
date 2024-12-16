# Musinsa_Review
## MobileBERT를 활용한 와인 리뷰 분석 프로젝트
badge icon 참고 사이트<br>
<img src="https://img.shields.io/badge/python-%233776AB.svg?&style=for-the-badge&logo=python&logoColor=white" />
<img src="https://img.shields.io/badge/pytorch-%23EE4C2C.svg?&style=for-the-badge&logo=pytorch&logoColor=white" />
<img src="https://img.shields.io/badge/pycharm-%23000000.svg?&style=for-the-badge&logo=pycharm&logoColor=white" />

   - 서론 (왜 하는지?, 어떤 의미가 있는지, 데이터는 어떻게 수집할 계획인지)
   - 데이터 수집을 어떻게 했는지 (소스코드 업로드)
   - 데이터 자체의 경우에는 kaggle에 업로드 하고 링크를 보고서에 언급
     * 데이터 자체가 문제가 될수도 있음 (저작권)
     * 가능하면 업로드 / 안해도 무방
   - 데이터 라벨링 과정을 상세하게 작성하기
   - 기본적인 탐색적 데이터 분석 하기
   - 학습 :  epoch별 학습 정확도 / 검증 정확도 그래프
     * 학습 loss 그래프는 별도로 그리기
   - 결과 
     * 라벨이 있는 경우 : 전체 데이터셋에 대한 최종 정확도
     * 라벨이 없는 경우 : 다양한 분석으로 시각화 (긍부정 비율 등)
     * (추가사항) 가능한 토픽 모델링을 하여 현상을 설명해보기
  - 느낀점 및 보완방향

## 1. 서론
무신사에서 청바지를 판매하는 쇼핑몰 여러개를 골라 그 중 리뷰가 많은 청바지를 4개씩 골라 리뷰를 수집한다.
수집 된 리뷰를 분석하여 청바지를 어떻게 제작해야 많이 판매를 할 수 있는지 알아볼 수 있다. <br>
https://www.dailycnc.com/news/articleView.html?idxno=209683 기사에 따르면 
![209683_214106_921](https://github.com/user-attachments/assets/a5d322e8-16b4-463c-a54b-12fad00f8794) <br>
현대 소비자들은 제품을 구매할 때 온라인 리뷰를 많이 참고한다는 조사 결과가 나타났다.
패션산업에서는 소비자 리뷰가 제품 디자인, 품질, 착용감 등 트렌드 반영 여부에 대한 생생한 피드백을 제공하기에 판매에 큰 영향을 미친다.
이에 따라 리뷰 데이터를 분석하여 소비자 선호도를 이해하고, 제품 개발 및 마케팅 전략에 반영하는 것은 온라인 쇼핑몰의 경쟁력을 강화하는 중요한 요소이다.
이번 프로젝트에서는 무신사에서 청바지를 판매하는 여러 쇼핑몰을 대상으로, 리뷰가 많은 청바지 4개씩을 선정하여 리뷰 데이터를 수집하였다. 이러한 리뷰 데이터를 기반으로 소비자들이 고려해야 할 주요 요소를 파악하고, 소비자의 요구를 충족시킬 수 있는 디자인과 품질 개선 방안을 제안하려한다.
본 보고서의 목적은 리뷰 데이터를 분석하여 청바지의 성공적인 판매를 위한 통찰을 얻는 것이다.

## 2. 데이터 수집을 어떻게 했는지

## 3. 데이터 라벨링 과정 (상세하게 작성)

## 4. 기본적인 탐색적 데이터 분석

## 5. 학습 :  epoch별 학습 정확도 / 검증 정확도 그래프 (학습 loss 그래프는 별도로 그리기)

## 6. 결과

## 7. 느낀점 및 보완빙행
