# [编译原理] 第四次作业
**151220129 计科 吴政亿 18805156360@163.com**

### 4.5.3

<table>
    <thead>
        <tr>
            <th>栈</th>
            <th>输入</th>
            <th>句柄</th>
            <th>动作</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>$</td>
            <td>aaa*a++$</td>
            <td></td>
            <td>移入</td>
        </tr>
        <tr>
            <td>$a</td>
            <td>aa*a++$</td>
            <td>a</td>
            <td>规约: S -> a</td>
        </tr>
        <tr>
            <td>$S</td>
            <td>aa*a++$</td>
            <td></td>
            <td>移入</td>
        </tr>
        <tr>
            <td>$Sa</td>
            <td>a*a++$</td>
            <td>a</td>
            <td>规约: S -> a</td>
        </tr>
        <tr>
            <td>$SS</td>
            <td>a*a++$</td>
            <td></td>
            <td>移入</td>
        </tr>
        <tr>
            <td>$SSa</td>
            <td>*a++$</td>
            <td>a</td>
            <td>规约: S -> a</td>
        </tr>
        <tr>
            <td>$SSS</td>
            <td>*a++$</td>
            <td></td>
            <td>移入</td>
        </tr>
        <tr>
            <td>$SSS*</td>
            <td>a++$</td>
            <td>SS*</td>
            <td>规约: S -> SS*</td>
        </tr>
        <tr>
            <td>$SS</td>
            <td>a++$</td>
            <td></td>
            <td>移入</td>
        </tr>
        <tr>
            <td>$SSa</td>
            <td>++$</td>
            <td>a</td>
            <td>规约: S -> a</td>
        </tr>
        <tr>
            <td>$SSS</td>
            <td>++$</td>
            <td></td>
            <td>移入</td>
        </tr>
        <tr>
            <td>$SSS+</td>
            <td>+$</td>
            <td>SS+</td>
            <td>规约: S -> SS+</td>
        </tr>
        <tr>
            <td>$SS</td>
            <td>+$</td>
            <td></td>
            <td>移入</td>
        </tr>
        <tr>
            <td>$SS+</td>
            <td>$</td>
            <td>SS+</td>
            <td>规约: S -> SS+</td>
        </tr>
        <tr>
            <td>$S</td>
            <td>$</td>
            <td></td>
            <td>接受</td>
        </tr>
    </tbody>
</table>

### 4.6.2

![](https://img-blog.csdn.net/20180403203930980?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2p1c3RpY2Uw/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

Follow(S) = {+ , *, $ , a}

| GOTO函数表 | +     | *     | $      | a     | S     |
|---------|-------|-------|--------|-------|-------|
| $I_0$   |       |       |        | $I_2$ | $I_1$ |
| $I_1$   |       |       | ACCEPT | $I_2$ | $I_3$ |
| $I_2$   |       |       |        |       |       |
| $I_3$   | $I_4$ | $I_5$ |        | $I_2$ | $I_3$ |
| $I_4$   |       |       |        |       |       |
| $I_5$   |       |       |        |       |       |


下面对其进行编号
1. S -> SS+
2. S -> SS*
3. S -> a

得到SLR语法分析表:

![slr](https://img-blog.csdn.net/20180403211914653?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2p1c3RpY2Uw/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

因为无冲突，所以是SLR文法。

### 4.6.3

| 栈    | 符号  | 输入     | 动作         |
|------|-----|--------|------------|
| 0    |     | aa*a+$ | 移入         |
| 02   | a   | a*a+$  | 按照S->a归约   |
| 01   | S   | a*a+$  | 移入         |
| 012  | Sa  | *a+$   | 按照S->a归约   |
| 013  | SS  | *a+$   | 移入         |
| 0135 | SS* | a+$    | 按照S->SS*归约 |
| 01   | S   | a+$    | 移入         |
| 012  | Sa  | +$     | 按照S->a归约   |
| 013  | SS  | +$     | 移入         |
| 0134 | SS+ | $      | 按照S->SS+归约 |
| 01   | S   | $      | 接受         |

### 4.6.6

1. 该文法不是 LL(1) 的

    `S -> SA` 和 `S -> A` 均能推导出以 a 开头的串，所以不是 LL(1) 的

2. 该文法是 SLR(1) 的

    该文法生成的语法分析表是没有冲突的
