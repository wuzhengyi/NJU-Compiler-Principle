# 第四章作业
![1](http://img.blog.csdn.net/20171011003348233?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvanVzdGljZTA=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
![2](http://img.blog.csdn.net/20171011003401501?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvanVzdGljZTA=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
![3](http://img.blog.csdn.net/20171011003411480?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvanVzdGljZTA=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
### 4.2.1
1. $S \rightarrow SS* \rightarrow SS+S* \rightarrow aS+S* \rightarrow aa+S* \rightarrow aa+a*$
2. $S \rightarrow SS* \rightarrow Sa* \rightarrow SS+a* \rightarrow Sa+a* \rightarrow aa+a*$
3. 如下图    
![4 2 1](https://f.cloud.github.com/assets/340282/469058/c08b4f9c-b6af-11e2-8236-f79c6a56215a.gif)
4. 略
5. 所有的后缀表达式的集合组成的加法和乘法

### 4.4.1
(5)$S\rightarrow (L) | a$ 以及$L\rightarrow L,S | S$   

1. 提取左公因子(无)
2. 消除左递归（仅有$L\rightarrow L,S|S$这一处立即左递归）   

    $S\rightarrow (L) | a$   
    $L\rightarrow SL'$   
    $L'\rightarrow ,SL'|\epsilon$

3. 计算First和Follow
    
```
    First(S)  = { ( , a }
    First(L)  = { ( , a }
    First(L') = { ，, ε }
    Follow(S) = { $ , ，, ) }
    Follow(L) = { ) }
    Follow(L')= { ) }
```

最终得到预测分析表：

<table>
    <thead>
        <tr>
            <th rowspan="2">非终结符号</th>
            <th colspan="5">输入符号</th>
        </tr>
        <tr>
            <th>(</th>
            <th>)</th>
            <th>,</th>
            <th>a</th>
            <th>$</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>S</th>
            <td>$S \rightarrow (L)$</td>
            <td></td>
            <td></td>
            <td>$S \rightarrow a$</td>
            <td></td>
        </tr>
        <tr>
            <th>S</th>
            <td>$L \rightarrow SL'$</td>
            <td></td>
            <td></td>
            <td>$L \rightarrow SL'$</td>
            <td></td>
        </tr>
        <tr>
            <th>L'</th>
            <td></td>
            <td>$L' \rightarrow \epsilon$</td>
            <td>$L' \rightarrow ,SL'$</td>
            <td></td>
            <td></td>
        </tr>
    </tbody>
</table>

### 4.4.2

- 提取左公因子
    
    $S \rightarrow SSA | a$   
    $A \rightarrow + | *$
    
- 消除左递归

```
    i = 1    
        S -> aB
        B -> SAB | ε
        A -> + | *
    i = 2
        j = 1
            S -> aB
            B -> aBAB | ε
            A -> + | *
```
  
- 预测分析表

<table>
    <thead>
        <tr>
            <th rowspan="2">非终结符号</th>
            <th colspan="4">输入符号</th>
        </tr>
        <tr>
            <th>+</th>
            <th>*</th>
            <th>a</th>
            <th>$</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>S</th>
            <td></td>
            <td></td>
            <td>S -> aB</td>
            <td></td>
        </tr>
        <tr>
            <th>A</th>
            <td>A -> +</td>
            <td>A -> *</td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <th>B</th>
            <td>B -> ε</td>
            <td>B -> ε</td>
            <td>B -> aBAB</td>
            <td>B -> ε</td>
        </tr>
    </tbody>
</table>

### 4.4.3 
- $First(S) = \{a\}$
- \(Follow(S) = \{a, +, *, \$\} \)

### 4.4.5 
1. 对于这个带回溯的递归下降分析器，   
    它每一次发现错误后回溯所消去的a的数量为2,4,8.....   
    即$2^n$，那么只有在a的个数为$\{a^{2^n} | n≥1\}$时,   
    假设为k，则他的预测a的个数为$2^k - 2^i,i=1,2,3...$,   
    当i等于k-1时匹配成功。   
    而对于六来说，只有3才能匹配，但是他不会经历这个情况。
2. 他识别$\{a^{2^n} | n≥1\}$的情况
### 4.5.2 
S -> SS+ -> Sa+ -> SS*a+ ->Sa*a+ -> SS+a*a+
因此句柄为SS+