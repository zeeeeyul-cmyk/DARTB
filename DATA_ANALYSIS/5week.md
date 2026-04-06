# 데이터분석 5주차 정규과제

📌데이터분석 정규과제는 매주 정해진 분량의 『*혼자 공부하는 데이터 분석 with 파이썬*』 을 읽고 학습하는 것입니다. 이번 주는 아래의 **DataAnalysis_5th_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=ho0LZ6GWhtc&list=PLVsNizTWUw7FGzSRCkQrPEEe-ljVXgS7k&index=10
https://www.youtube.com/watch?v=deYY4xHsI0o&list=PLVsNizTWUw7FGzSRCkQrPEEe-ljVXgS7k&index=11
-->


## DataAnalysis_5th_TIL

### 5장 데이터 시각화하기
#### 01. 맷플롯립 기본 요소 알아보기
#### 02. 선 그래프와 막대 그래프 그리기


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~81    | ✅         |
| 2주차 | p.84~151   | ✅         |
| 3주차 | p.154~219  | ✅         |
| 4주차 | p.222~279 | ✅         |
| 5주차 | p.282~325 | ✅         |
| 6주차 | p.328~379 | 🍽️         |
| 7주차 | p.382~430 | 🍽️         |

<br>

<!-- 여기까진 그대로 둬 주세요-->


# 1️⃣ 개념 정리 

## 01. 맷플롯립 기본 요소 알아보기

1. figure()의 figsize 매개변수
그림의 크기(가로,*세로) 를 정함
단위는 inch
기본 크기는 plt.rcParams['figure.figsize']로 확인 가능

print(plt.rcParams['figure.figsize'])
plt.figure(figsize=(9, 6))
plt.scatter(ns_book7['도서권수'], ns_book7['대출건수'], alpha=0.1)
plt.show()

핵심
figsize=(9, 6) → 가로 9인치, 세로 6인치
그림의 실제 출력 크기를 키우는 역할

2. figure()의 dpi 매개변수
해상도를 정함
dpi가 높을수록 더 촘촘하게 표시됨

print(plt.rcParams['figure.dpi'])
plt.figure(dpi=144)
plt.scatter(ns_book7['도서권수'], ns_book7['대출건수'], alpha=0.1)
plt.show()

핵심
figsize는 그림 크기
dpi는 그림 선명도(해상도)

3. figsize와 dpi 함께 생각하기

plt.figure(figsize=(900/72, 600/72))
plt.scatter(ns_book7['도서권수'], ns_book7['대출건수'], alpha=0.1)
plt.show()

핵심
픽셀 기준 크기를 inch로 바꿔서 넣은 것
계산 방식: 픽셀 / dpi

4. rcParams 객체
matplotlib의 기본 설정값을 저장한 객체
한 번 바꾸면 이후 그래프에 기본 적용됨

plt.rcParams['figure.dpi'] = 100
plt.rcParams['scatter.marker']
plt.rcParams['scatter.marker'] = '*'
plt.scatter(ns_book7['도서권수'], ns_book7['대출건수'], alpha=0.1)
plt.show()

개별 그래프에서만 바꾸기
plt.scatter(ns_book7['도서권수'], ns_book7['대출건수'], alpha=0.1, marker='+')
plt.show()

핵심
rcParams → 전체 기본 설정 변경
함수 인자 marker='+' → 해당 그래프만 변경

5. subplots()
여러 개의 그래프를 한 figure 안에 나눠서 배치할 때 사용
fig, axs = plt.subplots(2, figsize=(6, 8))

axs[0].scatter(ns_book7['도서권수'], ns_book7['대출건수'], alpha=0.1)
axs[0].set_title('scatter plot')

axs[1].hist(ns_book7['대출건수'], bins=100)
axs[1].set_title('histogram')
axs[1].set_yscale('log')

fig.show()

핵심
plt.subplots(2, figsize=(6, 8))
세로로 2개 그래프 생성
axs[0], axs[1]
각각 첫 번째, 두 번째 축

6. subplots() 가로 배치 예시
fig, axs = plt.subplots(1, 2, figsize=(10, 4))

axs[0].scatter(ns_book7['도서권수'], ns_book7['대출건수'], alpha=0.1)
axs[0].set_title('scatter plot')
axs[0].set_xlabel('number of books')
axs[0].set_ylabel('borrow count')

axs[1].hist(ns_book7['대출건수'], bins=100)
axs[1].set_title('histogram')
axs[1].set_yscale('log')
axs[1].set_xlabel('borrow count')
axs[1].set_ylabel('frequency')

fig.show()

핵심
plt.subplots(1, 2) → 1행 2열
set_title() → 제목
set_xlabel(), set_ylabel() → 축 이름
set_yscale('log') → y축 로그 스케


## 02. 선 그래프와 막대 그래프 그리기

1. 선 그래프 그리기
값의 변화 흐름을 볼 때 사용
plt.plot() 사용
plt.plot(count_by_year.index, count_by_year.values)
plt.title('Books by year')
plt.xlabel('year')
plt.ylabel('number of books')
plt.show()

핵심
x축: count_by_year.index
y축: count_by_year.values
연도별 변화처럼 추세 볼 때 좋음

2. 선 스타일 바꾸기
marker, linestyle, color로 선 모양 바꿀 수 있음
plt.plot(count_by_year, marker='.', linestyle=':', color='red')
plt.title('Books by year')
plt.xlabel('year')
plt.ylabel('number of books')
plt.show()

또는 축약형으로도 가능:
plt.plot(count_by_year, '*-g')
plt.title('Books by year')
plt.xlabel('year')
plt.ylabel('number of books')
plt.show()

핵심
marker='.' → 점 표시
linestyle=':' → 점선
color='red' → 빨간색
'* - g' 같은 형식으로 한 번에 지정 가능

3. 그래프에 텍스트 출력하기
plt.annotate()로 그래프 위에 값 표시 가능
plt.plot(count_by_year, '*-g')
plt.title('Books by year')
plt.xlabel('year')
plt.ylabel('number of books')
plt.xticks(range(1947, 2030, 10))

for idx, val in count_by_year[::5].items():
    plt.annotate(val, (idx, val))

plt.show()

핵심
annotate(텍스트, 위치) 형식
(idx, val) 위치에 값 표시
count_by_year[::5] → 너무 많으니까 5개마다 하나씩 출력

4. 텍스트 위치 조정하기
텍스트가 점이랑 겹치면 xytext와 textcoords 사용
plt.plot(count_by_year, '*-g')
plt.title('Books by year')
plt.xlabel('year')
plt.ylabel('number of books')
plt.xticks(range(1947, 2030, 10))

for idx, val in count_by_year[::5].items():
    plt.annotate(val, (idx, val), xytext=(idx+1, val+10))

plt.show()
또는 offset 방식:
plt.plot(count_by_year, '*-g')
plt.title('Books by year')
plt.xlabel('year')
plt.ylabel('number of books')
plt.xticks(range(1947, 2030, 10))

for idx, val in count_by_year[::5].items():
    plt.annotate(val, (idx, val), xytext=(2, 2), textcoords='offset points')

plt.show()

핵심
xytext → 글자 위치를 원래 점에서 살짝 이동
textcoords='offset points' → 점 기준으로 몇 포인트 옮길지 설정

5. 막대 그래프 그리기
항목별 크기 비교할 때 사용
plt.bar() 사용
plt.bar(count_by_subject.index, count_by_subject.values)
plt.title('Books by subject')
plt.xlabel('subject')
plt.ylabel('number of books')

for idx, val in count_by_subject.items():
    plt.annotate(val, (idx, val), xytext=(0, 2), textcoords='offset points')

plt.show()

핵심
카테고리별 수량 비교에 적합
막대 위에 숫자 표시 가능

6. 막대 그래프 스타일 바꾸기
width, color, fontsize, ha 등 설정 가능
plt.bar(count_by_subject.index, count_by_subject.values, width=0.7, color='blue')
plt.title('Books by subject')
plt.xlabel('subject')
plt.ylabel('number of books')

for idx, val in count_by_subject.items():
    plt.annotate(val, (idx, val), xytext=(0, 2), textcoords='offset points',
                 fontsize=8, ha='center', color='green')

plt.show()

핵심
width=0.7 → 막대 너비
color='blue' → 막대 색
ha='center' → 텍스트 가운데 정렬

7. 가로 막대 그래프 그리기
항목 이름이 길거나 비교가 많을 때 보기 편함
plt.barh() 사용
plt.barh(count_by_subject.index, count_by_subject.values, height=0.7, color='blue')
plt.title('Books by subject')
plt.xlabel('number of books')
plt.ylabel('subject')

for idx, val in count_by_subject.items():
    plt.annotate(val, (val, idx), xytext=(2, 0), textcoords='offset points',
                 fontsize=8, va='center', color='green')

plt.show()

핵심
barh()는 가로 막대 그래프
height는 막대 두께
va='center' → 세로 가운데 정렬


# 2️⃣ 수행 인증

<!-- 교재에서 안내된 과정을 직접 실행해본 뒤, 진행 결과가 보이도록 4~6장의 스크린샷을 캡처하여 아래에 첨부해주세요.-->



<br>
<br>

# 3️⃣ 확인 문제

## 문제 1.

> **🧚Q. 다음 데이터를 이용하여 matplotlib으로 선그래프를 그리는 코드를 작성해주세요.**
- x = [1, 2, 3, 4, 5]
- y = [2, 4, 6, 8, 10]
> 조건은 아래와 같습니다.
```
1️⃣ 제목은 "Linear Trend"로 설정해주세요.
2️⃣ x축 이름은 "X values"로 설정해주세요.
3️⃣ y축 이름은 "Y values"로 설정해주세요.
4️⃣ 마커(marker)를 포함하여 선그래프를 그려주세요.
```

```
여기에 코드를 작성해주세요!
```



### 🎉 수고하셨습니다.