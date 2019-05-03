# PYQT Object connection

### Signal and Emit

Gui를 만드는 과정에서 여러가지 기능을 생성할때 클래스를 여러개 만들어서 생성할 때, 객체에서 발생한 이벤트값을 다른 객체로 전달할 때 Signal과 Emit를 사용하여 전달가능하다.

{% code-tabs %}
{% code-tabs-item title="Example1" %}
```python
class MainDialog(QMainWindow):
    def __init__(self):
        QMainWindow.__init__(self, None)
        self.[object_name].[object_name2][str].connect(self.[connect_object].method)

class Board(QFrame,QMainWindow):
    [object_name2] = pyqtSignal(str)
                
    def method(self):
            self.[object_name2].emit("paused")
```
{% endcode-tabs-item %}
{% endcode-tabs %}

위 내용과 같으 코드를 짜게 되면 Class가 달라도, Event를 발생시켜 객체를 편집하는 것이 가능하다.

{% code-tabs %}
{% code-tabs-item title="Example1-1" %}
```python
class MainDialog(QMainWindow):
    def __init__(self):
        QMainWindow.__init__(self, None)
        self.game_frame.msg2sscorelabel[str].connect(self.scroe_lable.setText)

class Board(QFrame,QMainWindow):
    msg2Statusbar = pyqtSignal(str)
    def pause(self):
            self.msg2sscorelabel.emit("paused")
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Board Class에서 pause를 호출하게 되면 msg2sscorelabel객체의 signal이 emit되어 연결된 score\_label\(Qlabel\)의 텍스트 값을 바꾸게 된다.

