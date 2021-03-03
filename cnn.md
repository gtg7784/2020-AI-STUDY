---
marp: true
style: |
  * {
    font-size: 22px;
  }
  img[alt~="center"] {
    display: block;
    margin: 0 auto;
  }
---

# CNN 심화 두번째 이야기

## Convolutional Neural Network 두번째 이야기

2020 겨울방학 인공지능 특강

---

# Regularization


![width:600px](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FTd9EY%2FbtqxJx5IVHD%2F5gVSXVPgzNG85E49PLvYw1%2Fimg.png)

bias -> 데이터와 얼마나 멀어졌는지에 대한 값 -> 이게 높으면 Under Fitting
variance -> 예측된 값들이 얼마나 떨어져 있는가 -> 이게 높으면 Over Fitting

training accuracy를 낮춤으로써 testing accuracy를 높이고자 하는 것 

---

# Normalization

![width:400px](https://i0.wp.com/hleecaster.com/wp-content/uploads/2019/12/z-score.png?fit=1024%2C768)

모든 데이터 포인트가 동일한 정도의 스케일(중요도)로 반영되도록 해주는 게 정규화(Normalization)의 목표이다.
사진은 어떤 데이터셋을 Min-Max 정규화를 통해 데이터를 다시 만든 것이다.

---

# Min-Max Norm

최소-최대 정규화는 데이터를 정규화하는 가장 일반적인 방법이다. 모든 feature에 대해 각각의 최소값 0, 최대값 1로, 그리고 다른 값들은 0과 1 사이의 값으로 변환하는 거다.

```py
def min_max_normalize(lst):
    normalized = []
    
    for value in lst:
        normalized_num = (value - min(lst)) / (max(lst) - min(lst))
        normalized.append(normalized_num)
    
    return normalized
```

---

# Min-Max Norm

예를 들어, 100개의 값이 있는데 그 중 99개는 0과 40 사이에 있고, 나머지 하나가 100이면 어떨까. 그러면 99개의 값이 모두 0부터 0.4 사이의 값으로 변환된다.

![width:400px](https://i0.wp.com/hleecaster.com/wp-content/uploads/2019/12/z-score.png?fit=1024%2C768)

위 그림을 보면 y축에서는 정규화가 효과적으로 적용되었으나 x축에서는 여전히 문제가 있다. 이 상태로 데이터의 점들을 비교한다면, y축의 영향이 지배적일 수밖에 없다.

이러한 단점을 보완하려면 Z-점수 정규화를 고려해봐야 한다.

---

# Z-Score Norm

Z-점수 정규화는 이상치(outlier) 문제를 피하는 데이터 정규화 전략이다.

```
(X - 평균) / 표준편차
```

만약 feature의 값이 평균과 일치하면 0으로 정규화되겠지만, 평균보다 작으면 음수, 평균보다 크면 양수로 나타난다. 이 때 계산되는 음수와 양수의 크기는 그 feature의 표준편차에 의해 결정되는 거다. 그래서 만약 데이터의 표준편차가 크면(값이 넓게 퍼져있으면) 정규화되는 값이 0에 가까워진다.

```py
def z_score_normalize(lst):
    normalized = []
    for value in lst:
        normalized_num = (value - np.mean(lst)) / np.std(lst)
        normalized.append(normalized_num)
    return normalized
```

---

# Z-Score Norm

![width:500px](https://cdn.shortpixel.ai/client/q_glossy,ret_img,w_1280/http://hleecaster.com/wp-content/uploads/2019/12/z-score.png)

데이터가 여전히 찌그러져 보이긴 하지만, 그래도 거의 모든 점들이 x축과 y축에서 -2와 2 사이에 있다. 이제 어느정도 비슷한 스케일로 나타낸 셈이다. 여전히 x축에 5가 넘는 녀석 하나가 있어서 정확히 동일하진 않지만, 그래도 최소-최대 정규화에서 나타난 문제는 해결했다고 볼 수 있다.

---

# Dropout

![](https://t1.daumcdn.net/cfile/tistory/9927224A5AD9DCC90E)

왼쪽 그림과 같은 모델에서, 몊개의 연겷을 끊어서 몇개의 노드를 죽이고 남은 노드를 통해서만 훈련을 하는 것

이때, 죽이는 노드는 랜덤하게 선택함

쉽게 말해 각 노드들을 어떤 전문가라고 생각해본다면 랜덤하게 몇명은 쉬게하고 나머지만 일하게 합니다. 

그리고 마지막에는 모든 전문가들을 총 동원해서 예측을 하게 합니다.

---

# Mnist with Pooling, Dropout

---

# 숙제

1. 제공해준 데이터셋을 분류 할 수 있는, CNN 모델을 만들어 오세요!

   (Noise Mnist Dataset)

---

# 수고했습니다.
