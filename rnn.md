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

# RNN & LSTM

## Recursive Nueral Network & Long Short Term Memory

2020 겨울방학 인공지능 특강

---

# RNN

RNN은 인공지능하면 가장 먼저 떠올릴수 있는 자연어처리(NLP)를 할 때 가장 많이 사용하는 알고리즘이다.

여러분들이 작년에 했던 대통령님 목소리를 만드는 모델인 tacotron에도 RNN(LSTM)이 사용되었다.

---

# RNN

![width:600px](https://stanford.edu/~shervine/teaching/cs-230/illustrations/architecture-rnn-ltr.png?9ea4417fc145b9346a3e288801dbdfdc)

한국어로 하면 순환신경망이라 하는 RNN은 시퀀스 데이터를 모델링하기 위해 만들어진 신경망이다.

기존의 CNN 또는 다양한 신경망에는 없는 RNN만의 특징이 있는데, 이는 hidden state이다.

---

# 시퀀스 데이터란?

---

# hidden state

---
