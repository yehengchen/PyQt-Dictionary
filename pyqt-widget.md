# PYQT Widget

### QPushButton

버튼에 이벤트 연결하는 방법으로 이벤트에 함수를 연결시켜서 사용한다.

{% code-tabs %}
{% code-tabs-item title="Using \_btn" %}
```python
self.[btn_name].clicked.connect(self.[class_function_name])
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="QPushButton\_activate" %}
```python
self.Game_start_btn.setEnabled(False) # 버튼 비활성화
self.Game_start_btn.setEnabled(True) # 버튼 활성
```
{% endcode-tabs-item %}
{% endcode-tabs %}

[https://www.riverbankcomputing.com/static/Docs/PyQt4/qpushbutton.html](https://www.riverbankcomputing.com/static/Docs/PyQt4/qpushbutton.html)

