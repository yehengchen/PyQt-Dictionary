---
description: 현재 PYQT Main Window 또는 현재 화면을 capture할 때 사용되는 명령어를 다룹니다.
---

# PYQT ScreenShot

현재 QT Main Window에 있는 image를 캡쳐합니다.

{% code-tabs %}
{% code-tabs-item title="MainWindow-Capture" %}
```python
class MainDialog(QMainWindow):
   def __init__(self):
      QDialog.__init__(self, None) 
      uic.loadUi(CalUI, self)
      self.test_btn.clicked.connect(self.shoot) # 스샷을 찍기위한 함수를 연결

   def shoot(self):
      date = datetime.now()
      filename = date.strftime('%Y-%m-%d_%H-%M-%S.jpg') # 파일이름 만들기용도
      p = QScreen.grabWindow(app.primaryScreen(),main_dialog.winId())#(메인화면, 현재위젯)
      p.save(filename, 'jpg')
      # QScreen은 PYQT5.QtGui에 포함되어 있는 항목으로 grabwindow로 캡쳐가 가능합니다.

if __name__ == "__main__":
   app = QApplication(sys.argv)
   main_dialog = MainDialog()
   main_dialog.show()
   app.exec_()
```
{% endcode-tabs-item %}
{% endcode-tabs %}

