# 데이터분석 2주차 정규과제

📌데이터분석 정규과제는 매주 정해진 분량의 『*혼자 공부하는 데이터 분석 with 파이썬*』 을 읽고 학습하는 것입니다. 이번 주는 아래의 **DataAnalysis_2nd_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=s_-VvTLb3gs&list=PLVsNizTWUw7FGzSRCkQrPEEe-ljVXgS7k&index=4
https://www.youtube.com/watch?v=Il6L8OtNFpc&list=PLVsNizTWUw7FGzSRCkQrPEEe-ljVXgS7k&index=5
-->


## DataAnalysis_2nd_TIL

### 2장 데이터 수집하기
#### 01. API 사용하기
#### 02. 웹 스크래핑 사용하기


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~81    | ✅         |
| 2주차 | p.84~151   | ✅         |
| 3주차 | p.154~219  | 🍽️         |
| 4주차 | p.222~279 | 🍽️         |
| 5주차 | p.282~325 | 🍽️         |
| 6주차 | p.328~379 | 🍽️         |
| 7주차 | p.382~430 | 🍽️         |

<br>

<!-- 여기까진 그대로 둬 주세요-->


# 1️⃣ 개념 정리 

## 01. API 사용하기

API(Application Programming Interface)는 프로그램 간에 데이터를 주고받기 위한 통로다. 파이썬에서는 requests 라이브러리를 사용해 API에 HTTP 요청을 보내고 응답(주로 JSON 형식)을 받아온다.
pythonimport requests

url = "https://api.example.com/data"
response = requests.get(url)
data = response.json()  # JSON 응답을 딕셔너리로 변환
print(data)

핵심 개념:
requests.get(url) : GET 요청 전송
response.status_code : 응답 상태 코드 확인 (200 = 성공)
response.json() : JSON 응답을 파이썬 딕셔너리로 파싱
API 키가 필요한 경우 params 또는 headers에 포함해서 전달

## 02.웹 스크래핑 사용하기

웹 스크래핑은 웹 페이지의 HTML에서 원하는 데이터를 추출하는 기술이다. requests로 HTML을 받아오고, BeautifulSoup으로 파싱해 원하는 태그를 골라낸다.
pythonimport requests
from bs4 import BeautifulSoup

url = "https://example.com"
response = requests.get(url)
soup = BeautifulSoup(response.text, "html.parser")


titles = soup.find_all("h2")
for title in titles:
    print(title.get_text())

핵심 개념:
BeautifulSoup(html, 'html.parser') : HTML 문서를 파싱해 soup 객체 생성
find() : 조건에 맞는 첫 번째 태그 1개 반환
find_all() : 조건에 맞는 모든 태그 리스트로 반환
select() : CSS 선택자 방식으로 태그 추출
.get_text() : 태그 안의 텍스트만 추출


# 2️⃣ 수행 인증
<img width="1429" height="775" alt="Image" src="https://github.com/user-attachments/assets/40c1cf44-b0ab-4f07-8bf1-08c371b69f70" />
<img width="1186" height="654" alt="Image" src="https://github.com/user-attachments/assets/3e5bea94-ef31-4ddb-bbba-aedb2c0dac43" />
<img width="1186" height="654" alt="Image" src="https://github.com/user-attachments/assets/5617ee50-24d0-4b52-a024-36179cb596fa" />
<img width="1186" height="654" alt="Image" src="https://github.com/user-attachments/assets/20d36706-ed59-40f0-afca-02054e034a33" />
<img width="1186" height="654" alt="Image" src="https://github.com/user-attachments/assets/1fe00c08-6e5b-4865-a677-87e74c0fd8d8" />



<br>
<br>

# 3️⃣ 확인 문제

## 문제 1.

> **🧚Q. 다음 중 BeautifulSoup 외에 웹 스크래핑에 사용할 수 있는 파이썬 패키지로 가장 적절한 것은 무엇인가요?**

```
1️⃣ NumPy  
2️⃣ Scrapy  
3️⃣ Matplotlib  
4️⃣ Scikit-learn  
```

```
BeautifulSoup 외에 웹 스크래핑에 사용할 수 있는 파이썬 패키지는 Scrapy다.

NumPy: 수치 계산·배열 처리 라이브러리 (스크래핑 무관)
Scrapy: 웹 크롤링·스크래핑 전용 프레임워크로, 대규모 데이터 수집에 적합
Matplotlib: 데이터 시각화 라이브러리 (스크래핑 무관)
Scikit-learn: 머신러닝 라이브러리 (스크래핑 무관)

Scrapy는 BeautifulSoup보다 더 강력하고 구조화된 스크래핑 프레임워크로, 여러 페이지를 자동으로 순회하거나 대량의 데이터를 수집할 때 유용하다.
```



### 🎉 수고하셨습니다.
