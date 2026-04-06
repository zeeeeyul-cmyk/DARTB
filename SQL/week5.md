# SQL_BASIC 5주차 정규 과제 

📌SQL_BASIC 정규과제는 매주 정해진 분량의 `초보자를 위한 BigQuery(SQL) 입문` 강의를 듣고 간단한 문제를 풀면서 학습하는 것입니다. 이번주는 아래의 **SQL_Basic_5th_TIL**에 나열된 분량을 수강하고 `학습 목표`에 맞게 공부하시면 됩니다.

**5주차 과제는 문제 풀이를 중심으로**, 강의에서 제시된 예제 문제 중 **3 문제 이상을 선택하여 직접 풀어본 뒤**, 강의 영상의 풀이와 비교해 **틀린 부분, 맞은 부분, 새롭게 배운 개념**을 구체적으로 정리해주세요. (적어도 4문제는 정리해야 합니다.) 완성된 과제는 Gihub에 업로드하고, 링크를 스프레드시트 'SQL' 시트에 입력해 제출해주세요.

**👀(수행 인증샷은 필수입니다.)** 

<img width="1433" height="791" alt="Image" src="https://github.com/user-attachments/assets/54bf6250-6ba8-4680-833d-8802be927941" />
<img width="1433" height="791" alt="Image" src="https://github.com/user-attachments/assets/52e2cd6d-4a5e-44fc-89ae-943c4b3a228d" />
<img width="819" height="245" alt="Image" src="https://github.com/user-attachments/assets/1f96bfaa-55a1-4279-af78-994bd29cde52" />
<img width="1432" height="789" alt="Image" src="https://github.com/user-attachments/assets/9f3e449b-d979-46f2-9498-9eab88596738" />

## SQL_BASIC_5th

### 섹션 5. 데이터 탐색 - 변환

### 4-4. 날짜 및 시간 데이터 이해하기(2) (EXTRACT, DATETIME_TRUNC, PARSE_DATETIME, FROMAT_DATETIME)

### 4-5. 시간 데이터 연습문제 1~2번

### 4-5. 시간 데이터 연습문제 3~5번

### 4-6. 조건문 (CASE WHEN, IF)

### 4-7. 조건문 연습 문제

### 4-8. 정리

### 4-9. BigQuery 공식 문서 확인하는 법

(강의에서 연습문제가 많아서 따로 프로그래머스 문제 과제는 없습니다.)



## 🏁 강의 수강 (Study Schedule)

| 주차  | 공부 범위              | 완료 여부 |
| ----- | ---------------------- | --------- |
| 1주차 | 섹션 **1-1** ~ **2-2** | ✅         |
| 2주차 | 섹션 **2-3** ~ **2-5** | ✅         |
| 3주차 | 섹션 **2-6** ~ **3-3** | ✅         |
| 4주차 | 섹션 **3-4** ~ **4-4** | ✅         |
| 5주차 | 섹션 **4-4** ~ **4-9** | ✅         |
| 6주차 | 섹션 **5-1** ~ **5-7** | 🍽️         |
| 7주차 | 섹션 **6-1** ~ **6-6** | 🍽️         |

<br>



<!-- 여기까진 그대로 둬 주세요-->

---

# 4-4. 날짜 및 시간 데이터 이해하기(2) (EXTRACT, DATETIME_TRUNC, PARSE_DATETIME, FROMAT_DATETIME)

~~~
✅ 학습 목표 :
* 날짜 및 시간 데이터에 대해서 더 자세히 설명할 수 있다. 
* CURRENT_TIME, EXTRACT, DATETIME_TRUNC, PARSE_DATETIME, FROMAT_DATETIME 을 설명할 수 있다. 
~~~

1. CURRENT_TIME
현재 시간을 반환하는 함수

2. EXTRACT
날짜/시간 값에서 연,월, 일, 시, 분, 초 같은 특정 부분만 꺼내는 함수

3. DATETIME_TRUNC
날짜/시간 값을 특정 기준 단위까지 남기고 나머지는 잘라내는 함수
예를 들면 시, 일, 월 같은 단위 기준으로 맞춤

4. PARSE_DATETIME
문자열로 되어 있는 날짜/시간 데이터를 DATETIME 형식으로 변환하는 함수

5. FORMAT_DATETIME
DATETIME 값을 원하는 문자열 형식으로 바꿔주는 함수



# 4-6. 조건문(CASE WHEN, IF)

~~~
✅ 학습 목표 :
* 조건문 함수의 기능을 이해하고, 설명할 수 있다. 
~~~

조건문: 조건에 따른분기를 만듦/조건에 따라 값을 표시하고 싶을 때 사용
1. CASE WHEN
조건에 따라 다른 값을 보여주는 구문
CASE
    WHEN 조건1 THEN 결과1
    WHEN 조건2 THEN 결과2
    ELSE 결과3
END

2. IF
조건이 맞으면 한 값, 아니면 다른 값
IF(조건, 참일때값, 거짓일때값) AS 새로운 커럼의 이름

 # 4-5. 시간 데이터 연습문제 & 4-7. 조건문 연습 문제

~~~
✅ 학습 목표 :
* 4-5, 4-7 각각에서 두 문제 이상 (최소 4문제) 푼 내용 정리하기
~~~

문제 : 트레이너가 포켓몬을 포획한 날짜(catch_date)를 기준으로, 2023년 1월에 포획한 포켓몬의 수를 계산하는 문제

SELECT
  COUNT(*) AS pokemon_cnt
FROM basic.trainer_pokemon
WHERE catch_datetime BETWEEN '2023-01-01' AND '2023-01-31'

틀린 부분: catch_datetime이 UTC 기준인데 시간대 변환 없이 그대로 2023년 1월을 필터링했다.
맞은 부분: 포켓몬 수를 구하기 위해 COUNT를 사용한 점은 맞았다.
맞은 부분: 2023년 1월 데이터를 조건으로 걸어야 한다는 방향은 맞았다.
새롭게 배운 개념: TIMESTAMP는 시간대에 따라 날짜가 달라질 수 있어서, 한국 기준이면 변환 후 비교해야 한다.


문제 : 배틀이 일어난 날짜(battle_date)를 기준으로, 요일별로 배틀이 얼마나 자주 일어났는지 계산해주세요.

SELECT
  EXTRACT(DAYOFWEEK FROM battle_date) AS day_of_week,
  COUNT(DISTINCT id) AS battle_cnt
FROM basic.battle
GROUP BY day_of_week
ORDER BY day_of_week

틀린 부분: 처음에는 서브쿼리를 사용하지 않고 바로 요일을 추출해서 집계하려고 했다.
강의 풀이처럼 먼저 서브쿼리에서 day_of_week를 만든 뒤, 바깥 쿼리에서 집계하는 구조를 떠올리지 못했다.
맞은 부분: EXTRACT(DAYOFWEEK FROM battle_date)로 요일을 추출하려고 한 방향은 맞았다.
COUNT로 요일별 배틀 수를 구하려고 한 점도 맞았다.
새롭게 배운 개념: 서브쿼리를 사용하면 먼저 필요한 컬럼을 만든 뒤 바깥에서 집계할 수 있다.
복잡한 계산은 서브쿼리에서 미리 처리하면 메인 쿼리가 더 보기 쉬워진다.

문제: Speed 컬럼을 사용해 새로운 Speed_Category를 만들어주세요.

SELECT
  id,
  kor_name,
  IF(speed >= 70, "빠름", "느림") AS Speed_Category
FROM basic.pokemon

틀린 부분: Speed_Category를 만드는 것은 맞았지만, 정답 풀이처럼 speed 컬럼을 함께 보여주지 않아 결과를 바로 검증하기 어려웠다.
맞은 부분: speed >= 70 조건으로 빠름과 느림을 나눈 방향은 맞았다.
단일 조건이라 IF를 사용한 점도 맞았다.
새로운 컬럼 Speed_Category를 만든 점도 맞았다.
새롭게 배운 개념: 조건문으로 새 컬럼을 만들 때는 기준이 되는 원래 컬럼도 함께 보여주면 결과를 확인하기 쉽다.
IF(조건, 참일 때 값, 거짓일 때 값) 형태로 단일 조건 분기를 할 수 있다.


문제: 배틀에서 승자(winner_id)가 player1_id와 같으면 'Player 1 Wins', player2_id와 같으면 'Player 2 Wins', 그렇지 않으면 'Draw'로 결과가 나오게 해주세요
SELECT
  id,
  winner_id,
  player1_id,
  player2_id,
  CASE
    WHEN winner_id = player1_id THEN "Player 1 Wins",
    WHEN winner_id = player2_id THEN "Player 2 Wins",
    ELSE "Draw"
  END AS battle_result
FROM basic.battle

틀린 부분:
CASE WHEN 문에서 THEN 뒤 결과값 다음에 쉼표(,)를 넣었다.
CASE WHEN 안에서는 각 THEN 결과 뒤에 쉼표를 쓰지 않는다.
맞은 부분:
winner_id와 player1_id, player2_id를 비교해서 결과를 나누려는 방향은 맞았다.
여러 조건이므로 CASE WHEN을 사용한 점도 맞았다.
ELSE "Draw"로 나머지 경우를 처리하려 한 점도 맞았다.
새롭게 배운 개념:
CASE WHEN 문은 WHEN 조건 THEN 결과 형식으로 작성한다.
각 THEN 결과 뒤에는 쉼표를 넣지 않고, 마지막에 END로 마무리한다.


<br>

<br>

---

# 확인문제

## 문제 1

> **🧚Q. 광윤이는 카페 주문 로그 데이터(order_log)를 분석하여, '오전(0시-11시)'과 '오후(12시-23시)'의 주문 건수를 집계하려고 합니다. 광윤이가 작성한 다음 SQL 쿼리 중 문법적으로 틀렸거나 의도한 결과가 나오지 않는 것을 모두 골라보세요. (복수 선택 가능)**

~~~sql
1. SELECT 
   IF(EXTRACT(HOUR FROM order_time) < 12, '오전', '오후') AS time_type,
   COUNT(*)
   FROM order_log
   GROUP BY time_type;

2. SELECT 
   DATETIME_TRUNC(order_time, HOUR) AS truncated_hour,
   COUNT(*)
   FROM order_log
   WHERE order_time BETWEEN '2021-01-01' AND '2021-12-31'
   GROUP BY order_time;

3. SELECT 
   FORMAT_DATETIME(order_time, '%H') AS order_hour,
   COUNT(*)
   FROM order_log
   GROUP BY 1;

4. SELECT 
    CASE 
      WHEN EXTRACT(HOUR FROM order_time) BETWEEN 0 AND 11 THEN '오전'
      ELSE '오후'
    AS time_group,
    COUNT(*)
   FROM order_log
   GROUP BY time_group;
~~~

<!-- 틀린쿼리에 대한 오류의 원인도 같이 작성해주세요. 문제에서 제공된 order_time 컬럼은 DATETIME type의 데이터를 가지고 있다고 가정합니다. -->

~~~
정답: 2번, 4번
2번
오전/오후 집계가 아니라 시간대별(HOUR)로*자른 값을 구하고 있음
SELECT에서는 DATETIME_TRUNC(order_time, HOUR)를 썼는데, GROUP BY는 order_time으로 해서 집계 기준도 맞지 않음
그래서 의도한 오전/오후 주문 건수가 나오지 않음

4번
CASE문에 END가 빠져 있어서 문법 오류
원래는 END AS time_group이어야 함

~~~



## 문제 2

> **🧚Q. 예운이는 포켓몬 타입에 따라 설명을 부여하는 쿼리를 작성했습니다. type 1 컬럼의 값에 따라 조건을 분기했으며, 다음 SQL 쿼리를 실행했습니다.**

~~~sql
SELECT name,
       CASE 
         WHEN type1 = 'Fire' THEN 'Hot'
         WHEN type1 = 'Water' THEN 'Cool'
         ELSE 'Normal'
       END AS type_description
FROM pokemon;
~~~

> **다음 중 type_description의 결과가 'Normal'로 출력될 포켓몬은?**

| **name**   | **type1** |
| ---------- | --------- |
| Pikachu    | Electric  |
| Charmander | Fire      |
| Squirtle   | Water     |
| Bulbasaur  | Grass     |

<!-- 근거와 함께 답을 작성해주세요 -->

~~~
정답: Pikachu, Bulbasaur
이유
CASE문에서
Fire → 'Hot'
Water → 'Cool'
그 외 → 'Normal'
따라서 Electric인 Pikachu, Grass인 Bulbasaur는 모두 Normal로 출력됨
~~~



<br>

### 🎉 수고하셨습니다.
