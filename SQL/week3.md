# SQL_BASIC 3주차 정규 과제 

📌SQL_BASIC 정규과제는 매주 정해진 분량의 `초보자를 위한 BigQuery(SQL) 입문` 강의를 듣고 간단한 문제를 풀면서 학습하는 것입니다. 이번주는 아래의 **SQL_Basic_3rd_TIL**에 나열된 분량을 수강하고 `학습 목표`에 맞게 공부하시면 됩니다.

**3주차 과제는 문제 풀이를 중심으로**, 강의에서 제시된 예제 문제 중 **7 문제 이상을 선택하여 직접 풀어본 뒤**, 강의 영상의 풀이와 비교해 **틀린 부분, 맞은 부분, 새롭게 배운 개념**을 구체적으로 정리해주세요. (적어도 3문제는 정리해야 합니다.) 완성된 과제는 Gihub에 업로드하고, 링크를 스프레드시트 'SQL' 시트에 입력해 제출해주세요.

**👀(수행 인증샷은 필수입니다.)** 

## SQL_BASIC_3rd

### 섹션 3. 데이터 탐색 - 조건, 추출, 요약

### 2-6. 연습문제 1~3번

### 2-6. 연습문제 7~9번

### 2-6. 연습문제 10~12번

### 2-6. 연습문제 13~17번

### 2-7. 정리 

### 2-8. 새로운 집계함수



## 섹션 4. 쿼리 잘 작성하기, 쿼리 작성 템플릿 및 오류를 잘 디버깅하기

### 3-1. INTRO

### 3-2. SQL 쿼리 작성하는 흐름

### 3-3. 쿼리 작성 템플릿과 생산성 도구 



## 🏁 강의 수강 (Study Schedule)

| 주차  | 공부 범위              | 완료 여부 |
| ----- | ---------------------- | --------- |
| 1주차 | 섹션 **1-1** ~ **2-2** | ✅         |
| 2주차 | 섹션 **2-3** ~ **2-5** | ✅         |
| 3주차 | 섹션 **2-6** ~ **3-3** | ✅         |
| 4주차 | 섹션 **3-4** ~ **4-4** | 🍽️         |
| 5주차 | 섹션 **4-4** ~ **4-9** | 🍽️         |
| 6주차 | 섹션 **5-1** ~ **5-7** | 🍽️         |
| 7주차 | 섹션 **6-1** ~ **6-6** | 🍽️         |

<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 개념정리

## 2-6. 연습문제

~~~
✅ 학습 목표 :
* 연습문제(7문제 이상) 푼 것들 정리하기
~~~
<답안 필사했습니다>
#1
select
  count(id) as ct
from basic.pokemon
where
  type2 is null
  or (type1 = "Fire")
 
 
#2
select
  type1,
  count(id) as pokemon_cnt
from basic.pokemon
where
  type2 is null
group by
  type1
order by
  pokemon_cnt desc
 
 
#4
select
  is_legendary,
  count(id) as pokemon_cnt
from basic.pokemon
group by
  is_legendary
 
 
#5
select
  name,
  count(name) as trainer_cnt
from basic.trainer
group by
  name
having
  trainer_cnt >= 2
 
 
#7
select
from basic.trainer
where
  (name = "Ireis")
  or (name = "Cynthia")
  or (name = "whitney")
 
 
#8
select
  count(id) as pokemon_cnt
from basic.pokemon
 
 
#10
select
  *
from basic.pokemon
where
  type2 is not null
 
 
#11
select
  type1,
  count(id) as pokemon_cnt
from basic.pokemon
where
  type2 is not null
group by
  type1
 
 
#13
select
  kor_name
from basic.pokemon
where
  kor_name like "%파%"
 
 
#14
select
  count(id) as trainer_cnt
from basic.trainer
where
  badge_count >= 6
 
 
#15
select
  trainer_id,
  count(pokemon_id) as pokemon_cnt
from basic.trainer_pokemon
group by
  trainer_id
 
 
#16
select
  trainer_id,
  count(pokemon_id) as pokemon_cnt
from basic.trainer_pokemon
where
  status = "Released"
group by
  trainer_id
order by
  pokemon_cnt
limit 1
 
 
#17
select
  countif(trainer_id=17) as pokemon_cnt
from basic.trainer_pokemon
where
  status = "Released"
group by
  trainer_id
order by
  pokemon_cnt desc
limit 1

<오답노트입니다!>
-- ============================================================
-- 문제 13. 이름에 "파"가 포함된 포켓몬의 한국어 이름 조회
-- ============================================================

-- [내가 처음 작성한 쿼리]
SELECT
  kor_name
FROM basic.pokemon
WHERE
  kor_name LIKE "파%"


  [틀린 부분]
  - LIKE "파%" 로 쓰면 "파"로 시작하는 포켓몬만 나온다.
    "파"가 중간이나 끝에 오는 경우는 빠짐.
    앞뒤로 모두 %를 붙여야 포함 여부를 전체에서 검색한다.

  [맞은 부분]
  - LIKE 연산자와 % 와일드카드 사용 자체는 맞다.
  - 조회 컬럼과 테이블 지정도 정확하다.

  [새롭게 배운 점]
  - "포함"과 "시작"의 차이를 LIKE 패턴으로 명확히 구분하게 됐다.
    시작: LIKE "파%"
    끝:   LIKE "%파"
    포함: LIKE "%파%"
    습관적으로 "파%"를 써버린 게 실수였다.


-- [정답]
SELECT
  kor_name
FROM basic.pokemon
WHERE
  kor_name LIKE "%파%"


-- ============================================================
-- 문제 15. 트레이너별 보유 포켓몬 수 조회
-- ============================================================

-- [내가 처음 작성한 쿼리]
SELECT
  trainer_id,
  count(pokemon_id) as pokemon_cnt
FROM basic.trainer_pokemon
GROUP BY
  trainer_id
ORDER BY
  trainer_id          -- pokemon_cnt가 아니라 trainer_id 기준으로 정렬해버림


--[틀린 부분]
  - 결과 보기 편하게 정렬을 추가하려다 pokemon_cnt가 아닌 trainer_id로 걸었다.
    강의 정답은 ORDER BY 없이 단순 GROUP BY 집계만 하는 쿼리였음.
    요구사항에 없는 정렬을 추가하고 기준도 잘못 잡은 이중 실수.

  [맞은 부분]
  - GROUP BY trainer_id 집계 구조는 완전히 맞다.
  - COUNT(pokemon_id), 별칭 pokemon_cnt 모두 정확하다.

  [새롭게 배운 점]
  - "조회"만 요구하는 문제에 습관적으로 ORDER BY를 추가하다 보면
    의도와 다른 기준으로 걸릴 수 있다.
    문제 요구사항을 먼저 정확히 읽고 필요한 절만 추가하는 습관이 중요하다.


-- [정답]
SELECT
  trainer_id,
  count(pokemon_id) as pokemon_cnt
FROM basic.trainer_pokemon
GROUP BY
  trainer_id


-- ============================================================
-- 문제 16. Released 상태 포켓몬이 가장 적은 트레이너 1명 조회
-- ============================================================

-- [내가 처음 작성한 쿼리]
SELECT
  trainer_id,
  count(pokemon_id) as pokemon_cnt
FROM basic.trainer_pokemon
WHERE
  status = "Released"
GROUP BY
  trainer_id
HAVING
  pokemon_cnt = MIN(pokemon_cnt)   -- HAVING 안에서 MIN(집계값)을 걸려고 시도


--[틀린 부분]
  - HAVING 절 안에서 MIN(pokemon_cnt)처럼 집계 결과에 다시 집계를 거는 건
    BigQuery를 포함한 대부분의 SQL에서 지원하지 않는다. 실행 시 오류 발생.
    서브쿼리를 쓰거나 그냥 ORDER BY + LIMIT 1로 해결하는 게 맞다.
  - "최솟값인 행 1개"를 HAVING으로 풀려고 한 접근 자체가 과도했다.

  [맞은 부분]
  - WHERE status = "Released" 필터 조건은 정확하다.
  - GROUP BY 집계 구조도 맞고,
    HAVING으로 집계 후 필터링하려는 방향 자체는 맞다.
    중첩 집계가 안 된다는 제약을 놓친 것.

  [새롭게 배운 점]
  - 최솟값/최댓값 레코드 1건을 뽑을 때는 HAVING보다 ORDER BY + LIMIT이
    훨씬 간결하고 범용적이다.
  - HAVING은 그룹 필터링용이고, 다른 그룹의 집계값과 비교하려면
    서브쿼리 없이는 불가능하다는 점을 다시 확인했다.


-- [정답]
SELECT
  trainer_id,
  count(pokemon_id) as pokemon_cnt
FROM basic.trainer_pokemon
WHERE
  status = "Released"
GROUP BY
  trainer_id
ORDER BY
  pokemon_cnt
LIMIT 1



## 2-8. 새로운 집계함수

~~~
✅ 학습 목표 :
* SQL 쿼리 구조를 이해할 수 있다. 
* SELECT, FROM, WHERE을 활용하는 방법을 설명할 수 있다. 
~~~

COUNT : 행 수 집계
SUM : 합계
AVG : 평균
MIN / MAX : 최솟값 / 최댓값
COUNTIF(조건) : 조건을 만족하는 행 수만 집계 (BigQuery 전용)



## 3-2. 쿼리를 작성하는 흐름

~~~
✅ 학습 목표 :
* 쿼리를 작성하는 흐름을 설명할 수 있다.
~~~

원하는 결과물을 먼저 머릿속으로 그린다
어떤 테이블에서 데이터를 가져올지 결정 → FROM
필요한 조건으로 필터링 → WHERE
그룹화가 필요하면 → GROUP BY
출력할 컬럼 선택 → SELECT


쿼리는 작성 순서(SELECT → FROM → WHERE)와 실제 실행 순서(FROM → WHERE → SELECT)가 다르다.



## 3-3. 쿼리 작성 템플릿과 생산성 도구

~~~
✅ 학습 목표 :
* 생산성 도구를 만들 수 있다.
~~~




<br>
<br>

---

# 2️⃣ 학습 인증란





<br><br>



---

# 3️⃣ 확인문제

## 문제 1

> **🧚Q. Q. 포켓몬 연구에 흥미를 느낀 혜인은 각 타입(type1)별 평균 공격력(attack)을 비교해보고 싶었습니다.**
>
> 그래서 다음과 같은 필요한 정보를 미리 정리해보았습니다. 

~~~
조건 : attack이 50 이상인 포켓몬만 포함
보고 싶은 컬럼 : type1
집계 내용 : 각 type1 별 평균 공격력
정렬 기준 : 평균 공격력을 기준으로 내림차순 정렬
~~~

> **이 목표를 바탕으로 혜인은 아래와 같은 쿼리를 작성했지만, 일부 SQL 문법 요소를 빼먹었습니다. 비어 있는 부분인 ㄱ, ㄴ, ㄷ, ㄹ 에 들어갈 알맞은 SQL 구문을 채워보세요:**

~~~sql
SELECT type1, (ㄱ)
FROM pokemon
(ㄴ) attack >= 50
(ㄷ) type1
ORDER BY (ㄱ) (ㄹ);
~~~



~~~
ㄱ: AVG(attack)
ㄴ: WHERE
ㄷ: GROUP BY
ㄹ: DESC
~~~



### 🎉 수고하셨습니다.