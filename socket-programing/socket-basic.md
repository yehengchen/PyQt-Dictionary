---
description: '기본적인 소켓에 관한 내용을 다루며, 1대1 소켓 채팅 프로그램'
---

# Socket Basic

#### Socket Communication

인터넷 소켓 통신을 사용하기 위해 소켓을 만들어주어야 한다. 파이썬의 socket모듈은 소켓프로그래밍에 필요한 시스템 콜을 래핑하는 API 모듈이다. 

패키지를 가져오기 위해 `from socket import *` 을 사용한다.

```python
port = 8087
serverSock = socket(AF_INET, SOCK_STREAM) # IP4v, 스트림 소켓
serverSock.bind(('127.0.0.1', port)) # 서버가 소켓을 포트에 매
serverSock.listen(1) # 클라이언트가 바인드된 포트로 연결할 때까지 기다리는 블러킹 메소드(서버)
```

2번 줄의 코드에 주소 체계를 입력하는 패밀리, 소켓 타입 을 인수로 넣게 된다. 3 번째 줄에 오는 bind는 호출 할 때 호스트 이름과 포트 번호를 튜플로 감싸서 전달한다.

\#  Python3 `input()`사용시 문제가 없지만 Python 2 에서는 문자열 데이터를 입력 받을 때 `raw_input()`을 사용하여 입력을 처리해야 한다.

```python
connectionSock, addr = serverSock.accept() # Client 연결 수
```

클라이언트의 연결을 수락하고 클라이언트 소켓과, 주소를 받아

```python
recvData = sock.recv(1024) # 1024 byte크기만큼 메시지를 가져
print('other : %s '%recvData) # 가져온 메시지를 출
```

메시지를 출력할 때 `recvData.decode()` 형식으로 출력이 필요하기도 하다.

#### socket close

소켓은 외부 리소스를 열어서 사용하는 것이므로 닫는 것이 매우 중요하다. 연결을 종료할 때 에는 서버와 클라이언트 모두 소켓을 닫아야 하며, 이미 닫힌 소켓에서 데이터를 주고받는 모든 행동 에러가 된다.

`sock.close()` 소켓을 종료할 때 사용하는 메소드

{% code-tabs %}
{% code-tabs-item title="Chatting\_server.py " %}
```python
from socket import *
import threading
import time

class Communication_server(threading.Thread):
    def __init__(self):
        threading.Thread.__init__(self)
        port = 8087
        self.serverSock = socket(AF_INET, SOCK_STREAM)
        self.serverSock.bind(('127.0.0.1', port))
        self.serverSock.listen(1)
        print('%d port access waiting...'%port)
        connectionSock, addr = serverSock.accept()
        print('%s access'%str(addr))
        sender = threading.Thread(target=self.send, args=(connectionSock,))
        receiver = threading.Thread(target=self.receive, args=(connectionSock,))
        sender.start()
        receiver.start()

    def send(self, sock):
        while True:
            try:
                sendData = raw_input('>>>')
                sock.send(sendData)
            except:
                print("soket error..closed...server socket")
                sock.close()
                self.serverSock.Close()
                break

    def receive(self, sock):
        while True:
            try:
                recvData = sock.recv(1024)
                print('other : %s '%recvData)
            except:
                print("soket error..closed...server socket")
                sock.close()
                self.serverSock.Close()
                break

if __name__ == "__main__":
    communicate = Communication_server()
    while True:
        time.sleep(1)
        pass
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="Chatting\_client.py" %}
```python
from socket import *
import threading
import time


def send(sock):
    while True:
        sendData = raw_input('>>>')
        sock.send(sendData)


def receive(sock):
    while True:
        recvData = sock.recv(1024)
        print('other : %s '%recvData)


port = 8087
clientSock = socket(AF_INET, SOCK_STREAM)
clientSock.connect(('127.0.0.1',port))

print('access')

sender = threading.Thread(target=send, args=(clientSock,))
receiver = threading.Thread(target=receive, args=(clientSock,))

sender.start()
receiver.start()

while True:
    time.sleep(1)
    pass

```
{% endcode-tabs-item %}
{% endcode-tabs %}

