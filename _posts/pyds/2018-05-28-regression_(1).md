---
layout: post
title: Regression (1)
categories : pyds 
---

# 1. 사용할 패키지
**imoprt**

`import statsmodels.api as sm`

statsmodels은 파이썬에서 활용 가능한 통계 패키지 이다.

# 2. 회귀분석 기본 개념


# 3. 상관관계

`dfX0.corr()` 를 이용하면 쉽게 알 수 있다. (표로 확인 가능)


히트맵 만들기
```
sns.heatmap(dfX0.corr())
plt.show()
```

# 4. VIF

회분석에서 다중공선성을 없애는 방법.

`variance_inflation_factor` 을 이용하면 된다



```
from statsmodels.stats.outliers_influence import variance_inflation_factor

vif = pd.DataFrame()
vif["VIF Factor"] = [variance_inflation_factor(dfX0.values, i) for i in range(dfX0.shape[1])]
vif["features"] = dfX0.columns
vif
```



# 5. bias augmentation

회귀분석을 하기 앞서, 상수항을 만들어 주기 위해 맨 앞줄에 1이 필요하다.


`X = sm.add_constant(X)`

# 6. regressions

```
model = sm.OLS.from_formula(' y ~ x1 + x2 + x1:x2', data=data)
model_fit = model.fit()
print(model_fit.summary())
```

#### 1) 변수 사용법
`+` 변수 추가
`:` 두 변수간 상관관계가 있을 때 사용

`scale()` 정규화, 평균제거, 표준편차로 스케일링
`center()` 평균 제거
`I()` 연산 가능, `**`을 이용해 제곱 가능, 다항선형회귀 가능
`C()` 카테고리 값
`np.log()` 함수 사용 가능
`-1` 상수항 제거


#### 2) summary 보기
Adj. R-squared : 0~1 사이 값으로 1에 가까울 수록 정확도가 높다
F-statistic : F 통계량 
Prob (F-statistic) : 
coef : 회귀모형의 모수(parameter) 
std err : 표준 에러
t : t 통계량
P>|t| : p
[0.025  0.975] : 2.5% ~ 97.5% 사이 값