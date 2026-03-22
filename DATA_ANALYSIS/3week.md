# 데이터분석 3주차 정규과제

📌데이터분석 정규과제는 매주 정해진 분량의 『*혼자 공부하는 데이터 분석 with 파이썬*』 을 읽고 학습하는 것입니다. 이번 주는 아래의 **DataAnalysis_3rd_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=CE3_InvbmLY&list=PLVsNizTWUw7FGzSRCkQrPEEe-ljVXgS7k&index=6
https://www.youtube.com/watch?v=hhbzUEQWdTg&list=PLVsNizTWUw7FGzSRCkQrPEEe-ljVXgS7k&index=7
-->


## DataAnalysis_3rd_TIL

### 3장 데이터 정제하기
#### 01. 불필요한 데이터 삭제하기
#### 02. 잘못된 데이터 수정하기


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~81    | ✅         |
| 2주차 | p.84~151   | ✅         |
| 3주차 | p.154~219  | ✅         |
| 4주차 | p.222~279 | 🍽️         |
| 5주차 | p.282~325 | 🍽️         |
| 6주차 | p.328~379 | 🍽️         |
| 7주차 | p.382~430 | 🍽️         |

<br>

<!-- 여기까진 그대로 둬 주세요-->


# 1️⃣ 개념 정리 

## 01. 불필요한 데이터 삭제하기

# 01. 불필요한 데이터 삭제하기

열 삭제 : loc[:, '시작열':'끝열'] 로 범위 선택, drop('열이름', axis=1) 로 직접 삭제, 불리언 배열을 loc에 넘겨서 원하는 열만 선택하는 세 가지 방법이 있다.

dropna(axis=1) : NaN이 있는 열을 삭제한다. how='all'이면 전체가 NaN인 열만, 기본값은 NaN이 하나라도 있으면 삭제한다.

행 삭제 : drop([인덱스번호]) 로 특정 행을 삭제한다.

행 필터링 : df[df['열'] == 값] 처럼 불리언 배열을 [] 안에 넣으면 조건에 맞는 행만 남는다.

duplicated() : 중복 여부를 True/False로 반환한다. 기본값은 처음 행은 False, 이후 중복만 True이고, keep=False를 주면 중복된 행 전체를 True로 표시한다.

groupby().sum() : 중복 행 삭제 전에 수치 데이터를 먼저 합산해 데이터 손실을 막는다.

## 02. 잘못된 데이터 수정하기

info()는 데이터프레임의 전체 구조를 한눈에 확인한다. 전체 행 개수, 열 개수, 각 열의 Non-Null 개수, 데이터 타입, 메모리 사용량을 보여준다.

isna().sum() 으로 열별 NaN 개수를 숫자로 확인할 수 있다. NaN은 None을 넣어도, np.nan을 넣어도 동일하게 저장된다.

fillna() 는 NaN을 특정 값으로 채운다. 전체에 일괄 적용하거나, 특정 열만 지정하거나, 딕셔너리로 열마다 다른 값을 채울 수 있다.

replace() 는 NaN뿐 아니라 특정 값 자체를 다른 값으로 교체할 때 쓴다. fillna()보다 범용적이며, 리스트나 딕셔너리로 여러 값을 한번에 처리할 수 있다.

replace()에 regex=True를 주면 정규 표현식 패턴으로 값을 찾아 교체할 수 있다. \d는 숫자 한 글자, \d{2}는 숫자 두 글자, .은 임의의 문자 한 글자, .*은 아무 문자나 0개 이상을 의미한다. ()로 묶으면 그룹이 되고, \1 \2로 해당 그룹을 다시 참조할 수 있다.

str.contains() 는 특정 패턴이 포함된 행을 찾아 불리언 배열로 반환한다. \D(숫자가 아닌 문자)처럼 정규 표현식도 사용 가능하고, na=True를 주면 NaN인 셀도 True로 처리한다.


# 2️⃣ 수행 인증

<img width="1128" height="620" alt="Image" src="https://github.com/user-attachments/assets/921fb723-ec69-402e-8175-69cc33a4d7cc" />

<img width="1128" height="620" alt="Image" src="https://github.com/user-attachments/assets/31bb4770-4a4f-4899-a5ac-0366c22d2954" />

<img width="1128" height="620" alt="Image" src="https://github.com/user-attachments/assets/711459e0-ade8-4785-adc7-7aae4c0c9f84" />

<img width="1128" height="620" alt="Image" src="https://github.com/user-attachments/assets/d327298b-1ac6-4f20-8d62-9d2eb12f9ba0" />

<img width="1128" height="620" alt="Image" src="https://github.com/user-attachments/assets/1bff928c-27d6-40ff-af9f-dc160040cf48" />

<img width="1128" height="620" alt="Image" src="https://github.com/user-attachments/assets/7790089f-c62f-426c-882a-e8da56e92f40" />

<img width="1128" height="620" alt="Image" src="https://github.com/user-attachments/assets/f1c77baa-503f-4707-81e7-e5bc76ab2744" />

<img width="1440" height="767" alt="Image" src="https://github.com/user-attachments/assets/111a2e0a-58c8-4ac1-bc33-ca501f0d8043" />


<br>
<br>

# 3️⃣ 확인 문제

## 문제 1.

> **🧚Q. 다음 두 데이터프레임 df1, df2를 합쳐서 데이터프레임 df3를 만들려고 합니다.**  
> 적절한 판다스 명령을 선택해주세요.

<table>
<tr>

<td>

### df1

| index | col1 | col2 |
|-------|------|------|
| 0     | x    | 5    |
| 1     | y    | 6    |
| 2     | z    | 7    |

</td>

<td>

### df2

| index | col3 | col4 |
|-------|------|------|
| 0     | x    | 50   |
| 1     | y    | 60   |
| 2     | w    | 70   |

</td>

<td align="center" valign="middle">

<h2> ➜ </h2>

</td>

<td>

### df3 (결과)

| index | col1 | col2 | col3 | col4 |
|-------|------|------|------|------|
| 0     | x    | 5.0  | x    | 50.0 |
| 1     | y    | 6.0  | y    | 60.0 |
| 2     | z    | 7.0  | NaN  | NaN  |
| 3     | NaN  | NaN  | w    | 70.0 |

</td>

</tr>
</table>

```
1️⃣ pd.merge(df1, df2)
2️⃣ pd.merge(df1, df2, how='left')
3️⃣ pd.merge(df1, df2, left_on='col1', right_on='col3', how='outer')
4️⃣ pd.merge(df1, df2, left_on='col1', right_on='col3', how='inner')
```

```
정답 : 3️⃣ pd.merge(df1, df2, left_on='col1', right_on='col3', how='outer')

df1의 col1과 df2의 col3을 기준으로 매칭해야 하므로 left_on, right_on을 사용한다.
결과에 z와 w가 모두 남아있고 없는 값은 NaN으로 채워졌으므로 outer join이 필요하다.
```



### 🎉 수고하셨습니다.
