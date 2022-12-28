```python
import numpy as np
import matplotlib
import matplotlib.pyplot as plt
```


```python
import csv
```


```python
head = ["班级","学号", "姓别", "Python高级应用", "人工智能基础", "机器学习"] #csv文件第一行科目
```


```python
for i in range(1,9):# 用for循环写8个班的csv文件
    filename = "计算机190" + str(i) + ".csv"#创建1~8班的文件名
    file = open(filename, 'w',newline='')
    w = csv.writer(file)
    w.writerow(head)#将列名写入文件第一行
    student_num = np.random.randint(40,46)  #每个班随机人数为40~45人
    for student_id in range(1,student_num+1):#用for循环在csv文件中生成学号
        class_name = "计算机190" + str(i)#加入班级如，1903，3班
        if student_id < 10:# 生成学号
            student_id = "195150" + str(i) + "0" + str(student_id)#若小于10自动补0，避免学号不同长度，如1，即为195150i01
        else:
            student_id = "195150" + str(i) + str(student_id)#若大于10，即195150i14
        if np.random.randint(0,2) == 0:## 随机生成性别
            sex = "男"
        else:
            sex = "女"
        classdata = [class_name,str(student_id),sex]  # 生成数据，班级，学号，性别，并追加到classdata中
        for score in range(3):#生成3科成绩
            score = np.random.normal(70,9,size = (1))#生成一组服从正太分布随机成绩，平均70分左右,方差为10
            classdata.append(int(score))#数据转为int类型，为了方便后面的运算
        w.writerow(classdata)#写入csv中
    file.close()#关闭写入文件
    with open(filename,"r") as f:#读取文件
        data = np.loadtxt(f,str,delimiter = ',')  #利用循环，从1到8班，分别计算在python高级应用，人工智能，机器学习中计算出，最高分，最低分，平均分，中位数，标准差
    score_pygjyy = data[1:,3].astype(dtype = 'int16')
    print("班级：","",class_name,"班","python高级应用：最高分:",score_pygjyy.max(),"最低分:",score_pygjyy.min(),"平均分:",score_pygjyy.mean(),"中位数：",np.median(score_pygjyy),"标准差：",int(score_pygjyy.std()))
    score_rgzn = data[1:,4].astype(dtype = 'int16')
    print("人工智能：最高分:",score_rgzn.max(),"最低分:",score_rgzn.min(),"平均分:",score_rgzn.mean(),"中位数：",np.median(score_rgzn),"标准差：",int(score_rgzn.std()))
    score_jqxx = data[1:,5].astype(dtype = 'int16')
    print("机器学习：最高分:",score_jqxx.max(),"最低分:",score_jqxx.min(),"平均分:",score_jqxx.mean(),"中位数：",np.median(score_jqxx),"标准差：",int(score_jqxx.std()))

```

    班级：  计算机1901 班 python高级应用：最高分: 84 最低分: 46 平均分: 68.16666666666667 中位数： 69.5 标准差： 9
    人工智能：最高分: 97 最低分: 44 平均分: 70.07142857142857 中位数： 70.5 标准差： 10
    机器学习：最高分: 88 最低分: 47 平均分: 68.69047619047619 中位数： 69.0 标准差： 9
    班级：  计算机1902 班 python高级应用：最高分: 91 最低分: 53 平均分: 69.86363636363636 中位数： 68.0 标准差： 9
    人工智能：最高分: 100 最低分: 51 平均分: 69.29545454545455 中位数： 68.5 标准差： 8
    机器学习：最高分: 94 最低分: 53 平均分: 71.13636363636364 中位数： 69.5 标准差： 9
    班级：  计算机1903 班 python高级应用：最高分: 83 最低分: 50 平均分: 69.86046511627907 中位数： 71.0 标准差： 8
    人工智能：最高分: 88 最低分: 54 平均分: 68.4186046511628 中位数： 67.0 标准差： 9
    机器学习：最高分: 87 最低分: 51 平均分: 70.11627906976744 中位数： 70.0 标准差： 7
    班级：  计算机1904 班 python高级应用：最高分: 95 最低分: 47 平均分: 70.23809523809524 中位数： 71.5 标准差： 11
    人工智能：最高分: 90 最低分: 53 平均分: 70.14285714285714 中位数： 69.0 标准差： 9
    机器学习：最高分: 87 最低分: 45 平均分: 68.88095238095238 中位数： 68.0 标准差： 9
    班级：  计算机1905 班 python高级应用：最高分: 85 最低分: 47 平均分: 70.54545454545455 中位数： 70.0 标准差： 8
    人工智能：最高分: 86 最低分: 41 平均分: 69.68181818181819 中位数： 69.5 标准差： 8
    机器学习：最高分: 86 最低分: 54 平均分: 69.11363636363636 中位数： 69.0 标准差： 7
    班级：  计算机1906 班 python高级应用：最高分: 92 最低分: 52 平均分: 70.23255813953489 中位数： 72.0 标准差： 9
    人工智能：最高分: 88 最低分: 52 平均分: 70.51162790697674 中位数： 69.0 标准差： 9
    机器学习：最高分: 89 最低分: 55 平均分: 70.69767441860465 中位数： 70.0 标准差： 7
    班级：  计算机1907 班 python高级应用：最高分: 95 最低分: 44 平均分: 68.63636363636364 中位数： 70.0 标准差： 11
    人工智能：最高分: 89 最低分: 54 平均分: 71.5 中位数： 72.5 标准差： 7
    机器学习：最高分: 86 最低分: 51 平均分: 68.77272727272727 中位数： 70.5 标准差： 8
    班级：  计算机1908 班 python高级应用：最高分: 88 最低分: 51 平均分: 70.23809523809524 中位数： 69.5 标准差： 7
    人工智能：最高分: 94 最低分: 50 平均分: 69.95238095238095 中位数： 70.0 标准差： 8
    机器学习：最高分: 88 最低分: 55 平均分: 72.35714285714286 中位数： 71.0 标准差： 8
    


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```
