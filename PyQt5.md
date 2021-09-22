# Pyqt5/PySide2

## 第一个小例子

```python
#!/usr/bin/env python
# _*_ coding: UTF-8 _*_

import sys
import PyQt5.QtWidgets as qt

info='''薛蟠     4560 25
薛蝌     4460 25
薛宝钗   35776 23
薛宝琴   14346 18
王夫人   43360 45
王熙凤   24460 25
王子腾   55660 45
王仁     15034 65
尤二姐   5324 24
贾芹     5663 25
贾兰     13443 35
贾芸     4522 25
尤三姐   5905 22
贾珍     54603 35'''

class MyWin(qt.QMainWindow):
    def __init__(self, parent=None, title="python", size_w=0, size_h=0) -> None:
        super().__init__(parent)
        self.resize(size_w,size_h) #窗口大小
        self.setWindowTitle(title) #标题
        self.control_creat() #创建控件
        #事件绑定
        self.btn.clicked.connect(self.btn_event)

    #控件创建
    def control_creat(self):    
        self.edit=qt.QPlainTextEdit(info,self)        
        self.edit.resize(400,400)
        self.btn=qt.QPushButton('btn',self)
        self.btn.move(400,0)
        self.btn.resize(100,400)

    #事件回调
    def btn_event(self): #按钮按下的事件
        info=self.edit.toPlainText()
        info_list=info.splitlines()
        list_more="薪资两万以上的:\n"
        list_less="薪资两万以下的:\n"
        for info_i in info_list:
            num=int(info_i.split()[1])    
            if(num>=20000):
                list_more+=info_i+'\n'
            else:
                list_less+=info_i+'\n'
        qt.QMessageBox.about(self,'统计结果',list_more+'\n'+list_less)


#运行
if (__name__=='__main__'):
    app=qt.QApplication(sys.argv)
    win=MyWin(None,"薪资统计",500,400)
    win.show()
    sys.exit(app.exec_())   

```

![image-20210921203726511](https://i.loli.net/2021/09/22/wm7o2uPCpTqXM4Q.png)

![image-20210921203823339](https://i.loli.net/2021/09/22/KWfpduAHBNqLU2n.png)

## 我的第一个框架

`Ui_TEST_UI.py`

```python
from PyQt5 import QtCore, QtGui, QtWidgets


class Ui_MainWindow(object):
    def setupUi(self, MainWindow):
        MainWindow.setObjectName("MainWindow")
        MainWindow.resize(800, 600)
        ...
```

这是一个纯UI编写的文件，为了不在里面做改动，下面新创建一个继承的类，并在构造函数中完成窗口的创建。

`My_UI.py`

```python
from Ui_TEST_UI import *
import PyQt5.QtWidgets as qt

class My_UI(Ui_MainWindow):
    def __init__(self,win) -> None:
        super().__init__()
        self.win=win
        self.setupUi(win)  
        ###在下面添加新的窗口设计代码
        ...
        ...
    def ...
```

这是一个继承类，继承了UI文件所创建的所有控件和格式，在__init__中**setupUi**完成了对窗口的创建。

`main.py`

```python
#!/usr/bin/env python
# _*_ coding: UTF-8 _*_

from PyQt5 import QtCore, QtGui, QtWidgets
import sys
from My_UI import *

if __name__=='__main__':
    app=QtWidgets.QApplication(sys.argv)  

    win=QtWidgets.QMainWindow() #创建窗口对象
    ui=My_UI(win)  #创建新的实例
    win.show()

    sys.exit(app.exec_())   
```

这是主函数，创建示例并显示窗口。

## Matplotlib

### 基础例子

``` python
#!/usr/bin/env python
# _*_ coding: UTF-8 _*_

import sys
import matplotlib.pyplot as plt
import PyQt5.QtWidgets as qt
import numpy as np
from matplotlib.backends.backend_qt5agg import FigureCanvas as FigureCanvas

class Appdemo(qt.QMainWindow):
    def __init__(self):        
        super().__init__()
        self.mat_ax=Mat_ax(self)

class Mat_ax(FigureCanvas):
    def __init__(self,parent):
        fig,self.ax=plt.subplots(figsize=(5,4),dpi=100) #设置窗口大小
        super().__init__(fig)
        self.setParent(parent)
        self.ax.set_title("wyj")

        x=np.linspace(0,10,1000)
        y=np.sin(x)

        self.ax.plot(x,y)

if __name__=='__main__':
    app=qt.QApplication(sys.argv)
    win=Appdemo()
    win.resize(500,400)
    win.show()
    sys.exit(app.exec_())
```

![image-20210922232032680](https://i.loli.net/2021/09/22/dHFc2rIxMVYA5QE.png)

