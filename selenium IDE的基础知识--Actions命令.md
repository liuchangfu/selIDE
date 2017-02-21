# 一. 浏览器的操作

 附：selenium IDE的下载地址：http://seleniumhq.org/download/，位于“Selenium IDE”栏中，直接单击“Download version”后面的版本号即可；

## 1. open(url)命令

    1）作用：打开指定的URL，URL可以为相对或是绝对URL；

    2）URL：命令准备打开的URL，可为空；


    3）Target：要打开的URL；

      1）当Target为空，将打开Base URL中填写的页面；

      2）当Target不为空，将打开Base URL + Target页面。如，假设Base URL为http://www.baidu.com/，而Target为index.html，则执行open命令时，将打开http://www.baidu.com/index.html；

      3）当Target以http://开头时，将忽略Base URL，直接打开Target的网址；

## 2.goBack()

    1）作用：模拟单击浏览器的后退按钮； 

    2）由于没有参数，所以Target和Value可不填；

## 3.refresh()

    1）作用：刷新当前页；

    2）由于没有参数，所以Target和Value可不填；

## 4.windowFocus()

    1）作用：将焦点赋予当前的窗体，所有命令在当前的窗体进行，即激活当前选中的浏览器窗口；

    2）由于没有参数，所以Target和Value可不填；

## 5.windowMaximize()

    1）作用：将当前的窗口最大化，即设置为全屏显示； 

    2）由于没有参数，所以Target和Value可不填；

## 6.close()

    1）作用：模拟用户单击窗口上的关闭按钮；

    2）由于没有参数，所以Target和Value可不填；

# 二.界面元素的基本操作

## 1.type(locator,value)

    1）作用：向指定输入域中输入指定值；也可为下拉框、复选框和单选框按钮赋值，只是value应为选项的值，而不是文本内容；

      locator：指向某个元素的元素定位器；

      value：录入的值，复选框和单选框按钮选项的值； 

    2）Target：元素的定位表达式；

    3）Value：要输入的值；

## 2.typeKeys(locator,value)

    1）作用：模拟在指定元素上的按键行为，一个一个地输入字符；

      locator：指向指定元素的元素定位器；

      value：需要输入的值；

    2）Target：元素的定位表达式；

    3）Value：要输入的值；

   **注：typeKeys与type命令不同，type会一次性强制录入指定的值（而非键盘上拥有的字符，例如汉字），而typeKeys相当于一个键一个键的按。在某些特殊情况下，可能会先使用type命令来设置字段的值，然后使用typeKeys来出发刚输入字符对应的键盘事件；**

## 3.click（locator）

    1）作用：单击一个链接、按钮、复选框或单选按钮；

    2）如果该单击事件导致新的页面加载，命令将会加上后缀“AndWait”，即“clickAnd Wait”，或“waitForPageToLoad”命令；

## 4.clickAt(locator,coordString)

     1）作用：与click命令类似，但需要填写相对坐标；

      locator：命令操作对象的定位器；

      coordString：需要单击的元素位置，用坐标(x,y)表示；

## 5.doubleClick(locator)

     1）作用：模拟用户双击；

     2）如果该双击事件导致新的页面加载，命令将会加上后缀“AndWait”，即“doubleClickAndWait”命令，或waitForPageToLoad命令；

## 6.doubleClickAt(coordString)

    1）作用：模拟用户双击；

      coordString：需要单击的元素位置，用坐标（x,y）表示；

## 7.select(selectLocator,optionLocator)

     1）作用：模拟人工单击下拉列表框；

     selectLocator：指向指定选择元素的元素定位器；

     optionLocator：选项的选择器（默认为标签）；

     2）注，选项的定位方式和下拉框的定位方式有所不同；

      a）label=文本值，基于选项的文本进行匹配（默认方式），如label=three；

      b）value=真实值，基于选项的真实值进行匹配，如value=3；

      c）id=id，基于选项的id进行匹配，如id=option3；

      d）index=index，基于选项的索引进行匹配（从0开始），如index=2；

## 8.check(locator)/uncheck(locator)

    1） 作用：勾选/取消一个关联性按钮（checkbox和radio）；

    locator：指向指定元素的元素定位器； 

   **注：大多数程序员在编写JS事件时，喜欢用onClick，而check不会触发单击动作（即不会触发onClick），所以必要的时候可用click 命令来勾选复选框或单选框；**

## 9.uncheck(locator)

    1）与check命令的功能相反，作用为取消勾选；

## 10.focus(locator)

    1）作用：将焦点移动到指定元素；

# 三.键盘鼠标模拟操作

|名称|作用|参数|
|----|----|-----|
|altKeyDown()|模拟按下alt键不放，直到调用altKeyUp命令或者加载新页面|无|
|altKeyUp()|松开Alt键|无|
|controlKeyDown()|模拟按下Ctrl键不放，直到调用controlKeyUp命令或者加载新页面|无|
|controlKeyUp()|松开Ctrl键|无|
|shiftKeyDown()|模拟按下Shift键不放，直到调用shiltKeyUp命令或者加载新页面|无|
|shiftKeyUp()|松开Shift键|无|
|keyDown(locator,keySequencee)|模拟按下某个键不放，直到执行keyUp命令|Target-元素的定位表达式Value-要输入的字符串，是按键的ASCII编码|
|keyPress(locator,keySequence)|模拟用户敲击了某个按键|Target-元素的定位表达式Value-要输入的字符串，是按键的ASCII编码|
|keyUp(locator,keySequence)|模拟松开某个键|Target-元素的定位表达式Value-要输入的字符串，是按键的ASCII编码|
|mouseDown(locator)|模拟用户在指定元素上按下鼠标左键不放|Target-元素的定位表达式 |
|mouseDownAt(locator,coordString)|和mouseDown命令是一个概念，区别在于需要填写相对坐标|Target-元素的定位表达式,Value-要在指定元素上进行点击的x,y坐标|
|mouseDownRight(locator)|模拟用户在指定元素上按下鼠标右键不放|Target-元素的定位表达式|
|mouseDownRightAt(locator,coordString)|和mouseDownRight命令是一个概念，区别在于需要填写相对坐标|Target-元素的定位表达式
,Value-要在指定元素上进行点击的x,y坐标|
|mouseUp(locator)|松开之前使用mouseDown在指定元素上按下的鼠标左键|Target-元素的定位表达式|
|mouseUpAt(locator,coordString)|松开之前使用mouseDownAt在指定元素上按下的鼠标左键|Target-元素的定位表达式,Value-要在指定元素上进行点击的x,y坐标|
|mouseUpRight(locator)|松开之前使用mouseDownRight在指定元素上按下的鼠标右键|Target-元素的定位表达式|
|mouseUpRightAt(locator,coordString)|松开之前使用mouseDownRightAt在指定元素上按下的鼠标右键|Target-元素的定位表达式,Value-要在指定元素上进行点击的x,y坐标|
|mouseOver(locator)|将鼠标光标移动到指定元素内|Target-元素的定位表达式|
|mouseOut(locator)|将鼠标光标移动到指定元素外|Target-元素的定位表达式|

# 四.设置类操作

## 1.setTimeout(timeout)

    1）作用：设置动作的等待时间，默认为30s，仅适用于open命令、以waitFor开头的命令，以及带有AndWait后缀的命令；

    2）timeout：等待时间，单位为ms；

## 2.setSpeed(value)

    1）作用：设置每次操作之间的间隔，默认为0；

    2）value：置操作间隔的时间数，单位为ms；

## 3.pause(waitTime)
    1）作用：强制停止脚本运行，通常用于脚本的调试，定位脚本错误；

    2）waitTime：等待时间，单位为ms；

## 4.break()

    1）作用：暂停正在执行的测试，直到用户手动单击继续按钮；

    2）注：应注意哪些地方使用了该命令，以便及时单击继续按钮，否则会一直停止等待；

## 5.catchEntirePageScreenshot(filename, kwargs)

    1）作用：将当前窗口进行截图并保存为PNG文件；

## 6.highlight(locator)

    1）作用：暂时将指定元素的背景改为黄色，并在稍后取消该效果，一般用于调试；

## 7.echo(message)

    1）作用：将需要的信息在显示区显示，一般用于调试；

## 8.assignld(locator,identifier)

    1) 作用：临时为指定元素设定一个id，以便将来使用该元素时使用该id，通常用于一个元素被多次使用；

    2) locator：指向指定元素的元素定位器；

    3) identifier：为指定元素指定的id；

##9.captureEntirePageScreenshop(filename,kwargs)

    1) 作用：捕获一个快照，并将其存放在本地；

    2) filename：快照名及路径名；

    3) kwargs：改变快照的模式，可为空；

## 12.selectFrame(locator)

    1) 作用：在当前窗体中选择一个框架；

    2) locator：元素定位器；

## 13.runScript(script)
  
    1) 作用：在当前测试窗体的body标签中创建一个新的“script”标签，并在body标签中添加指定的命令文本；
  
    2)script：需要执行的JavaScript；

##14.fireEvent(locator,eventName)

    1) 作用：模拟页面元素被激活的操作；

    2) locator：指向指定元素的元素定位器；

    3) eventName：事件名，如focus、blur等；

## 15.keyPress(locator,keySequence)

    1）作用：模拟用户按下和释放一个键；

    2)locator：指向指定元素的元素定位器；

    3)keySequence：一个字符串，通常为该按键的ASCII；

## 16.controlKeyDown()/controlKeyUp()

    作用：保持键盘上Ctrl键的按下/释放状态，当新的页面加载时，该命令无效；

## 18.metaKeyDown()/metaKeyUp()

    作用：保持Meta键的按下/取消状态；

## 19.shiftKeyDown()/shiftKeyUp()

    作用：保持Shift键的按下/取消状态；

## 20.altKeyDown()/altKeyUp()

    作用：保持Alt键的按下/取消状态；

## 21.setMouseSpeed(pixeks)

    1) 作用：设置鼠标的移动速度；

    2) pixels：每次移动经过的像素；若为0，则每次移动都要进行一次MouseMove操作这样导致缓慢；

## 22.openWindow(url,windowID)

    1) 作用：打开一个新窗口，打开后，需用selectWindow命令选择这个窗口；

    2) url：打开窗口的url；

    3) windowID：为新窗口指定的ID；

**注：此命令可解决selenium对于_blank的BUG问题；**

## 23.selectWindow(windowID)
  
    作用：选择由本次实例所打开的窗口；

## 24.chooseCancelOnNextConfirmation()
  
    作用：相当于手动单击“cancel”按钮，仅一次有效；

**注：该过程不会弹出窗口；**

## 25.answerOnNextPrompt(answer)

    1) 作用：对下一次prompt做出指定回答；

    2) answer：对prompt的指定回答；
**注：该过程不会弹出窗口；**

## 26.contextMenu(locator)

    作用：模拟为元素打开一个关联的菜单，大多数时间效果和鼠标右键一样；

## 27.waitForPageToLoad(timeout)

  作用：等待页面的加载；

## 28.waitForFrameToLoad(frameAddress,timeout)

    1) 作用：等待一个框架的加载完成；

    2) frameAddress：指向该框架的定位器；

    3) timeout：设置最长等待时间，单位为ms；

## 29.waitForCondition(script,timeout)

    1) 作用：等待一段script返回true；

    2) script：等待执行的script；

    3) timeout：设置最长等待时间，单位为ms；

## 30.store(expression,variableName)

    1) 作用：将值存储在变量中；

    2) expression：需要存储的值的表达式；

    3）variableName：存放值的变量；

## 31.submit(formLocator)

    作用：提交一个指定的表单；

## 32.keyDown(locator,keySequence)/keyUP(locator,keySequence)

    作用：模拟用户按下/释放一个按键；

    keySequence：按键对应的ASCII码；

## 33.mouseDown(locator)/mouseUp(locator)
  
    作用：模拟用户在元素上按下/释放鼠标；

## 34.mouseMove(locator)/mouseOut(locator)

    作用：模拟鼠标移到/移出元素；

## 35.mouseOver(locator)

    作用：模拟鼠标停留在元素上；

## 36.removeAllSelections(locator)

    作用：取消多选元素的选择状态。



