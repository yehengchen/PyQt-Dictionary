# Basic Plot 사용법

## Matplotlib 기본 사용

```python
import matplotlib.pyplot as plt # matplotlib 패키지를 plt라 가정하고 사용
plt.figure(figsize=(6,4)) # 그래프의 크기를 지정하기 위해 사
plt.show() # 그래프를 출력하기 위해서 사용
```

그래프의 제목을 사용할 때 title을 사용한다.

```text
plt.title('Tetris')
```

x축 의 라벨을 사용할 때 **`plt.xlabel`**을 사용한다.

```text
plt.xlabel('episode')
```

y축 의 라벨을 사용할 때**`plt.ylabel`**을 사용한다.

```text
plt.ylabel('score')
```

**`plot`** 명령을 사용할 때 **`label`**옵션을 주고, **`plt.legend()`**를 사용하면 범례\(legend\)가 표시됩니다

**`plt.grid()`** : 그리드 적용하기 위하서 사용한다.

