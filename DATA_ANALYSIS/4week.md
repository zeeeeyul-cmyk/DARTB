# 데이터분석 4주차 정규과제

📌데이터분석 정규과제는 매주 정해진 분량의 『*혼자 공부하는 데이터 분석 with 파이썬*』 을 읽고 학습하는 것입니다. 이번 주는 아래의 **DataAnalysis_4th_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=HNlRYQnLkek&list=PLVsNizTWUw7FGzSRCkQrPEEe-ljVXgS7k&index=8
https://www.youtube.com/watch?v=Cbk_tQtuhbM&list=PLVsNizTWUw7FGzSRCkQrPEEe-ljVXgS7k&index=9
-->


## DataAnalysis_4th_TIL

### 4장 데이터 요약하기
#### 01. 통계로 요약하기
#### 02. 분포 요약하기


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~81    | ✅         |
| 2주차 | p.84~151   | ✅         |
| 3주차 | p.154~219  | ✅         |
| 4주차 | p.222~279 | ✅         |
| 5주차 | p.282~325 | 🍽️         |
| 6주차 | p.328~379 | 🍽️         |
| 7주차 | p.382~430 | 🍽️         |

<br>

<!-- 여기까진 그대로 둬 주세요-->


# 1️⃣ 개념 정리 

## 01. 통계로 요약하기

describe() : 평균, 표준편차, 최솟값, 분위수, 최댓값 등 기술통계를 한번에 출력한다.
mean() / median() : 평균은 전체 합을 개수로 나눈 값, 중앙값은 정렬했을 때 가운데 값이다. 이상치가 많으면 평균보다 중앙값이 더 대표성이 있다.
min() / max() : 최솟값과 최댓값을 반환한다.
quantile() : 분위수를 구한다. quantile(0.25)는 하위 25%, quantile(0.75)는 상위 25% 기준값이다.
var() / std() : 분산은 데이터가 평균에서 얼마나 퍼져 있는지, 표준편차는 분산의 제곱근으로 단위가 원래 데이터와 같아 해석하기 쉽다.
mode() : 가장 많이 등장하는 최빈값을 반환한다.


## 02. 분포 요약하기

히스토그램 : 데이터를 구간(bin)으로 나눠 각 구간의 도수를 막대로 표현한다. bins 값으로 구간 수를 조정할 수 있고, 데이터가 한쪽에 몰려 있을 때 yscale('log')를 쓰면 분포를 더 잘 볼 수 있다.
상자 수염 그림 : 25%, 50%, 75% 분위수와 이상치를 한눈에 보여준다. 상자 안 선이 중앙값이고, 수염 밖의 점들이 이상치다. vert=False로 가로로 그릴 수 있다.
산점도 : 두 변수의 관계를 점으로 표현한다. 데이터가 많아 점이 겹칠 때 alpha 값을 낮춰서 밀도를 확인할 수 있다.

# 2️⃣ 수행 인증

<!-- 교재에서 안내된 과정을 직접 실행해본 뒤, 진행 결과가 보이도록 3장 이상의 스크린샷을 캡처하여 아래에 첨부해주세요.-->
<img width="859" height="636" alt="Image" src="https://github.com/user-attachments/assets/a1076ddb-e47b-49bd-84ac-a071ff390903" />
<img width="859" height="636" alt="Image" src="https://github.com/user-attachments/assets/1ce41079-b7c3-4bd1-a083-4e9bc805ae80" />
<img width="859" height="636" alt="Image" src="https://github.com/user-attachments/assets/5680a2cf-a714-437c-bfaa-d07343d6e5a6" />
<img width="859" height="636" alt="Image" src="https://github.com/user-attachments/assets/4039946f-4ca7-40cf-a804-312c26bc126f" />

<br>
<br>

# 3️⃣ 확인 문제

## 문제 1.

> **🧚Q. 이번 주차에는 확인문제 대신 실습 과제를 진행합니다. 캐글에서 원하는 데이터셋을 선택하여 기술통계를 계산하고, 다양한 시각화를 수행해보세요.
작업은 코랩에서 진행한 뒤, 코랩 링크를 아래에 첨부해주세요.**

```
https://colab.research.google.com/drive/16FFxIpU-tu3DnppQA27PRJALp3qVGsWL?usp=sharing
```



### 🎉 수고하셨습니다.
