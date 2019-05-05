---
description: 'Python Multi-Threading, Multi-Processing에 관련된 내용을 다룹니다.'
---

# Multi Programming

### Python Thread Coding

일반적인 프로세스는 하나의 루틴을 가지고 직력적으로 순서대로 일을 처리한다. 하지만 쓰레드를 사용하는 경우에 하나의 프로세스 안에  여러개의 루틴을 만들어 병렬적인 방법으로 프로그램을 실행하는 것이 가능하다.

파이썬에서 Thread 모듈을 사용하기 위해 threading 을 import 시켜야 사용할 수 있다.

{% code-tabs %}
{% code-tabs-item title="Thread를 이용한 counter" %}
```python
import threading, time
def count():
    count = 0
    while(count<=10):
        print(count)
        count+=1 
        time.sleep(1)

t1 = threading.Thread(target=count) # t1에 thread를 할당시키고 목표함수는 count함수를 실행
t1.start() # t1의 thread 시작
time.sleep(3) 
t2 = threading.Thread(target=count) # t2에 thread를 할당시키고 목표함수는 count함수를 실행
t2.daemon=True # t2의 객체를 데몬 thread로 지정
t2.start() # t2의 thread 시작
```
{% endcode-tabs-item %}
{% endcode-tabs %}

#### Daemon Thread

```python
t2.daemon=True
```

데몬쓰레드는 백그라운드 쓰레드로 메인 쓰레드가 종료되면 같이 종료되는 쓰레드이다. 데몬스레드로 지정을 하지 않을 경우 메인 스레드가 종료되도 서브 스레드는 계속 동작한다.

#### Thread class

{% code-tabs %}
{% code-tabs-item title="Class에서 Thread 사용하기" %}
```python
import threading, time
class counter(threading.Thread):
    def __init__(self):
        threading.Thread.__init__(self) #class안에 thread객체를 넣어준다.
        self.count = 0
    def run(self):
        while (self.count <= 10):
            print(self.count)
            self.count += 1
            time.sleep(1)

if __name__=="__main__":
    object = counter() # object를 class로 생성
    object2 = counter()
    object2.daemon=True # object2 객체를 daemon Thread로 지정함.
    object.start() # start()함수를 사용하면 class안에 run()함수가 실행된다.
    time.sleep(3)
    object2.start()
```
{% endcode-tabs-item %}
{% endcode-tabs %}

