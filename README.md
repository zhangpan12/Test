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
          
 （3）数字类型及操作
 
      1.要注意浮点数间运算存在不确定尾数，浮点数间运算与比较用round()函数辅助，round(x,d)：对x四舍五入，d是小数截取位数
      2.Python中多了一个复数类型，与数学中复数概念一致
      3.x/y是x与y之商，而x//y是整数除；x**y表示幂运算，x的y次幂
      
 （4）字符串类型及操作
 
      1.字符串处理函数chr(x)中x为Unicode编码，返回其对应的字符；ord(x)中x为字符，返回其对应的Unicode编码
      2.字符串类型的格式化使用.format()方法，<模板字符串>.format(<逗号分隔的参数>)
      
 （5）time库
 
      1.包括三类函数
        时间获取：time()  ctime()   gmtime()
        时间格式化：strftime()   strptime()
        程序计时：sleep()  perf_counter()
      2.“文本进度条”的例子
         
         #time.py
         import time
         scale=50
         print("执行开始".center(scale//2,"-"))
         start=time.perf_counter()
         for i in range(scale+1):
            a='*'*i
            b='.'*(scale-i)
            c=(i/scale)*100
            dur=time.perf_counter()-start
            print("\r{:^3.0f}%[{}->{}]{:.2f}s".format(c,a,b,dur),end=" ")
            time.sleep(0.1)
         print("\n"+"执行结束".center(scale//2,'-'))
    
  （6）程序的控制结构
  
   1.程序的异常处理的基本使用            
        
        try:                        
            <语句块1>
        except:
            <语句块2>
        或    
        try:
            <语句块1>
        except <异常类型>:
            <语句块2> 
   2.异常处理的高级使用：
        
         try:
            <语句块1>
         except:
            <语句块2>
         else:
            <语句块3>
         finally：
            <语句块4>
       其中finally对应语句块4一定执行，else对应语句块3在不发生异常时执行
   3.例子：身体质量指标BMI
         
         height, weight = eval(input("请输入身高(米)和体重(公斤)[逗号隔开]:"))
         bmi=weight / pow(height,2)
         print("BMI数值为:{:.2f}".format(bmi))
         who, nat="", ""
         if bmi<18.5:
            who,nat="偏瘦","偏瘦"
         elif 18.5<=bmi<24:
            who,nat="正常","正常"
         elif 24<=bmi<25:
            who,nat="正常","偏胖"
         elif 25<=bmi<28:
            who,nat="偏胖","偏胖"
         elif 28<=bmi<30:
            who,nat="偏胖","肥胖"
         else:
            who,nat="肥胖","肥胖"
         print("BMI指标为：国际'{0}',国内'{1}'".format(who,nat))
   4.循环的高级用法
   
     循环与else:当循环没有被break语句退出时，执行else语句块
     eg:
     
     for c in "PYTHON":
      if c=="T":
          continue
      print(c,end="")
      else:
          print("正常退出")
      输出结果为：PTHON正常退出
   
      for c in "PYTHON":
            if c=="T":
                  break
            print(c,end="")
            else:
                  print("正常退出")
      输出结果为：PY
   
   5.rondom库的使用
   
    A. 基本随机函数：seed(), random()
       seed(a=None)初始化给定的随机数种子，默认为当前系统时间
       random()生成一个[0.0,1.0)之间的随机小数
    B. 扩展随机数函数
       randint(a,b)生成一个[a,b]之间的整数
       randrange(m,n[,k])生成一个[m,n)之间以k为步长的随机整数
       getrandbits(k)生成一个k比特长的随机整数
       uniform(a,b)生成一个[a,b]之间的随机小数
       choice(seq)从序列seq中随机选一个元素
       shuffle(seq)将序列seq中元素随机排列，返回打乱后的序列
   6.例子：圆周率的计算
      
      from random import random
      from time import perf_counter
      DARTS=1000*1000
      hits=0.0
      start=perf_counter()
      for i in range(1,DARTS+1):
          x,y=random(),random()
          dist=pow(x**2+y**2,0.5)
          if dist<=1.0:
              hits=hits+1
      pi=4*(hits/DARTS)
      print("圆周率值是:{}".format(pi))
      print("运行时间是:{:.5f}s".format(perf_counter()-start))
      
  （7）函数和代码复用
  
      1.lambda函数
        lambda函数返回函数名作为结果，是一种匿名函数，用于定义简单的、能够在一行内表示的函数
        <函数名> = lambda <参数>: <表达式>
        等价于
        def <函数名>(<参数>):
            <函数体>
            return <返回值>
            
        eg：
        >>>f=lambda x,y : x+y
        >>>f(10,15)
        25
        >>>f=lambda : "lambda函数"
        >>>print(f())
        lambda函数
      2.“汉诺塔”例子
         count=0
         def hanoi(n,src,dst,mid):
            global count
            if n==1:
                  print("{}:{}->{}".format(1,src,dst))
                  count+=1
            else:
                  hanoi(n-1,src,mid,dst)
                  print("{}:{}->{}".format(n,src,dst))
                  count+=1
                  hanoi(n-1,mid,dst,src)
          hanoi(3,"A","C","B")
          print(count)
          >>>
          1:A->C
          2:A->B
          1:C->B
          3:A->C
          1:B->A
          2:B->C
          1:A->C
          7
       
   （8）组合数据类型
   
      1.集合数据类型及操作
        集合使用{}和set()函数创建
        集合间操作：交(&)、并(|)、差(-)、补(|)、比较(>=<)
        集合类型方法：.add()、.discard()、.pop()等
        集合类型主要应用于：包含关系比较、数据去重
      2.序列类型及操作
        序列是基类类型，扩展类型包括：字符串、元组、列表
        元组用()和tuple()创建，列表用[]和set()创建
        元组一旦创建就不能被修改，列表创建后可以随意被修改
      3.字典类型及操作
        映射关系采用键值对表示
        字典类型使用{}和dict()创建，键值对之间用:分隔
        d[key]方式既可以索引，也可以赋值
        字典类型有一批操作方法和函数，最重要的是.get()
      4."文本词频统计"例子
         def getText():
             txt=open("hamlet.txt","r").read()
             txt=txt.lower()
             for ch in '!"#$%&()*+,-./:;<=>?@[\\]^_‘{|}~':
                 txt=txt.replace(ch," ")
             return txt
             
         hamletTxt=getText()
         words=hamletTxt.split()
         counts={}
         for word in words:
             counts[word]=counts.get(word,0)+1
         items=list(counts.items())
         items.sort(key=lambda x:x[1],reverse=True)
         for i in range(10):
             word,count =items[i]
             print("{0:<10}{1:>5}".format(word,count))
         >>>
         the        1138
         and         965
         to          754
         of          669
         you         550
         i           542
         a           542
         my          514
         hamlet      462
         in          436
         
   （9）文件和数据格式化
   
       1.文件的使用
         文件内容的读取: .read()  .readline()  .readlines()
         数据的文件写入: .write()  .writelines()  .seek()
       2.一维数据的格式化和处理
         一维数据的表示：列表类型（有序）和集合类型（无序）
         一维数据的存储：空格分隔、逗号分隔、特殊符号分隔
         一维数据的处理：字符串方法 .split()和.join()
       3.二维数据的格式化和处理
         二维数据的表示：列表类型，其中每个元素也是一个列表
         CSV格式：逗号分隔表示一维，按行分隔表示二维
         二维数据的处理：for循环+.split()和.join()
         
         
        
         
        
            
      
      
     
     

        
            
        
         



        
                  
            
