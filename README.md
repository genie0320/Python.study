# Python.study
## 3. Metplotlib : 데이터시각화
### Bar : axes[0]
axes[0].bar(x, y)
### Histogram : axes[1]
axes[1].hist(z, bins = 50)
* bins = 막대의 갯수

### 꽁수
matplotlib 의 pyplot으로 그래프를 그릴 때, 한글을 지원하는 나눔바른고딕 폰트로 바꾸기.
````py
import matplotlib.font_manager as fm
fname='./NanumBarunGothic.ttf'
font = fm.FontProperties(fname = fname).get_name()
plt.rcParams["font.family"] = font
````

# 소감 : 
NumPy, pandas, Metplotlib 는, 적어도 지금으로선 서비스기획 단계에서 그닥 쓸모를 발견하기가 힘들다. 
- pandas를 통한 데이터 클리닝은 엑셀의 파워쿼리만 이용해도 충분하고(뭐 내가 쿠팡주문시스템 급의 거대한 데이터를 가공할 일이 생기면 또 몰라도), 
- NumPy를 통한 계산은 이번에 파워BI를 통해서 처리해볼 기회가 있었는데, 엑셀을 다뤘던 내게는 훨씬 친숙하고 무엇보다 말이 되었다.
- Metplotlib를 통한 데이터시각화는... 이건 개발자의 영역이지 기획자의 영역은 아닌거 같다. 

그렇지만 알아둬서 나쁠 것은 세상에 없으니, 일단 이번에는 이정도 기초중의 기초를 익힌 것에 만족. 하지만 아나콘다를 설치하면서... 현타가 오고 있다.(211121작성)