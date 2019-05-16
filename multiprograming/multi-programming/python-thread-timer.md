---
description: 쓰레드를 사용해서 타이머를 만듦
---

# Python Thread timer

기초적인 파이썬 타이머 호출 방법

{% code-tabs %}
{% code-tabs-item title="Python-Timer" %}
```python

import threading

class AsyncTask:
    def __init__(self):
        pass
    def TaskA(self):
        print 'Process A'
        threading.Timer(1,self.TaskA).start() # Timer 1초 간격으로 Task A 실

def main():
    print 'Async Function'
    at = AsyncTask()
    at.TaskA()

if __name__ == '__main__':
    main()
```
{% endcode-tabs-item %}
{% endcode-tabs %}

join\(\) 종료할때까지 대기

cancel\(\) 현재 진행중신 쓰레드 제거.

