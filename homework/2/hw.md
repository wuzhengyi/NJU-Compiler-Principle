# 151220129 计科 吴政亿

### 厚书 3.7.1
(2)一个状态

$\epsilon-closure(0)=\{0\}=A$   
$Dtran[A,a] = \epsilon-closure(0,1) = \{0,1\} = B$   
$Dtran[A,b] = \epsilon-closure(0) = A$   
$Dtran[B,a] = \epsilon-closure(0,1,2) = \{0,1,2\} = C$   
$Dtran[B,b] = \epsilon-closure(0,1) = B$   
$Dtran[C,a] = \epsilon-closure(0,1,2) = C$   
$Dtran[C,b] = \epsilon-closure(0,1,2,3) = D$   
$Dtran[D,a] = \epsilon-closure(0,1,2) = C$   
$Dtran[D,b] = \epsilon-closure(0,1,2,4) = D$   

| NFA       | DFA | a   | b   |
| --------- | --- | --- | --- |
| {0}       | A   | B   | A   |
| {0,1}     | B   | C   | B   |
| {0,1,2}   | C   | C   | D   |
| {0,1,2,3} | D   | C   | D   |

### 4.2.1
1. $S \rightarrow SS* \rightarrow SS+S* \rightarrow aS+S* \rightarrow aa+S* \rightarrow aa+a*$   
2. $S \rightarrow SS* \rightarrow Sa* \rightarrow SS+a* \rightarrow Sa+a* \rightarrow aa+a*$   
3. 如下图    
![4 2 1](https://f.cloud.github.com/assets/340282/469058/c08b4f9c-b6af-11e2-8236-f79c6a56215a.gif)   
4. 略   
5. 所有加法和乘法混合的a的后缀表达式集合

