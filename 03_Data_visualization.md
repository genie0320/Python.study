## 그래프그리기 
### 한글폰트를 사용하고 싶은 경우의 세팅
* metplotlib 에서 폰트매니저를 들여와야 함.
````py
import matplotlib.font_manager as fm

font_dirs = ['/usr/share/fonts/truetype/nanum', ] 
font_files = fm.findSystemFonts(fontpaths=font_dirs)

for font_file in font_files:
    fm.fontManager.addfont(font_file)
````

### 어떻게 관점으로 시각화할 것인지 결정하기
* 변수2의 데이터에서 _컬럼명1_의 데이터로 그룹을 묶어, 각 평균을 낸 다음 새 인덱스를 부여해라._이때 기존의 인덱스는 버려지지 않고 데이터의 첫번째 칼럼으로 넘어가게 된다. 그럴 필요가 없다면 drop=true 옵션을 주면 된다._
* 필요없는 칼럼을 제외하고, 데이터를 새로운 기준으로 인덱스를 설정해라.
* 그걸로 그래프를 그리되, 모든 '열'의 평균을 구하여 오름차순으로 그려내라.
````py
_변수3_ = _변수2_.groupby(['_컬럼명_']).mean().reset_index()
_변수3_ = _변수3_.drop(columns='_칼럼명_').set_index('_인덱스로 설정할 컬럼명_')
_변수3_ = _변수3_.mean(axis=1).sort_values(ascending=False)

# 참고로... groupby는 다음과 같이 여러개를 컬럼을 넣을 수도 있다.
_변수명_ = _다른변수명_.groupby(['_칼럼명_','_갈럼명2_']).mean().reset_index()
````

### 그래프 그리기
* 그래프의 크기는 X:20, Y:10 이고
* 폰트는 나눔고딕이며,
* 마이너스값이 있으면 보여주지 말고!
* 바 그래프로 보여주라.
````py
plt.figure(figsize=(20,10))
plt.rc('font', family="NanumBarunGothic")
plt.rcParams['axes.unicode_minus'] = False

metro_line.plot(kind=('bar'))
plt.show()
````

* 바그래프로 보여주는데... X를 탑10값으로, Y를 인원수로설정해라.
* 그리고 첫번째[0] 데이터의 값표시는 빨간색으로 해라.
* enumerate, range 함수는... 왠지 js의 map 같은 함수 같다.

````py
plt.bar(top10_on.index, top10_on['평균 승차 인원 수'])
for x, y in enumerate(list(top10_on['평균 승차 인원 수'])):
    if x == 0:
        plt.annotate(y, (x-0.15, y), color = 'red')
    else:
        plt.annotate(y, (x-0.15, y))

plt.title('2021년 6월 평균 승차 인원 수 Top10')
plt.show()
````
````py
````