# 编译原理 第三次作业

## 151220129 计科 吴政亿

### 4.4.1

无左公因子，消除左递归后得到: 

- bexpr $\rightarrow$ bterm bexpr'   
- bexpr' $\rightarrow$ **or** bterm bexpr' | $\epsilon$   
- bterm $\rightarrow$ bfactor bterm'  
- bterm' $\rightarrow$ **and** bfactor bterm' | $\epsilon$   
- bfactor $\rightarrow$ **not** bfactor | (bexpr) | **true** | **false**

First(bexpr) = First(bterm) = First(bfactor) = {**not**,(,**true**,**false**}   
First(bexpr') = {**or**, $\epsilon$}   
First(bterm) = {**and**, $\epsilon$}   
Follow(bexpr) = Follow(bexpr') = { ), $ }   
Follow(bterm) = Follow(bterm') = { or, $ }   
Follow(bfactor) = { and, $ }   

预测分析表：
<table>
    <thead>
        <tr>
            <th rowspan="2">非终结符号</th>
            <th colspan="8">输入符号</th>
        </tr>
        <tr>
            <th>and</th>
            <th>or</th>
            <th>not</th>
            <th>(</th>
            <th>)</th>
            <th>true</th>
            <th>false</th>
            <th>$</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>bexpr</th>
            <td></td>
            <td></td>
            <td>bexpr -> bterm bexpr'</td>
            <td>bexpr -> bterm bexpr'</td>
            <td></td>
            <td>bexpr -> bterm bexpr'</td>
            <td>bexpr -> bterm bexpr'</td>
            <td></td>
        </tr>
        <tr>
            <th>bexpr'</th>
            <td></td>
            <td>bexpr' -> or bterm bexpr'</td>
            <td></td>
            <td></td>
            <td>bexpr' -> ε</td>
            <td></td>
            <td></td>
            <td>bexpr' -> ε</td>
        </tr>
        <tr>
            <th>bterm</th>
            <td></td>
            <td></td>
            <td>bterm -> bfactor bterm'</td>
            <td>bterm -> bfactor bterm'</td>
            <td></td>
            <td>bterm -> bfactor bterm'</td>
            <td>bterm -> bfactor bterm'</td>
            <td></td>
        </tr>
        <tr>
            <th>bterm'</th>
            <td></td>
            <td>bterm' -> and bfactor bterm'</td>
            <td></td>
            <td></td>
            <td>bterm' -> ε</td>
            <td></td>
            <td></td>
            <td>bterm' -> ε</td>
        </tr>
        <tr>
            <th>bfactor</th>
            <td></td>
            <td></td>
            <td>bfactor -> not bfactor</td>
            <td>bfactor -> (bexpr)
            <td></td>
            <td>bfactor -> true</td>
            <td>bfactor -> false</td>
            <td></td>
        </tr>
    </tbody>
</table>

### 4.4.4

- First(S) = { (, $\epsilon$ }
- FollowS(S) = { ), $ }

### 4.4.5

1. 对于这个带回溯的递归下降分析器，   
    它每一次发现错误后回溯所消去的a的数量为2,4,8.....   
    即$2^n$，那么只有在a的个数为$\{a^{2^n} | n≥1\}$时,   
    假设为k，则他的预测a的个数为$2^k - 2^i,i=1,2,3...$,   
    当i等于k-1时匹配成功。   
    而对于六来说，只有3才能匹配，但是他不会经历这个情况。
2. 他识别$\{a^{2^n} | n≥1\}$的情况

### 4.5.2

S   $\Rightarrow$ S S + 
    $\Rightarrow$ S S S + + 
    $\Rightarrow$ S S a + + 
    $\Rightarrow$ S S S * a + +    
$~~~ \Rightarrow$ S S a * a + +
    $\Rightarrow$ S a a * a + +
    $\Rightarrow$ a a a * a + + 