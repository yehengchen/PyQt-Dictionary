# PyQt설치 및 실행방법

### PyQt설치

#### 설치환경 : 16.04 Ubuntu, Python3 기준으로 작성되었습니다.

pip3 install --user pyqt5  
sudo apt-get install python3-pyqt5  
sudo apt-get install pyqt5-dev-tools sudo apt-get install qttools5-dev-tools

### Qt designer 실행 방법

1. Terminal 창에서 바로 실행하기

`$ qtchooser -run-tool=designer -qt=5`

1. Designer App 실행

$ /usr/lib/x86\_64-linux-gnu/qt5/bin/designer 경로에 Designer App 실행

### 기초 파일구성

Qt Designer로 파일을 생성하게 되면, ui 파일이 생성되어, python 코드에서 불러와서 사용 해야한다.

!
