# SQL_BASIC 4주차 정규 과제 

📌SQL_BASIC 정규과제는 매주 정해진 분량의 `초보자를 위한 BigQuery(SQL) 입문` 강의를 듣고 간단한 문제를 풀면서 학습하는 것입니다. 이번주는 아래의 **SQL_Basic_4th_TIL**에 나열된 분량을 수강하고 `학습 목표`에 맞게 공부하시면 됩니다.

**4주차 과제부터는 강의 내용을 정리하는 것과 함께, 프로그래머스에서 제공하는 SQL 문제를 직접 풀어보는 실습도 병행합니다.** 강의에서는 **배운 내용을 정리하고 주요 쿼리 예제를 정리**하며, 프로그래머스 문제는 **직접 풀어본 뒤 풀이 과정과 결과, 배운 점을 함께 기록**해주세요. 완성된 과제는 Github에 업로드하고, 링크를 스프레드시트 'SQL' 시트에 입력해 제출해주세요.

**👀(수행 인증샷은 필수입니다.)** 

## SQL_BASIC_4th

### 섹션 4. 쿼리 잘 작성하기, 쿼리 작성 템플릿 및 오류를 잘 디버깅하기

### 3-4. 오류를 잘 디버깅하는 방법



## 섹션 5. 데이터 탐색 - 변환

### 4-1. INTRO

### 4-2. 데이터 타입과 데이터 변환(CAST, SAFE_CAST)

### 4-3. 문자열 함수(CONCAT, SPLIT, REPLACE, TRIM, UPPER)

### 4-4. 날짜 및 시간 데이터 이해하기(1) (타임존, UTC, Millisecond, TIMESTAMP/DATETIME)



## 🏁 강의 수강 (Study Schedule)

| 주차  | 공부 범위              | 완료 여부 |
| ----- | ---------------------- | --------- |
| 1주차 | 섹션 **1-1** ~ **2-2** | ✅         |
| 2주차 | 섹션 **2-3** ~ **2-5** | ✅         |
| 3주차 | 섹션 **2-6** ~ **3-3** | ✅         |
| 4주차 | 섹션 **3-4** ~ **4-4** | ✅         |
| 5주차 | 섹션 **4-4** ~ **4-9** | 🍽️         |
| 6주차 | 섹션 **5-1** ~ **5-7** | 🍽️         |
| 7주차 | 섹션 **6-1** ~ **6-6** | 🍽️         |

<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 개념정리

## 3-4. 오류를 디버깅하는 방법

~~~
✅ 학습 목표 :
* 오류의 정의에 대해 설명할 수 있다. 
* 오류 메시지를 보고 디버깅이라는 과정을 수행할 수 있다. 
~~~

오류는 코드가 의도대로 실행되지 않을 때 발생하는 문제로, 무엇이 잘못됐는지 진단할 수 있게 해주는 길잡이 역할을 한다.

디버깅 프로세스
오류 발생 → 오류 메시지 확인 → 메시지 검색 → 수정

자주 보이는 오류 메시지
- `Syntax error` : 문법 오류
- `SELECT list must not be empty` : SELECT 절이 비어있으면 안 됨
- `Number of arguments does not match` : 함수 인자 수가 맞지 않음



## 4-2. 데이터 타입과 데이터 변환(CAST, SAFE_CAST)

~~~
✅ 학습 목표 :
* 데이터 타입의 종류를 설명할 수 있다. 
* 데이터 타입을 변환하는 방법을 설명할 수 있다. 
~~~

**데이터 타입 종류**
- 숫자 (INT, FLOAT)
- 문자 (STRING)
- 날짜/시간 (DATE, DATETIME, TIMESTAMP)
- 부울 (BOOL) : TRUE / FALSE

보이는 것과 실제 저장된 타입이 다를 수 있기 때문에 연산 전 타입 변환이 필요한지 확인해야 한다.

CAST : 타입 변환
```sql
CAST(1 AS STRING)  -- 숫자 1을 문자 '1'로 변환
```

SAFE_CAST : 변환 실패 시 오류 대신 NULL 반환
```sql
SAFE_CAST('abc' AS INT64)  -- NULL 반환
```

SAFE_DIVIDE : 0으로 나누는 오류 방지용, x/y 대신 사용
```sql
SAFE_DIVIDE(x, y)
```




## 4-3. 문자열 함수(CONCAT, SPLIT, REPLACE, TRIM, UPPER)

~~~
✅ 학습 목표 :
* 문자열 함수들의 종류를 이해하고 어떠한 상황에서 사용하는지 설명할 수 있다. 
~~~

- `CONCAT('a', 'b')` : 문자열을 이어 붙임. FROM 없이도 사용 가능
- `SPLIT(원본, 구분자)` : 구분자 기준으로 문자열을 나눠 배열로 반환
- `REPLACE(원본, 찾을단어, 바꿀단어)` : 특정 문자열 교체
- `TRIM(문자열)` : 앞뒤 공백 제거
- `UPPER(문자열)` : 모두 대문자로 변환



## 4-4. 날짜 및 시간 데이터 이해하기(1) (타임존, UTC, Millisecond, TIMESTAMP/DATETIME)

~~~
✅ 학습 목표 :
* 날짜 및 시간 데이터 타입과 UTC의 개념을 설명할 수 있다. 
* DATE, DATETIME, TIMESTAMP 에 대해서 설명할 수 있다.
* 시간함수들의 종류와 시간의 차이를 추출하는 방법을 설명할 수 있다. 
~~~

**날짜/시간 타입**
- `DATE` : 날짜만 저장
- `DATETIME` : 날짜 + 시간 (타임존 없음)
- `TIMESTAMP` : 날짜 + 시간 + 타임존 포함

**GMT vs UTC**
- GMT : 그리니치 천문대 기준, 지역별 시간 차이를 조정하기 위한 시간 체계
- UTC : GMT 기반의 국제 표준 시간. 한국(KST)은 UTC+9

**Millisecond**
- 1초 = 1,000ms
- 시스템 내부에서 시간을 ms 단위 숫자로 저장하는 경우가 많아 타입 변환이 필요할 수 있음

**시간 함수**
- 두 시간의 차이 : `DATETIME_DIFF`, `TIMESTAMP_DIFF`
- 특정 부분 추출 : `EXTRACT(YEAR FROM 날짜컬럼)`



<br>

<br>

---

# 2️⃣ 확인문제 & 문제 인증

## 프로그래머스 문제 

> 조건에 맞는 도서 리스트 출력하기
>
> **먼저 문제를 풀고 난 이후에 확인 문제를 확인해주세요**
>
> 문제 링크 
>
> :  https://school.programmers.co.kr/learn/courses/30/lessons/144853

<!-- 문제를 풀기 위하여 로그인이  필요합니다. -->

<img width="1440" height="783" alt="Image" src="https://github.com/user-attachments/assets/bed0fe30-a697-41e1-90f9-ac33a2fec616" />

<img width="1440" height="783" alt="Image" src="https://github.com/user-attachments/assets/ed3bd348-04b6-4177-9539-83aa75cde977" />



## 문제 1

> **🧚Q. 프로그래머스 문제를 풀던 규서는 여러 번의 시행착오 끝에 결국 혼자 해결하기 어려워 오류 메시지를 공유하며 도움을 요청했습니다. 여러분들이 오류 메시지를 확인하고, 해당 SQL 쿼리에서 어떤 부분이 잘못되었는지 오류 메시지를 해석하고 찾아 설명해주세요.**

~~~sql
# 조건에 맞는 도서 리스트 출력하기
# 규서의 SQL 첫 번째 풀이
SELECT BOOK_ID, PUBLISHED_DATE
FROM BOOK
WHERE CATEGORY = '인문'
  AND YEAR(PUBLISHED_DATE, 2021);
  
오류 메시지 : Error: Number of arguments does not match for function YEAR
~~~



~~~
YEAR() 함수는 인자를 하나만 받는데, YEAR(PUBLISHED_DATE, 2021)처럼 두 개를 넣어서 발생한 오류입니다.
연도를 조건으로 필터링하려면 아래처럼 작성해야 합니다.

AND YEAR(PUBLISHED_DATE) = 2021
~~~



### 🎉 수고하셨습니다.
