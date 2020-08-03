# Test
第一阶段：python学习
（1）“温度转换”实例
      #TempConvert.py
      TempStr=input("请输入带有符号的温度值:")
      if TempStr[－1] in ['F','f']:
        C=(eval(TempStr[0:－1])－32)/1.8
        print("转换后的温度是{:.2f}C".format(C))
      elif TempStr[－1] in ['C','c']:
        F=1.8 * eval(TempStr[0:－1])+32
        print("转换后的温度是{:.2f}F".format(F))
      else:
        print("输入格式错误")
        
   自己认为比较重要的知识点：
   1.单行注释：以#开头
     多行注释：以'''开头和结尾
   2.字符串的使用：使用[]获取字符串中一个或多个字符
     索引：返回字符串中单个字符   <字符串>[M]  eg:TempStr[－1]  (表示获取字符串中的倒数第一个字符)
     切片:
