# 编译原理 作业六
**151220129 计科 吴政亿 18805156360**

### 5.4.3

先提取左公因子

$B \rightarrow B_1 d~|~1$   
$d \rightarrow 0~|~1$



消除左递归后得

$B \rightarrow 1~\{R.i = 1\}~R~\{B.val=R.val\}$   
$R \rightarrow d~\{R_1.i = 2*R.i+d.val\}~R_1~\{R.val=R_1.val\}$   
$R \rightarrow ~\epsilon~\{R.val=R.i\}$   
$d \rightarrow 0~\{d.val=0\}$  
$d \rightarrow 1~\{d.val=1\}$  