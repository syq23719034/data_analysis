# data_analysis

1)scripts/stats.py（数据分析脚本）</br>
-
####1.使用方法</br>
python  scripts/stats.py    输入dataframe所在csv    输出dataframe所在csv    待分析特征变量</br>

####2.使用例子</br>
python  scripts/stats.py    'd:\age.csv'    'd:\output.csv'    'age'</br>

####3.参数解释</br>
输入dataframe</br>
<table>
<tr><td></td><td>UserId</td><td>age</td></tr>
<tr><td>0</td><td>27226838</td><td>22</td></tr>
<tr><td>1</td><td>28297563</td><td>30</td></tr>
<tr><td>2</td><td>27951286</td><td>27</td></tr>
<tr><td>3</td><td>27865599</td><td>24</td></tr>
<tr><td colspan="3">...</td></tr>
</table>

输出dataframe(字段解释清移步wiki)</br>
age,cnt_rec,cnt_target,%target,%cnt_rec,%cnt_target,%cum_cnt_rec,%cum_cnt_target,cnt_nontarget,%cnt_nontarget,%cum_nontarget,%cum_target-%cum_nontarget </br>
18,110,9.0,8.18%,0.36%,0.53%,0.36%,0.53%,101.0,0.35%,0.35%,0.18%</br>
19,479,22.0,4.59%,1.57%,1.30%,1.93%,1.84%,457.0,1.59%,1.94%,-0.28%</br>
20,1006,45.0,4.47%,3.30%,2.67%,5.23%,4.50%,961.0,3.34%,5.27%,-0.67%</br>
21,1765,77.0,4.36%,5.79%,4.56%,11.01%,9.06%,1688.0,5.86%,11.14%,-1.30%</br>
22,1825,69.0,3.78%,5.98%,4.09%,17.00%,13.15%,1756.0,6.10%,17.23%,-2.01%</br>
23,1865,82.0,4.40%,6.11%,4.86%,23.11%,18.01%,1783.0,6.19%,23.42%,-1.33%</br>
24,1931,118.0,6.11%,6.33%,6.99%,29.44%,25.00%,1813.0,6.29%,29.72%,0.70%</br>


2)scripts/woe.py（计算woe和iv脚本）</br>
-
####1.使用方法</br>
python  scripts/woe.py    输入dataframe所在csv    待分析特征变量   分段表达式（用逗号连接）  y变量</br>

####2.使用例子</br>
python  scripts/woe.py    "age.csv" "age" "20,30,45" "is_dft"</br>

####3.参数解释</br>
输入dataframe</br>
	UserId	       age     is_dft</br>
0	27226838	22     1 </br>
1	28297563	30     1</br>
2	27951286	27     0</br>
3	27865599	24     1</br>
4	2042801	        27     0</br>
5	28624643	37     1</br>
6	28769069	28     1</br>
...</br>

输出结果</br>
      class  good    bad  %good    %bad    all      woe        iv</br>
0  (0,20.0]    76   1519  4.76%  95.24%   1595 -6.34584  0.048765</br>
1   (20,30]   895  17129  4.97%  95.03%  18024 -8.75549  0.561679</br>
2   (30,45]   673  10021  6.29%  93.71%  10694  7.31007  0.372628</br>
3   (45...)    75    869  7.94%  92.06%    944  2.57974  0.036832</br>
4        NA     0      0   nan%    nan%      0      NaN  0.000000</br>
             1688  28819  5.53%  94.47%  30507           1.019905</br>
