# Wxpython参考文档

[Toc]

## Mainloop()

```python
app=wx.App() ##实例化
app.MainLoop() ##主循环
```

## Frame 类

```python
win=wx.Frame(None, title='Basic_Win',size=(760,540),style= wx.CAPTION | 				 wx.CLOSE_BOX | wx.CLIP_CHILDREN) ##wx.MINIMIZE_BOX | 					     wx.MAXIMIZE_BOX | wx.RESIZE_BORDER | wx.SYSTEM_MENU | wx.CAPTION 			   | wx.CLOSE_BOX | wx.CLIP_CHILDREN (wx.DEFAULT_FRAME_STYLE)
			 ##wx.MAXIMIZE
win.Center(wx.BOTH)   #wx.CentreX wx.CentreY
win.Show()
```

## 常用控件

### Button

```python
##构造函数
__init__ (self, parent, id=ID_ANY, label=””, pos=DefaultPosition, 			   		   size=DefaultSize, style=0, validator=DefaultValidator,  					  name=ButtonNameStr)
    
##实例化
btn=wx.Button(parent,label="btn",pos=(10,10),size=(100,50))
```

**Event:**

- `EVT_BUTTON`: *Process a wxEVT_BUTTON event, when the button is clicked.*

**Methods**

- `GetLable` `SetLable`

### TextCtrl

```python
##构造函数
__init__ (self, parent, id=ID_ANY, value=””, pos=DefaultPosition, 		   			  size=DefaultSize, style=0, validator=DefaultValidator, 			       	   name=TextCtrlNameStr)
##实例化
filename=wx.TextCtrl(win,pos=(5,5),size=(210,25))
contents=wx.TextCtrl(win,pos(5,35),size(390,255),style=wx.TE_MULTILINE|wx.HSCROLL)  ##style为两个滑动槽
## wx.TE_PASSWORD 密码
```

**Event**

- **`EVT_TEXT`**: *Respond to a `wxEVT_TEXT` event, generated when the text changes. Notice that this event will be sent when the text controls contents changes – [`wx.TextCtrl.SetValue`](https://docs.wxpython.org/wx.TextEntry.html#wx.TextEntry.SetValue) is called); see [`wx.TextCtrl.ChangeValue`](https://docs.wxpython.org/wx.TextEntry.html#wx.TextEntry.ChangeValue) for a function which does not send this event. This event is however not sent during the control creation.* 
- `EVT_TEXT_ENTER`: *Respond to a `wxEVT_TEXT_ENTER` event, generated when enter is pressed in a text control which must have `wx.TE_PROCESS_ENTER` style for this event to be generated.* 

**Methods**

- `GetValue`  `SetValue` `ChangeValue`

- `LoadFile` `SaveFile`

- `AppendText`

## 布局

```python
pnl=wx.Panel(win) ##面板
###控件布局
hbox_1=wx.BoxSizer(wx.HORIZONTAL)
hbox_2=wx.BoxSizer(wx.HORIZONTAL)
vbox_1=wx.BoxSizer(wx.VERTICAL)
hbox_1.Add(---)
```

```python
SizerItem(sizer, proportion=0, flag=0, border=0, userData=None)
```




## 打包程序

```python
pip install pyinstaller ##安装python打包工具
```

```python
pyinstaller --noconsole main.py  ##打包程序入口文件
```

