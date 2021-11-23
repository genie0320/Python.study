# 1. 데이터 불러오기

### 필요한 모듈을 세팅
- numpy : 데이터처리
- pandas : 데이터처리
- metplotlib : 그래프 그리는 도구
````py
import numpy as np 
import pandas as pd 
import matplotlib.pyplot as plt
````

### 사용할 데이터 로딩
경로와 인코딩방식을 결정하여 변수에 저장
````py
_변수1_ = pd.read_csv("./data path.csv", encoding = '_인코딩방식_')
````

데이터개요 살피기 (상위 5개만 로딩하여 어떤 모양인지 파악)
````py
_변수1_.head()
````

데이터프레임정보 확인(데이터의 무결성, 자료형태를 파악)
* 전체 데이터의 크기와 행/열의 크기가 어떤 의미를 가지는 것인지 생각해야 함.
````py
변수1.info()
````
