#### AI课前导学

python基本库：（numpy pandas）数据分析+人工智能的基础

​				sklearn 数据挖掘+人工智能基础

可视化工具： 	Matplotlib、seborn、Excel、POWERBI、Tableau、SPSS

python是综合学科：python web 爬虫 数据分析

​				数据分析岗：监控数据 给出一些决策建议（商业数据分析模式）

#### Jupter基础

##### 单元格介绍

cell单元格有两种<b>【状态】</b>：

选中状态：没有光标闪动，此时可以对整个单元格操作、比如删除单元格、新增一个单元格、复制、粘贴、撤销、切换模式

编辑状态：能看到光标在闪动，此时可以在单元格内部写代码或文本
编辑状态——>选中状态：按esc
选中状态——>编辑状态：按下enter

单元格有两个<b>【模式】</b>

Code 编码模式：运行代码，运行当前选中单元格：Ctrl+Enter

Markdown 文本模式：识别md语法

两个模式切换：Code——>Markdown 在单元格选中状态下按下M，Y切回

##### 单元格操作

前提：保证单元格处于选中状态

1. 新增单元格 按B在选中单元格下方新增，按A在选中单元格上方新增
2. 删除单元格 双击D删除选中单元格
3. 剪切单元格  按X   剪切选中单元格
4. 复制单元格  按C   复制选中单元格
5. 粘贴单元格  按V   粘贴粘贴板里的单元格
6. 撤销单元格  按Z   撤销上一次的单元格操作
#### ipython使用技巧

##### 运行外部python文件

%run test.py	运行外部python文件，相当于把整个文件的资源加载到jupyter notebook中了。所以py文件中所有的变量、函数等都可以直接使用

##### 运行计时

% 表示检测一行代码

%% 表示检测多行代码

time 代码运行一次

times 代码运行多次求平均时间

#### numpy

numpy 提供了一种数组类型，高维数组，提供了数据分析的运算基础（业务表一般就是二维）

##### 1. 创建列表

使用np.array()由python List 创建

数组的概念：数据类型一致的一个连续的内存空间

python  列表（c语言说：列表其实就是一个指针数组），列表不要求数据类型一致

numpy的数组：同样是一个<b>有序</b>的，<b>相同数据类型</b>的集合

<b>注意</b>:

* numpy默认ndarray的所以元素的类型是相同的
* 如果传进来的列表中包含不同的类型，则会统一为同一类型，优先级：str>float>int

##### 2. 使用np的routines函数创建

##### 回顾

1. 查看文档：shift+tab

2. 输入输出历史：In Out

3. %time %timeit  %%time %%timeit

numpy:

1. 特点：数据类型相同的有序数据集合，如果初始化数据类型不同，会强制类型统一。优先级：str>float>int

2. 构造：np.array(list)

   ​           np.ones(shape,dtype)    np.zeros()   np.full(shape,dtype,fill_value)

   ​	   np.eye(N)

   ​	    np.linspace(start, stop, num)    np.arange([start], stop, [step])

   ​	    np,random.randint()   

   ​	     np.random.randn()   

   ​	     np.random.normal()

   ​	     np.random.random()
   ​    	np.random.permutation()

3. 属性：ndim  shape  size  dtype

4. 索引：访问元素：arr[index1,index2,index3.....]

   ​            访问行：arr[行索引]

   ​	    访问列：arr[:,列索引]

   ​	    特殊的访问方式：使用列表（索引列表，bool列表）

5. 切片：在每一个维度上指定切片范围

   ​	    eg.  arr[rowindex1:rowindex2, colindex1:colindex2]

6. 聚合运算：sum()  mean() std() var()  argmax()  argmin() np.median()

   ​		   any()   all()    经常与逻辑表达式配合，比如查询一组数据中大于均值的所有数
7. 广播运算：

   * 缺失维度补1

   * 用已有值填充

​		最终目的：保证参与运算的两个数组形状一致

​		array+ num

8. 排序

   ​	np.sort()   快速排序，堆排序

   ​	np.partition()

#### pandas

numpy array  提供运算基础

pandas 提供了业务逻辑的处理方法

Series（一维）, DataFrame（二维）

构造：

Series(data,index)  Series(data=dic,index)

读取DataFrame

索引访问：

​	字典的访问：s[key]

​	下标访问：s[index]

​	loc访问：s.loc[key]

​	iloc访问：s.iloc[index]

​	列表访问：结合上面4种访问

​	BOOL列表访问：list,numpy,长度匹配

​				      series  长度匹配，索引匹配

切片操作：

​		注意：索引操作都是闭区间，下标操作都是开区间

​	下标：s[index1:index2]

​	loc iloc

常规操作

​		属性访问：index，values, dtype,shape

​		查看头尾n个元素：head(), tail()

​		isnull(), notnull()  配合any(), all()

​		值排序：sort_values(ascending=True)

​		索引排序：sort_index()

​		统计元素次数：values_counts()

​		去重操作：unique()   [A, B, A, B, C]——>[A, B, C]

运算：

​	Series + num	广播

​	Series+ numpy	先转换为numpy类型再运算

​	Series +Series 	索引对齐，不对齐补空值

​	操作函数：add, sub, mul,div

​	或者可以先处理空值再运算

DataFrame

构造：

​	DataFrame(data,index, columns)

​	DataFrame(data=dic, index)

​	pd.read_excel(io, sheet_name, header, index_col)

​	DataFrame(series )

访问：

​	访问列：df[column]

​	访问行：df.loc[index]

​	访问元素：df.loc[index, column]

​	访问方式都可以结合列表\切片操作

​	间接访问(只读)、直接访问（读写）

​	【注意】直接用[]访问，索引是列索引，切片是行切片

运算：

​	聚合运算：默认是列方向的聚合，axis修改聚合方向

​	DataFrame +num 	广播

​	DataFrame + numpy  ——>  	df.values+numpy  广播	

 	DataFrame + Series  ——>	df.add(s, axis=0\1)  指定索引方向

​	DataFrame +DataFrame  索引对齐







1多层级索引表

​	如果格式有问题，可以先把excel里面的数据规范一下，让索引处于第一列或者第一行

​	pd.read_excel(io,header=[], index_col)

​	构造多层级：

​		pd.MultiIndex.from_product([[A,B], [1,2,3]])

​		pd.MultiIndex.from_arrays([[A,A,A,B,B,B], [1,2,3,1,2,3]])

​	多层级访问：

​		索引的表达方式使用(level1, level2, ....leveln)

​		df.loc[index, column]

​		s.loc[index]

​		隐式索引处理不受多层级索引影响

​		把多层级索引变成单层级索引再访问，属于间接访问，读操作可以，读写不安全

​	多层级索引的变形（stack,unstack）

​		stack(level) level指定索引的层级，由内向外-1.-2.-n..

​	聚合同层级索引的聚合

2级联和合并

​	pd.concat((), axis, join, keys, join_axes, ignore_index)

​			()接受的索引dataFrame对象

​			axis 控制级联的一个方向，axis=0纵向连接，axis=1横向连接

​			join: inner, 保留级联方向上索引的交集，outer保留级联方向上索引的并级

​			ignore_index:True, False,忽略索引，重新排列（以整数）

​			keys：保留原始索引，增加索引的级数

​	df.append() 简洁的纵向连接的方法

​	应用场景：相同的表结构进行汇总	 

​	

​	pd.merge(left ,right, how, on, left_on, right_on, left_index, right_index, suffiexes, )

​		left, right 参与合并的左表和右表

​		how: inner outer left right	【内容上的交集或并集】

​		on:两张表中有多个字段相同，但是我们只希望根据其中的一个或几个进行合并

​		suffiexes:为字段名相同且不参与合并的列标签添加后缀

​		left_on, right_on:如果两张表中希望合并的列名字不同，可以分别指定列名称

​		left_index, right_index: 如果某张表希望以行索引作为合并列，使用这两个参数开启，True, False

​	注意事项：

		* 合并只列相关，跟行没关
		* 合并的时候，和列名称没关系，跟内容有关，主要看两个列的内容是否存在一对一，一对多，多对多的关系
		* 合并的列，最好选离散型的列，不要选数值型（连续型）

扩展的两个方法：

​		df.set_index(列标签) 把某一列设置为行索引

​		df.drop() 删除行或列

​		df.drop(index, axis=0， inplace=True) 删除行

​		df.drop(index, axis=1) 删除列
