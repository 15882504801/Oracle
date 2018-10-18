# Oracle
首先我运行了查询一和查询二
<br>
截图如下
第一段查询语句的运行
<br>
![第一段查询语句的运行截图](https://github.com/15882504801/Oracle/blob/master/test1/运行1.jpg)
<br>
第二段查询语句的运行
<br>
![第二段查询语句的运行截图](https://github.com/15882504801/Oracle/blob/master/test1/运行2.jpg)
<br>
很明显，第一段查询语句运行的时间比第二段查询语句时间长
所以我认为第二段查询语句是最佳的。
我对第二段查询语句进行了优化指导
<br>
截图如下
<br>
![优化指导截图](https://github.com/15882504801/Oracle/blob/master/test1/优化.jpg)
<br>
结果并没有给我什么指导
然后我对比了两个查询语句的步骤
查询一
<br>
![详情截图](https://github.com/15882504801/Oracle/blob/master/test1/详情1.jpg)
<br>
查询二
br>
![详情截图](https://github.com/15882504801/Oracle/blob/master/test1/详情2.jpg)
<br>
查询一的步骤数明显比查询二的步骤数多
所以查询二是最佳的

接下来是我自己的代码
```
select initcap(concat(last_name,first_name)) "姓名" 
from employees
where initcap(concat(last_name,first_name)) like '%a%' 
and  initcap(concat(last_name,first_name)) like '%b%'
and  initcap(concat(last_name,first_name)) like '%c%';
```
分析：目的是查询员工中姓名包含字母a，b，c的人，首先通过表employees查询员工的姓名，然后条件是名字包含字母a,b,c
<br>
![运行3截图](https://github.com/15882504801/Oracle/blob/master/test1/运行3.jpg)
<br>
然后是优化指导
<br>
![优化2截图](https://github.com/15882504801/Oracle/blob/master/test1/优化3.jpg)
<br>
然而也并没有给我什么优化
感觉我软件有问题......
