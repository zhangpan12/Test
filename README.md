# Test
第一阶段：python学习
（1）“温度转换”实例
      #TempConvert.py
      TempStr=input("请输入带有符号的温度值:")
      if TempStr[-1] in ['F','f']:
          C=(eval(TempStr[0:-1])-32)/1.8
          print("转换后的温度是{:.2f}C".format(C))
      elif TempStr[-1] in ['C','c']:
          F=1.8 * eval(TempStr[0:-1])+32
          print("转换后的温度是{:.2f}F".format(F))
      else:
          print("输入格式错误")

        
   自己认为比较重要的知识点：
   1.单行注释：以#开头
     多行注释：以'''开头和结尾
   2.字符串的使用：使用[]获取字符串中一个或多个字符
     索引：返回字符串中单个字符   <字符串>[M]  eg:TempStr[－1]  (表示获取字符串中的倒数第一个字符)
     切片：返回字符串中一段字符子串  <字符串>[M:N]  eg:TempStr[0:－1]  (表示获取第一个字符到最后一个字符，包括第一个字符但不包括最后一个)
   3.输入函数input():<变量>=input(<提示信息字符串>) 
     eg:TempStr=input("请输入")  #TempStr保存用户输入的信息
   4.评估函数eval():去掉参数最外侧引号并执行余下语句的函数
     eg:如果TempStr[0:－1]值是"12.3",输出是12.3
   
（2）“Python蟒蛇绘制”实例
      #PythonDraw.py
      import turtle
      turtle.setup(650,350,200,200)
      turtle.penup()
      turtle.fd(-250)
      turtle.pendown()
      turtle.pensize(25)
      turtle.pencolor("purple")
      turtle.seth(-40)
      for i in range(4):
            turtle.circle(40,80)
            turtle.circle(-40,80)
      turtle.circle(40,80/2)
      turtle.fd(40)
      turtle.circle(16,180)
      turtle.fd(40 * 2/3)
      turtle.done()
      
   重要知识点：
   1.库引用：使用import保留字完成
     import <库名>
     <库名>.<函数名>(<函数参数>)
   2.import更多用法
     A.使用from和import保留字共同完成
       from <库名> import <函数名>
       from <库名> import *
       <函数名>(<函数参数>)
       ------要点1中的import的用法不会出现函数重名问题，但这种方法则会出现
     B.使用import和as保留字共同完成
       import <库名> as <库别名>
       <库别名>.<函数名>(<函数参数>)
       ------这种方法给调用的外部库关联一个更短、更适合自己的名字
   3.turtle画笔控制函数penup(), pendown(), pensize(), pencolor()
   4.turtle运动控制函数fd(), circle()
     其中turtle.circle(r, extent=None)表示根据半径r绘制extent角度的弧形
         r:默认圆心在海龟左侧r距离的位置
         extent：绘制角度，默认是360度整圆
    5.turtle方向控制函数seth()
    6.循环语句与range()函数
      for <变量> in range(<次数>):
            <被循环执行的语句>
      其中<变量>表示每次循环的计数
          range(N)产生0到N-1的整数序列，共N个
          range(M,N)产生M到N-1的整数序列，共N-M个
                  
            
