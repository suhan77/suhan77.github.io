---
layout: post
title: Matplotlib
categories : pyds 
---

#1. 설치
**설치**
`$pip install matplotlib`
**import**
`import matplotlib.pyplot as plt`

**jupyter notebook에서는 과 함께 사용**
`%matplotlib inline` 


#2. 색깔, 마커, 선스타일
### 1) 색깔

| 문자열 | 약자 |
|--------|--------|
|    `blue`    | b       |
|    `green`   | g       |
|    `red`    | r       |
|    `yellow`    | y       |
|    `black`    | k       |

### 2) 마커
|마커 문자열    |  의미       |
|--------|--------|
|    `.`    | pint       |
|    `,`   | pixel   |
|    `o`    | circle       |
|    `v`    | triangle_down      |
|    `^`    | triangle_up       |
|    `1`    | tri_down        |
|D	|diamond marker|

### 3) 선스타일
| 선 스타일 문자열 | 의미 |
|--------|--------|
|   ` -`    | 	solid line       |
|   ` --  ` | dashed line       |
|   ` -.`    | dash-dot        |
|   ` : `   | dotted        |

#3. plot

```
plt.plot(x, y, fmt, data)
plt.xlim(0, 50) #그림의 범위
plt.ylim(0, 100)
plt.xtics([1, 2, 3, 4, 5]) #축위에 숫자or문자 표시
plt.ytics([-np.pi, 0, np.pi])
plt.grid(True) # 그리드 설정
plt.legend(loc=0) #범례 설정, 숫자로 위치 변경
plt.xlabel("x축 이름")
plt.ylabel("y축 이름")
plt.title("그래프 제목")
plt.show()
```

fmt는 `'ro--'` 이런식으로 쓰면 된다
plot을 여러개 그리고 `plt.show()`를 하면 그림이 겹쳐진다

```
f1 = plt.figure(figsize=(10, 2)) #그림 크기 설정
plt.subplot(221) #여러개의 그래프를 그릴때
```
위의 subplot은 2x2개의 그림중 1번째 그림이라는 뜻

#4. bar
```
plt.bar(x, y, xerr, alpha) # 막대그래프
plt.barh() # 가로로된 막대그래프
```

xerr : [ ]형식, 에러 바
alpha : 투명도 0~1 사이값

#5. stem
`plt.stem(x, y, fmt)`


#6. pie

```
labels = '개구리', '돼지', '개', '통나무'
sizes = [15, 30, 45, 10]
colors = ['yellowgreen', 'gold', 'lightskyblue', 'lightcoral']
explode = (0, 0.1, 0, 0)
plt.pie(sizes, explode=explode, labels=labels, colors=colors,
        autopct='%1.1f%%', shadow=True, startangle=90)
plt.axis('equal')
plt.show()
```

#7. histogram
`arrays, bins, patches = plt.hist(x, bins=10)`

#8. scatter
`plt.scatter(x, y, c, s)`

s는 점의 크기

c는 점의 색깔

#9. 컨투어 플롯

```
plt.contourf(XX, YY, ZZ, alpha=.75, cmap='jet') # 샐깔표시
plt.contour(XX, YY, ZZ, colors='black', linewidth=.5) #색깔없음
```

#10. 삼차원 서피스 플롯

```
from mpl_toolkits.mplot3d import Axes3D
fig = plt.figure()
ax = Axes3D(fig)
ax.plot_surface(XX, YY, ZZ, rstride=1, cstride=1, cmap='hot')
plt.show()
```
