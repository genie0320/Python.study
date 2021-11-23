특정칼럼의 데이터만 뽑아오기
````py
sorted(list(set(변수1['_칼럼이름_'])))
````

특정칼럼의 데이터갯수 확인
````py
len(list(set(변수1['_칼럼이름_'])))
````

특정 칼럼값에 맞는 정보만 sort 하기
- *원본데이터를 훼손하지 않기 위해서 가급적 단계별로 새로운 변수를 선언해주는 것이 좋다.*
````py
_변수2_ = 변수1[변수1['_칼럼이름_']==_찾을값_]
_변수2_ # 해당 값을 출력하라는 뜻
````

필요없는 칼럼 제거
````py
_변수2_ = _변수2_.drop(columns={'_칼럼명_'})
_변수2_
````

#### 그룹으로 만든 값에서 데이터 인덱싱하기
* 2개의 기준에 맞춰 각기 그룹을 맺어서 각 평균을 내서 새로운변수에 담아라.
* 그 새로운변수의 값 중 특정 칼럼의 값이 있는 것을 따로 떼서 변수명4에 담아라.
````py
line = '2호선'
_새로운변수_ = _변수명_.groupby(['_칼럼명_','_칼럼명_']).mean().reset_index()
_변수명4_ = _새로운변수_[_새로운변수_['_칼럼명_']==_비교값_]
_변수명4_
````

### 새로운 테이블을 생성해주기
* 새로운 테이블을 만들고,
* 다른 테이블의 데이터를 특정조건에 따라 새로운 테이블의 열로 넣기.
* '지하철역' 열로 인덱스 새로 세팅해주기.
````py
_테이블1_ = pd.DataFrame()
_테이블1_['지하철역'] = _다른테이블명_['지하철역']

# 본래 테이블의 데이터 특성(홀수행'승차', 짝수행'하차')의 특성을 고려하여 새로운 테이블의 데이터를 구성.
for i in range(int((len(metro_recent.columns)-3)/2)):
    metro_get_on[metro_st_line2.columns[3+2*i]] = metro_st_line2[metro_st_line2.columns[3+2*i]]
metro_get_on = metro_get_on.set_index('지하철역')
````

* 데이터프레임을 하나 새로 만들되, 인덱스는 '지하철역'으로 하기
* 데이터프레임에 ~라는 열을 만들고, 각 역마다 승차인원을 평균을 내서(즉, 열값의 평균을 내서) 넣어주기.
````py
# 역 별 평균 승하차 인원을 구한 후 정수로 형 변환하여 데이터프레임으로 저장
df = pd.DataFrame(index = metro_st_line2['지하철역'])
df['평균 승차 인원 수'] = metro_get_on.mean(axis=1).astype(int)
df['평균 하차 인원 수'] = metro_get_off.mean(axis=1).astype(int)
df
````

### TOP10 골라내기
* 평균승차인원수의 값에 따라 정렬하되, 내림차순으로 정리해서, (위로부터) 10개만 가지고 와라.
````py
top10_on = df.sort_values(by='평균 승차 인원 수', ascending=False).head(10)

````


# TODOS
- [ ] metplotlib에서 한글폰트 적용하는 방법(not local)
