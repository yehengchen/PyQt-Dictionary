# 학습을 위한 데이터 전처리

데이터 전처리에 Numpy를 사용해서 학습 input으로 넣기위한 형태로 데이터를 만들 수 있다.

```text
state = np.reshape(state, [1,224])
image_list = np.expand_dims(image_list, axis=3)
```



