---
description: Python을 사용한 Multi-Processing에 관해 설명드립니다.
---

# Multi-Processing



{% code-tabs %}
{% code-tabs-item title="Multi-processing 기본 예제" %}
```python
import multiprocessing,time
def count(d):
    while(d<=15):
        print(d)
        time.sleep(1)
        d += 1
if __name__ == '__main__':
    p1 = multiprocessing.Process(target=count,args=(3,)) # Thread 생성법과 유사
    p2 = multiprocessing.Process(target=count,args=(3,))
    p1.start()
    time.sleep(2)
    p2.start()
```
{% endcode-tabs-item %}
{% endcode-tabs %}



