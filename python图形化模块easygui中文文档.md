---
title: Python图形化模块EasyGUI中文文档
date: 2020-03-23 09:15:02
tags: [python,图形化,easygui ]
categories: [笔记,开发文档 ]
---
# 说明
在EasyGUI中，所有的GUI交互都由简单函数调用  
这是一个使用EasyGUI的简单演示程序。  
```python
from easygui import *
import sys

# A nice welcome message
ret_val = msgbox("Hello, World!")
if ret_val is None: # User closed msgbox
    sys.exit(0)

msg ="What is your favorite flavor?\nOr Press <cancel> to exit."
title = "Ice Cream Survey"
choices = ["Vanilla", "Chocolate", "Strawberry", "Rocky Road"]
while 1:
    choice = choicebox(msg, title, choices)
    if choice is None:
        sys.exit(0)
    msgbox("You chose: {}".format(choice), "Survey Result")

```
<!--more-->
# EasyGUI演示程序
要运行EasyGUI的演示程序，从命令行调用EasyGUI：  
```shell
python easygui.py
```
或者从IDE（如 IDLE, PythonWin, Wing等）这样：
```python
from easygui import *
egdemo()
```
这样就可以使用EasyGUI的各个函数，并将你的选择输出到控制台中。
# 导入EasyGUI
* 为了使用EasyGUI，必须在使用前导入本模块。最简单的导入语句是：
```python
import easygui
```  
如果使用该表单，则需要访问EasyGUI的函数，必须使用"EasyGUI"前缀，示例：
```python
easygui.msgbox(...)
```  
* 第二种是以这种方式导入EasyGUI：
```python
from easygui import *
```  
这使得调用EasyGUI函数更容易；您不必用"EasyGUI"来对函数名进行前缀，此时你就可以这样写：
```python
msgbox(...)
```  
* 第三种是使用如下导入语句：
```python
import easygui as g
```
这样你就可以使用较少的单词(g)替代原单词(easygui),此时你可以这样写：
```python
g.msgbox(...)
```
若你习惯使用Python和EasyGUI，则第三种替代方法实际上是最好的方法。  

# 使用EasyGUI
当您已经导入EasyGUI模块后，GUI操作就可以简单的用EasyGUI函数添加几个参数实现了。例如，使用EasyGUI写一个简单的"Hello,World!"程序：
```python
from easygui import *
msgbox("Hello, world!")
```
若要查看调用EasyGUI运行结果，在命令提示符窗口输入：
```python
python easygui.py
```
若要查看调用EasyGUI函数的代码示例，请查看EasyGUI.py末尾的演示代码。
# EasyGUI函数的缺省参数
对于所有的图形化组件函数，前两个参数是消息(msg)和标题(title)，按顺序排列。在某些情况下，对用户来说这可能不是最为友好的安排（例如，获取目录和文件名的对话框忽略消息(msg)参数），但我认为更重要的是保持所有组件之间的一致性。  

大多数EasyGUI函数的参数都有缺省值。几乎所有的图形化组件函数都显示一个消息和一个标题。标题默认为空字符串，并且消息通常具有简单的默认值。

这样可以根据需要，指定尽可能少的参数，以获得所需的结果。例如，msgbox函数的标题参数是可选的，所以你可以只指定消息调用msgbox函数，这样：
```python
msgbox("Danger, Will Robinson!")
```  
或者指定消息和标题，这样：
```python
msgbox("Danger, Will Robinson!", "Warning!")
```
在各种类型的buttonbox上，默认的消息是"Shall I continue?"，所以，你可以无需任何参数去调用buttonbox函数。这里，我们可以无需任何参数调用ccbox函数（close/cancel box，它返回布尔值）：
```python
if ccbox():
    pass	# 用户选择后继续
else:
    return	#用户选择后退出
```

# 在调用EasyGUI函数时使用关键字参数
在调用EasyGUI函数时可能会使用到关键字参数。  

假设你想使用一个ButoBox，但是（不管什么原因）不想指定标题（第二）位置的参数。您仍然可以使用关键字指定选择参数（第三个参数），这样：
```python
choices = ["是","否","只在周五"]
reply = choicebox("你喜欢吃鱼吗?", choices=choices)
```  

# 使用按钮控件(buttonboxes)
为满足公共需求在文件顶部建立buttonbox()的函数。

## 提示框
msgbox显示一条消息并提供一个OK按钮。你可以发送任何你想要的消息，以及你想要的任何标题。如果你愿意，你也可以在按钮上重写“OK”的默认文本。下面是msgbox函数的示例：
```python
def msgbox(msg="(Your message goes here)", title="", ok_button="OK"):
    ....
```
重写按钮文本最简单的方法是用关键字参数，示例：
```python
msgbox("Backup complete!", ok_button="Good job!")
```
下面是几个示例：
```python
msgbox("Hello, world!")
```
![msgbox("Hello, world!")](https://imgkr.cn-bj.ufileos.com/8f68cfe4-6af5-4a58-b607-edcf747dd050.png)
```python
msg = "Do you want to continue?"
title = "Please Confirm"
if ccbox(msg, title):     # show a Continue/Cancel dialog
    pass  # user chose Continue
else:  # user chose Cancel
    sys.exit(0)
```
![Do you want to continue?](https://imgkr.cn-bj.ufileos.com/2ab4290d-082f-471d-b930-998bc58bb854.png)

## ccbox
ccbox提供"继续"和"取消"选项，并返回 True（用于继续）或返回 False（用于取消）。

## ynbox  
ynbox提供了"是"和"否"的选择，并返回false的true。

## buttonbox
若要在buttonbox中指定自己的按钮集，请使用buttonbox()函数。

buttonbox可以用来显示你选择的一组按钮。当用户单击按钮时，buttonbox()返回选择的文本。如果用户取消或关闭buttonbox，则返回默认选择（第一选择）。

按钮框显示一个消息、一个标题和一组按钮。返回值为用户选择的按钮的文本。

## indexbox
indexbox显示一个消息、一个标题和一组按钮。返回用户选择的索引。例如，如果使用三个选项（A，B，C）调用索引框，如果用户选择A，则索引框将返回0，如果他选择B，则返回1，如果选择C，则为2。

## boolbox
boolbox(boolean box)显示一个消息、一个标题和一组按钮。如果选择第一个按钮，返回1。否则返回0。
下面是boolbox()的一个简单例子：
```python
message = "What does she say?"
title = ""
if boolbox(message, title, ["She loves me", "She loves me not"]):
    sendher("Flowers") # This is just a sample function that you might write.
else:
    pass
```
<!--这个例子就很魔性-->
  
# 如何在buttonbox中显示图像
当调用Button框函数时(或显示按钮的其他函数，如msgbox、indexbox、ynbox等等)，您可以指定关键字参数image=xxx，其中xxx是图像的文件名，文件可以是.gif。

你也可以使用其他图像格式，如.png。

如果指定了图像参数，则图像文件将在消息之后显示。

以下是EasyGUI示例代码：
```python
image = "python_and_check_logo.gif"
msg = "Do you like this picture?"
choices = ["Yes","No","No opinion"]
reply = buttonbox(msg, image=image, choices=choices)
```
如果点击底部的一个按钮，它的值将在“reply”中返回。你也可以点击图像，返回图像文件名。

![buttonbox中显示图像](https://imgkr.cn-bj.ufileos.com/de4e342a-3dfd-452b-9e64-cd5ba220c65a.png)

# 让用户从选择列表中选择

## choicebox

Buttonboxes很好地为用户提供了短选择的小选择。但是如果有很多选择，或者选择的文本很长，那么一个更好的策略就是把它们呈现为一个列表。

choicebox提供了一种用户从选择列表中选择的方法。选择是按序列（元组或列表）指定的。在呈现之前，将给出不区分大小写的选项。

键盘可以用来选择列表中的元素。

例如，在键盘上按下"g"，将跳转到"g"开头单词的第一个元素，再次按下"g"，光标会跳转到下一个元素。在从"g"开始的元素的末尾，再次按下"g"将使选择包括所有"g"开头的元素，并跳到"g"开头第一个元素。

如果没有从"g"开始的元素，则选择发生在"g"位置之前的最后一个元素。如果在"g"之前没有元素，则选择列表中的第一个元素：

```python
msg ="What is your favorite flavor?"
title = "Ice Cream Survey"
choices = ["Vanilla", "Chocolate", "Strawberry", "Rocky Road"]
choice = choicebox(msg, title, choices)
```
![choicebox](https://imgkr.cn-bj.ufileos.com/382bb6f3-8836-4fbf-86ff-752c5838e85d.png)

choicebox的另一个例子：

![choicebox的另一个例子](https://imgkr.cn-bj.ufileos.com/fe0f90e8-e8eb-4250-b3ed-283b59fb0481.png)

## multchoicebox
multchoicebox()函数为用户从选择列表中选择了一种方式。界面看起来像choicebox，但是用户可以有0个、1个或多个选择。

选项是按序列（元组或列表）指定的。在输出之前，选项将按不区分大小写的顺序排列。

![multchoicebox](https://imgkr.cn-bj.ufileos.com/e19e9baa-6a04-4e5c-b9ec-6499add8ba61.png)

# 让用户输入信息

###enterbox

enterbox是从用户那里获取字符串的最简单的方法

## integerbox

integerbox是从用户那里获取整数的最简单的方法

## multenterbox

multenterbox是显示多个enterbox在一个屏幕上的最简单的方法

![multenterbox](https://imgkr.cn-bj.ufileos.com/fad079a0-6227-4daa-aaf9-104ed89a78a7.png)

在multenterbox中：
* 如果值比名称少，则在值的数目与名称的数目相同的情况下，用空字符串填充值列表。
* 如果有更多的值而不是名称，则将列表的值截断，以便有与名称一样多的值。

返回字段值的列表，若用户取消操作，则无返回值。

下面是一些示例代码，它显示了multenterbox返回的值如何在被接受之前检查其有效性：

```python
from __future__ import print_function
msg = "Enter your personal information"
title = "Credit Card Application"
fieldNames = ["Name", "Street Address", "City", "State", "ZipCode"]
fieldValues = multenterbox(msg, title, fieldNames)
if fieldValues is None:
    sys.exit(0)
# make sure that none of the fields were left blank
while 1:
    errmsg = ""
    for i, name in enumerate(fieldNames):
        if fieldValues[i].strip() == "":
          errmsg += "{} is a required field.\n\n".format(name)
    if errmsg == "":
        break # no problems found
    fieldValues = multenterbox(errmsg, title, fieldNames, fieldValues)
    if fieldValues is None:
        break
print("Reply was:{}".format(fieldValues))
```

# 让用户输入密码信息

## passwordbox

passwordbox就像一个enterbox，但用于输入密码。在键入文本时，文本被屏蔽为星号。

## multpasswordbox

multpasswordbox具有与multenterbox相同的接口，但当显示时，最后一个字段被假定为密码，并用星号屏蔽。

![multpasswordbox](https://imgkr.cn-bj.ufileos.com/baa8db8e-b313-4730-bb30-e98d69431575.png)

# 显示文本

EasyGUI提供了显示文本的功能。

## textbox

textbox()函数以比例字体显示文本。正文将文字换行。

## codebox

codebox()函数以一个单字符的字体显示文本，不进行格式处理。

![codebox](https://imgkr.cn-bj.ufileos.com/d9f16224-febb-4de9-a537-c921247c69d5.png)

注意，可以通过字符串或字符串列表传递codebox()和textbox()。字符串列表将在显示之前转换为文本。你可以使用这些函数显示文件的内容：

```python
import os
filename = os.path.normcase("c:/autoexec.bat")
f = open(filename, "r")
text = f.readlines()
f.close()
codebox("Contents of file " + filename, "Show File Contents", text)
```

# 使用文件

常见的需求是向用户请求文件名或目录。EasyGUI提供了允许用户浏览文件系统并选择目录或文件的基本功能(这些函数是关于lib-tk中的小部件和类的包装)。

请注意，在当前版本的EasyGUI中，不支持startpos参数。

## diropenbox
diropenbox返回目录的名称

## fileopenbox
fileopenbox返回打开文件的名称

![fileopenbox](https://imgkr.cn-bj.ufileos.com/3fdbf151-527e-41a2-a423-08c3fc64d562.png)

## filesavebox

filesavebox返回文件名

# 记住用户设置

## EgStore
用户请求一些设置，然后保存或者将其存储在磁盘上，这样，下次用户使用你的应用程序时，就可以记住他以前的设置。

为了实现存储和恢复用户设置的过程，EasyGUI提供了一个名为EgStore的类。为了记住一些设置，您的应用程序必须定义一个继承EgStore的类（我们称之为设置，你可以改为"啥都无所谓")。

您的应用程序还必须创建该类的对象（让我们调用设置对象）

设置类的构造函数(the__init__method)可以初始化所有你设置的值。

完成此操作后，你就可以简单地通过将值赋值给设置对象中的实例变量来记住设置，并使用settings.store()方法将设置参数保存到磁盘。

下面是使用设置类的代码示例：

```python
from easygui import EgStore

# -----------------------------------------------------------------------
# define a class named Settings as a subclass of EgStore
# -----------------------------------------------------------------------
class Settings(EgStore):

    def __init__(self, filename):  # filename is required
        # -------------------------------------------------
        # Specify default/initial values for variables that
        # this particular application wants to remember.
        # -------------------------------------------------
        self.userId = ""
        self.targetServer = ""

        # -------------------------------------------------
        # For subclasses of EgStore, these must be
        # the last two statements in  __init__
        # -------------------------------------------------
        self.filename = filename  # this is required
        self.restore()

# Create the settings object.
# If the settingsFile exists, this will restore its values
# from the settingsFile.
# create "settings", a persistent Settings object
# Note that the "filename" argument is required.
# The directory for the persistent file must already exist.

settingsFilename = "settings.txt"
settings = Settings(settingsFilename)

# Now use the settings object.
# Initialize the "user" and "server" variables
# In a real application, we'd probably have the user enter them via enterbox
user    = "obama_barak"
server  = "whitehouse1"

# Save the variables as attributes of the "settings" object
settings.userId = user
settings.targetServer = server
settings.store()    # persist the settings
print("\nInitial settings")
print settings

# Run code that gets a new value for userId
# then persist the settings with the new value
user    = "biden_joe"
settings.userId = user
settings.store()
print("\nSettings after modification")
print settings

# Delete setting variable
del settings.userId
print("\nSettings after deletion of userId")
print settings
```
下面是使用专用函数创建设置类的代码示例：

```python
from easygui import read_or_create_settings

# Create the settings object.
settings = read_or_create_settings('settings1.txt')

# Save the variables as attributes of the "settings" object
settings.userId = "obama_barak"
settings.targetServer = "whitehouse1"
settings.store()    # persist the settings
print("\nInitial settings")
print settings

# Run code that gets a new value for userId
# then persist the settings with the new value
user    = "biden_joe"
settings.userId = user
settings.store()
print("\nSettings after modification")
print settings

# Delete setting variable
del settings.userId
print("\nSettings after deletion of userId")
print settings
```

# 捕获异常(抛出异常)

##exceptionbox

在EasyGui应用程序中有时会出现异常情况。根据应用程序的运行方式，堆栈跟踪可能会被丢弃，或者在应用程序崩溃时输出异常信息。

EasyGUI提供了一种通过exceptionbox处理异常的方法。exceptionbox显示代码框中的堆栈跟踪，并允许继续处理。

exceptionbox使用简单。下面是一个代码示例：

```python
try:
    someFunction()  # this may raise an exception
except:
    exceptionbox()
```
![exceptionbox](https://imgkr.cn-bj.ufileos.com/b5fbb376-dfb9-403e-b7fe-51bc0fd2cace.png)

<hr/>
# 翻译自英文版原文档  
原版文档地址：[https://easygui.readthedocs.io/en/latest/tutorial.html](https://easygui.readthedocs.io/en/latest/tutorial.html)