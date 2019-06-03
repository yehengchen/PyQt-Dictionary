# PYQT Image Processing

imageLabel.setPixmap\(QtGui.QPixmap.fromImage\(이미지파일\)\)



```python
def get_state(self):
    p = QScreen.grabWindow(app.primaryScreen(), main_dialog.winId())  # (메인화면, 현재위젯)
    p = p.toImage()
    qimg = p.convertToFormat(QImage.Format_RGB888)
    qimg = qimg.rgbSwapped()
    ptr = qimg.constBits()
    ptr.setsize(qimg.byteCount())
    mat = np.array(ptr).reshape(qimg.height(), qimg.width(), 3)
    mat=mat[10:390,10:210] # crop game_image
    mat = cv2.resize(mat, (64, 64))/255
    #cv2.imwrite('Original.jpg', mat)
    print(mat)
    # p.save("test.jpg")
    return mat
```



