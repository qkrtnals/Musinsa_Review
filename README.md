# Musinsa_Review
badge icon 참고 사이트<br>
<img src="https://img.shields.io/badge/python-%233776AB.svg?&style=for-the-badge&logo=python&logoColor=white" />
<img src="https://img.shields.io/badge/pytorch-%23EE4C2C.svg?&style=for-the-badge&logo=pytorch&logoColor=white" />
<img src="https://img.shields.io/badge/pycharm-%23000000.svg?&style=for-the-badge&logo=pycharm&logoColor=white" />


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
데이터 수집은 웹 크롤링 기술을 이용하여 진행되었으며, 이를 통해 각 청바지 제품의 상세 페이지에서 리뷰 정보를 자동으로 추출하였다. <br>
<br>
<크롤링 과정> <br>
1. 쇼핑몰 선정<br>
- 무신사에서 청바지를 판매하는 여러 쇼핑몰을 대상으로, 각 쇼핑몰에서 판매되고 있는 청바지 제품 중 리뷰가 많은 제품을 선정
2. 리뷰 데이터 추출<br>
- 선정된 청바지 제품의 상세 페이지에서 소비자 리뷰 데이터를 크롤링
- 각 제품 페이지에서 소비자 리뷰 내용(Review), 평점(Rating), 작성 날짜(Date)를 추출후 csv 파일로 저장
- 저장 된 각각의 csv 파일에 맞는 쇼핑몰명, 상품명을 추가
- 여러 csv파일을 하나의 파일 통합
   
3. 크롤링 도구 <br>
- Selenium 사용<br>
     (Selenium은 웹 브라우저를 직접 제어할 수 있는 기능을 제공하여, 웹 페이지 상의 요소를 자동으로 클릭하거나 스크롤하며 필요한 정보를 수집할 수 있게 해준다.)<br>
     ![화면 캡처 2024-12-16 144914](https://github.com/user-attachments/assets/e5947e8c-719a-4a2b-aae9-20296487ccb1) (코드예시)


## 3. 데이터 라벨링 과정 (상세하게 작성)
- 추출한 리뷰 데이터에서 NaN값이 들어있는 리뷰를 제외하면 평점(Rating)이 4점 이상은 9972건, 3점 이하는 254건
  ![0000](https://github.com/user-attachments/assets/36a87b6b-fb59-4e38-aabe-bc2ad4cb4c4c)
   - 별점이 4점 이상인 리뷰는 긍정(1) 라벨을 부여
   - 별점이 3점 이하인 리뷰는 부정(0) 라벨을 부여
   - 위의 데이터를 기반으로, Koelectra-base-v3-discriminator 모델을 사용하여 감정 분석을 위한 학습을 진행 <br>
   (이 모델은 한국어 자연어 처리에서 우수한 성능을 보이는 Electra 모델을 기반으로 한 모델로, 감정 분석에 적합한 구조를 가지고 있다.) <br>
학습은 4 epochs에 걸쳐 진행되었으며, 각 epoch마다 학습 오차(loss)와 정확도(accuracy)가 측정되었다. 학습 중 loss는 꾸준히 감소했으며, 최종적으로 모델의 학습 정확도는 98.2%, 검증 정확도는 86.6%로 나타났다.
![000](https://github.com/user-attachments/assets/b71597f3-d72e-485c-a240-728bdf837779)


## 4. 기본적인 탐색적 데이터 분석
- 데이터 구성 <br>
![0011](https://github.com/user-attachments/assets/41b84e3d-7b21-4f49-aa68-bb7f1b3bb7df) <br>
Review(리뷰), 쇼핑몰명, 상품명, Rating(별점), Date(날짜), pred_label(긍부정)의 칼럼이 있다. <br><br>

<NaN값이 없는 데이터>
- 쇼핑몰별 긍정리뷰와 부정리뷰 그래프<br>
![긍부정그래프](https://github.com/user-attachments/assets/d232a507-c53b-446d-81fb-ba97e0ce5896) <br>
그래프를 보면 긍정 리뷰가 가장 많은 쇼핑몰은 트릴리온이고, 부정 리뷰가 가장 많은 쇼핑몰은 페이탈리즘이다. <br>
- 쇼핑몰 트릴리온의 긍부정 리뷰 살펴보기<br>
   - 부정리뷰
![10](https://github.com/user-attachments/assets/a486d491-c7d2-4a36-bcff-342eb2da1ef3) <br>
별점이 4.0이상임에도 부정 리뷰가 많다.<br>
 별점이 높더라도 부정적인 리뷰가 있다는 것을 확인할 수 있다.<be>
   - 긍정리뷰
  ![트릴리온긍정](https://github.com/user-attachments/assets/da4ae6a2-811d-4b0c-9cd6-41dcf953ade4) <br>
- 쇼핑몰 페이탈리즘의 긍부정 리뷰 살펴보기 <br>
   - 부정리뷰
     
 
   - 긍정리뷰


## 5. 학습 그래프
- epoch별 학습 정확도 / 검증 정확도 그래프<br>
![11](https://github.com/user-attachments/assets/378dce85-71cb-4a72-80cf-586fa3c02ee3)
   - 파란색 그래프는 학습 정확도
   - 빨간색 그래프는 검증 정확도<br><br>
- 학습 loss 그래프<br>
![22](https://github.com/user-attachments/assets/ce4ff23a-139a-4cb7-877b-0fbd70eb8a6b)

## 6. 결과
학습을 진행하면서 모델의 정확도가 향상되었고, loss 값은 꾸준히 감소하는 것을 확인할 수 있었다.

* (추가사항) 가능한 토픽 모델링을 하여 현상을 설명해보기<br>
<NaN값이 포함 모든 데이터>
- 긍정리뷰가 가장 많은 상품보기<br>
  ![긍정리뷰가가장많은상품명](https://github.com/user-attachments/assets/70d98204-a4f1-4849-8431-5ad16dfe932d)
- 부정리뷰가 가장 많은 상품보기<br>
  ![부정리뷰가가장많은상품](https://github.com/user-attachments/assets/dfc3119b-ced8-486c-9f48-efc7252615fd)
<br>
- 긍정리뷰가 가장 많은 상품과 부정리뷰가 가장 많은 상품의 토픽 모델링을 하여 긍정리뷰에 많이 사용된 단어와 부정리뷰에 많이 사용된 단어보기

## 7. 느낀점 및 보완방향
이번 프로젝트를 통해 리뷰 데이터를 크롤링하고 이를 분석하여 소비자들이 선호하는 제품의 특징과 개선점을 파악하는 과정에서 여러 가지 중요한 정보를 얻을 수 있었다. <br>
크롤링 과정에서 19763견의 리뷰 데이터를 추출했지만, 리뷰내용, 별점, 날짜가 완벽하게 추출된 데이터는 10226건에 불과하여 아쉬운 점이 있었다. 데이터에 NaN값이 존재하는 것을 미리 확인했다면, 이를 보완하거나 부족한 데이터를 다시 수집하는 방식으로 문제를 해결할 수 있었을 텐데, 아쉽게도 시간이 부족하여 처리할 수 없었다. 이런 부분에서 앞으로는 크롤링할 때, 데이터의 누락이나 이상값을 미리 점검하고, 이를 처리하는 코드를 추가해보면 좋을 것 같다고 생각했다. <br>
또한 소비자가 어떤 제품에 관심을 가지고 어떤 부분에 대해 개선이 필요하다고 생각하는지알 수 있었고, 제품을 개선하거나 마케팅 전략을 수립하는데 있어 중요한 참고자료가 될 수 있겠구나 생각하게 되었다.
