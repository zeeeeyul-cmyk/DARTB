# SQL_BASIC 2주차 정규 과제 

📌SQL_BASIC 정규과제는 매주 정해진 분량의 `초보자를 위한 BigQuery(SQL) 입문` 강의를 듣고 간단한 문제를 풀면서 학습하는 것입니다. 이번주는 아래의 **SQL_Basic_2nd_TIL**에 나열된 분량을 수강하고 `학습 목표`에 맞게 공부하시면 됩니다.

**2주차 과제**는 1주차 과제처럼 SQL의 필요성이나 느낀점 위주가 아닌, **실제 강의 내용을 바탕으로 개념을 정리하고 학습한 내용을 집중적으로 기록**해주세요. 완성된 과제는 Github에 업로드하고, 링크를 스프레드시트 'SQL' 시트에 입력해 제출해주세요. 

**👀(수행 인증샷은 필수입니다.)** 

## SQL_BASIC_2nd

### 섹션 3. 데이터 탐색 - 조건, 추출, 요약

### 2-3. 데이터 탐색 (SELECT, FROM, WHERE)

### 2-4. SELECT 연습문제

### 2-5. 집계 (Group By + Having + Sum/Count)



## 🏁 강의 수강 (Study Schedule)

| 주차  | 공부 범위              | 완료 여부 |
| ----- | ---------------------- | --------- |
| 1주차 | 섹션 **1-1** ~ **2-2** | ✅         |
| 2주차 | 섹션 **2-3** ~ **2-5** | ✅         |
| 3주차 | 섹션 **2-6** ~ **3-3** | 🍽️         |
| 4주차 | 섹션 **3-4** ~ **4-4** | 🍽️         |
| 5주차 | 섹션 **4-4** ~ **4-9** | 🍽️         |
| 6주차 | 섹션 **5-1** ~ **5-7** | 🍽️         |
| 7주차 | 섹션 **6-1** ~ **6-6** | 🍽️         |

<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 개념정리 

## 2-3. 데이터 탐색 (SELECT, FROM, WHERE)

~~~
✅ 학습 목표 :
* SQL 쿼리 구조를 이해할 수 있다. 
* SELECT, FROM, WHERE의 핵심 문법을 설명할 수 있다. 
~~~

SQL은 데이터베이스에서 원하는 데이터를 조회할 때 사용하는 언어이다. 기본적인 조회문은 SELECT, FROM, WHERE 순서로 작성한다.

SELECT: 조회하고 싶은 열(컬럼)을 선택하는 문법
FROM: 데이터를 가져올 테이블을 지정하는 문법
WHERE: 특정 조건에 맞는 데이터만 선택할 때 사용하는 문법

예를 들어 포켓몬 테이블에서 이름과 타입을 조회하려면 SELECT name, type FROM pokemon과 같이 작성할 수 있다. 여기에 전기 타입 포켓몬만 조회하고 싶다면 WHERE type = 'Electric' 조건을 추가하면 된다.
즉, SELECT는 무엇을 볼지, FROM은 어디서 가져올지, WHERE는 어떤 조건으로 찾을지를 정하는 문법이다. 이를 통해 SQL이 원하는 데이터를 조건에 맞게 효율적으로 조회할 수 있도록 도와주는 언어라는 점을 이해했다.


## 2-5. 집계 (Group By / HAVING / SUM,COUNT)

~~~
✅ 학습 목표 :
* 데이터를 집계하고 그룹화하는 방법을 설명할 수 있다.
* GROUP BY, HAVING, ORDER BY, 집계함수(SUM/COUNT 등)을 활용하는 방법을 설명할 수 있다.
* having과 where의 차이에 대해서 설명할 수 있다.
~~~

집계는 여러 데이터를 하나로 묶어 개수, 합계, 평균 등의 값을 구하는 작업이다. 이때 COUNT, SUM, AVG와 같은 집계 함수를 사용할 수 있다.

COUNT: 데이터의 개수를 세는 함수
SUM: 데이터의 합계를 구하는 함수
AVG: 데이터의 평균을 구하는 함수
GROUP BY: 같은 값을 가진 데이터끼리 그룹으로 묶는 문법
HAVING: 그룹화한 결과에 조건을 줄 때 사용하는 문법
WHERE: 그룹화 전에 개별 행에 조건을 줄 때 사용하는 문법
HAVING과 WHERE의 차이: WHERE는 원본 데이터에 조건을 주고, HAVING은 집계한 결과에 조건을 줌
ORDER BY: 조회 결과를 특정 기준에 따라 정렬하는 문법


# 2️⃣ 학습 인증란

<img width="2360" height="1640" alt="Image" src="https://github.com/user-attachments/assets/c2d6ba39-6671-4aff-97fc-7dccd2e8ee89" />

<img width="1429" height="775" alt="Image" src="https://github.com/user-attachments/assets/3bb5b093-689f-4d0c-8e35-60a802f50508" />



<br><br>



---

# 3️⃣ 확인문제

## 문제 1

> **🧚Q. 포켓몬 마스터 진아는 포켓몬 데이터 조회하는 SQL문에 재미를 느껴서 혼자서 데이터를 조회하는 쿼리문을 짰습니다. 하지만 세 가지의 오류로 다음 코드가 실행이 안된다고 하는데, 각 오류의 위치와 이유를 설명하고, 올바른 쿼리문으로 수정해보세요.**

~~~sql
# 진아의 SQL Query문 
SELECT name. type
FROM pokemon;
WHERE type = Electric;
~~~



~~~
먼저 SELECT name. type에서 name과 type은 각각 다른 컬럼이기 때문에 마침표가 아니라 쉼표로 구분해야 한다. 또 FROM pokemon;에서 세미콜론이 먼저 들어가서 쿼리가 중간에 끝나버린다. 마지막으로 Electric는 문자열 값이기 때문에 작은따옴표로 감싸줘야 한다.

SELECT name, type
FROM pokemon
WHERE type = 'Electric';
~~~



## 문제 2

> **🧚Q. 앞서 SQL Query의 오류를 해결한 진아는 기분 좋게 이번에는 포켓몬 데이터에서 타입별 평균 공격력이 60 이상인 타입만 조회하려는 쿼리를 작성하려고 했습니다. 하지만 이번에도 실수를 하여 쿼리문이 실행되지 않거나 잘못된 결과가 나오고 있는데, 쿼리에서 잘못된 부분이 무엇인지 설명하고, 올바르게 수정한 쿼리를 작성해보세요.**

~~~sql
SELECT type, AVG(attack) AS avg_attack
FROM pokemon
WHERE AVG(attack) >= 60
GROUP BY type;
~~~



~~~
이 쿼리에서 문제는 WHERE절에 AVG(attack)를 사용한 것이다.
AVG() 같은 집계 함수는 데이터를 그룹으로 묶은 뒤 계산되는 값이라서 WHERE에서 바로 사용할 수 없다. 그래서 타입별 평균 공격력이 60 이상인 경우를 찾으려면 GROUP BY로 먼저 묶고, 그 결과에 조건을 거는 HAVING을 사용해야 한다.

SELECT type, AVG(attack) AS avg_attack
FROM pokemon
GROUP BY type
HAVING AVG(attack) >= 60;

~~~



### 🎉 수고하셨습니다.
