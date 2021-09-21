# Python

## 开头

```pyhton
#!/usr/bin/env python
# _*_ coding: UTF-8 _*_
```

## 类和对象

#### 无构造函数

```python
def test_func(num): #return a same number
    return num

class MyClass:
    a=1
    def pluse_func(self,pluse_num): #return self.a pluse pluse_number
        a=self.a
        self.a+=test_func(pluse_num)
        return self.a

obj=MyClass()
print(obj.pluse_func(pluse_num=20))
```

类的组成：构造函数（创建对象的时候默认运行，可以没有构造函数）

​				   成员变量（可在构造函数中定义，或者在与构造函数同等级定义）

​				   成员函数（**第一个参数为self**） 

#### 有构造函数

```python
def test_func(num): #return a same number
    return num

class MyClass:
    def __init__(self,a_in):
        self.a=a_in
    def pluse_func(self,pluse_num): #return self.a pluse pluse_number
        self.a+=test_func(pluse_num)
        return self.a
    
obj=MyClass(2)
print(obj.pluse_func(pluse_num=20))
```

上述类中引入了构造函数，**新创建一个对象时，先进入构造函数中**

#### 类的继承

以pyqt5为例:

```python
import PyQt5.QtWidgets as qt


class MyWin(qt.QMainWindow):
    def __init__(self, parent=None, title="python", size_w=0, size_h=0) -> None:
        super().__init__(parent)
        self.resize(size_w,size_h) #窗口大小
        self.setWindowTitle(title) #标题
        self.control_creat() #创建控件
        self.btn.clicked.connect(self.btn_clicked)
    def control_creat(self):    
        self.edit=qt.QPlainTextEdit('niu',self)        
        self.edit.resize(400,400)
        self.btn=qt.QPushButton('btn',self)
        self.btn.move(400,0)
        self.btn.resize(100,400)
    def btn_clicked(self):
        qt.QMessageBox.about(self,'提示',"good")
if (__name__=='__main__'):
    app=qt.QApplication([])
    win=MyWin(None,"薪资统计",500,400)
    win.show()
    app.exec_()
```

## 字符串处理

#### `splitlines()`

返回一个列表

```python
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
info.splitlines()
```

![image-20210920223117026](https://i.loli.net/2021/09/22/M7LSYKIXTAU8s3B.png)

#### `split`

拆分字符串为列表

![image-20210920230344236](https://i.loli.net/2021/09/22/1EADV7c5tTs4Wim.png)

#### 类型转换

`int` `float` `str`

​	

