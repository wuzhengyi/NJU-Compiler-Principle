# 编译原理第四章作业(2)
## 计科 吴政亿

<!-- TOC -->

- [编译原理第四章作业(2)](#编译原理第四章作业2)
    - [151220129 计科 吴政亿](#151220129-计科-吴政亿)
        - [4.6.2](#462)
        - [4.6.3](#463)
        - [4.6.6](#466)
        - [4.7.1](#471)

<!-- /TOC -->

### 2
1. 增广文法:

    (0)$S' \rightarrow S$   
    (1)$S \rightarrow S S +$   
    (2)$B \rightarrow S S *$   
    (3)$B \rightarrow a$   

2. SLR项集如下:   
- $I_0:S' \rightarrow \cdot S, S \rightarrow \cdot SS+, S \rightarrow \cdot SS*,S \rightarrow \cdot a$
- $I_1:S' \rightarrow a \cdot$
- $I_2:S' \rightarrow S \cdot , S \rightarrow S \cdot S+, S \rightarrow S \cdot S*,S \rightarrow \cdot SS+, S \rightarrow \cdot SS*,S \rightarrow \cdot a$
- $I_3:S' \rightarrow SS \cdot +, S \rightarrow SS \cdot *, S \rightarrow S \cdot S+,$   
    $\ \ \ \ \ \ \ S \rightarrow S \cdot S*,S \rightarrow \cdot SS+, S \rightarrow \cdot SS*,S \rightarrow \cdot a$
- $I_4:S' \rightarrow SS+ \cdot$
- $I_5:S' \rightarrow SS* \cdot$

3. GOTO 函数如下:   
$GOTO(I_0,a)=I_1$ , $GOTO(I_0,S)=I_2$      
$GOTO(I_2,a)=I_1$ , $GOTO(I_2,S)=I_3$ , $GOTO(I_2,$\$$)=accept$   
$GOTO(I_3,a)=I_1$ , $GOTO(I_3,S)=I_3$   
$GOTO(I_3,+)=I_4$ , $GOTO(I_3,*)=I_5$   

4. 语法分析表如下：

<table class="tg">
  <tr>
    <th class="tg-2n8g" rowspan="2">状态</th>
    <th class="tg-2n8g" colspan="4">ACTION</th>
    <th class="tg-2n8g">GOTO</th>
  </tr>
  <tr>
    <td class="tg-2n8g">a</td>
    <td class="tg-2n8g">+</td>
    <td class="tg-2n8g">*</td>
    <td class="tg-2n8g">$</td>
    <td class="tg-2n8g">S</td>
  </tr>
  <tr>
    <td class="tg-2n8g">0</td>
    <td class="tg-2n8g">S1</td>
    <td class="tg-2n8g"></td>
    <td class="tg-2n8g"></td>
    <td class="tg-2n8g"></td>
    <td class="tg-2n8g">2</td>
  </tr>
  <tr>
    <td class="tg-2n8g">1</td>
    <td class="tg-2n8g">r3</td>
    <td class="tg-2n8g">r3</td>
    <td class="tg-2n8g">r3</td>
    <td class="tg-2n8g">r3</td>
    <td class="tg-2n8g"></td>
  </tr>
  <tr>
    <td class="tg-2n8g">2</td>
    <td class="tg-2n8g">S1</td>
    <td class="tg-2n8g"></td>
    <td class="tg-2n8g"></td>
    <td class="tg-2n8g">accept</td>
    <td class="tg-2n8g">3</td>
  </tr>
  <tr>
    <td class="tg-2n8g">3</td>
    <td class="tg-2n8g">S1</td>
    <td class="tg-2n8g">S4</td>
    <td class="tg-2n8g">S5</td>
    <td class="tg-2n8g"></td>
    <td class="tg-2n8g">3</td>
  </tr>
  <tr>
    <td class="tg-2n8g">4</td>
    <td class="tg-2n8g">r1</td>
    <td class="tg-2n8g">r1</td>
    <td class="tg-2n8g">r1</td>
    <td class="tg-2n8g">r1</td>
    <td class="tg-2n8g"></td>
  </tr>
  <tr>
    <td class="tg-2n8g">5</td>
    <td class="tg-2n8g">r2</td>
    <td class="tg-2n8g">r2</td>
    <td class="tg-2n8g">r2</td>
    <td class="tg-2n8g">r2</td>
    <td class="tg-2n8g"></td>
  </tr>
</table>

无冲突，这显然是一个 SLR 文法

### 3

| 序号 | 栈   | 符号 | 输入   | 动作         |
|------|------|------|--------|--------------|
| (1)  | 0    |      | aa*a+$ | 移入         |
| (2)  | 01   | a    | a*a+$  | 按S->a规约   |
| (3)  | 02   | S    | a*a+$  | 移入         |
| (4)  | 021  | Sa   | *a+$   | 按S->a规约   |
| (5)  | 023  | SS   | *a+$   | 移入         |
| (6)  | 0235 | SS*  | a+$    | 按S->SS*规约 |
| (7)  | 02   | S    | a+$    | 移入         |
| (8)  | 021  | Sa   | +$     | 按S->a规约   |
| (9)  | 023  | SS   | +$     | 移入         |
| (10) | 0234 | SS+  | $      | 按S->SS+规约 |
| (11) | 02   | S    | $      | 接受         |

### 6

- 因为First(SA) = First(A) = {a}，所以该文法不是LL(1)的。
- 下证该文法是SLR(1)的：   
    1. 增广文法：   
        (0) $S' \rightarrow S$   
        (1) $S \rightarrow SA$   
        (2) $S \rightarrow A$   
        (3) $A \rightarrow a$   
    2. SLR项集:   
    - $I_0:S' \rightarrow \cdot S , S \rightarrow \cdot SA,S \rightarrow \cdot A , A \rightarrow \cdot a$
    - $I_1:A \rightarrow a \cdot$
    - $I_2:S \rightarrow A \cdot$
    - $I_3:S' \rightarrow S \cdot , S \rightarrow S \cdot A , A \rightarrow \cdot a$
    - $I_4:S \rightarrow SA \cdot$

    3. 语法分析表:

<table>
  <tr>
    <th rowspan="2">状态</th>
    <th colspan="2">ACTION</th>
    <th colspan="2">GOTO</th>
  </tr>
  <tr>
    <td>a</td>
    <td>$</td>
    <td>S</td>
    <td>A</td>
  </tr>
  <tr>
    <td>0</td>
    <td>S1</td>
    <td></td>
    <td>S2</td>
    <td>S3</td>
  </tr>
  <tr>
    <td>1</td>
    <td>r3</td>
    <td>r3</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>2</td>
    <td>r2</td>
    <td>r2</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>3</td>
    <td>S!</td>
    <td>acc</td>
    <td></td>
    <td>S4</td>
  </tr>
  <tr>
    <td>4</td>
    <td>r1</td>
    <td>r1</td>
    <td></td>
    <td></td>
  </tr>
</table>

因为没有重复的冲突项，故该文法为SLR（1）的。

### 1
1. 规范LR项集族

```
I0:
    [S' -> ·S  , $] 
    [S' -> ·SS+, $], [S' -> ·SS+, a]
    [S' -> ·SS*, $], [S' -> ·SS*, a]
    [S' -> ·a  , $], [S' -> ·a  , a]
I1:
    [S' -> a·  , $], [S' -> a·  , a]
I2:
    [S' -> S·  , $] 
    [S' -> S·S+, $], [S' -> S·S+, a]
    [S' -> S·S*, $], [S' -> S·S*, a]
    [S' -> ·SS+, a], [S' -> ·SS+, *], [S' -> ·SS+, +]
    [S' -> ·SS*, a], [S' -> ·SS*, *], [S' -> ·SS*, +]
    [S' -> ·a  , a], [S' -> ·a  , *], [S' -> ·a  , +]
I3:
    [S' -> a·  , a], [S' -> a·  , *], [S' -> a·  , +]
I4:
    [S' -> SS·+, $], [S' -> SS·+, a]
    [S' -> SS·*, $], [S' -> SS·*, a]
    [S' -> S·S+, a], [S' -> S·S+, *], [S' -> S·S+, +]
    [S' -> S·S*, a], [S' -> S·S*, *], [S' -> S·S*, +]
    [S' -> ·SS+, a], [S' -> ·SS+, *], [S' -> ·SS+, +]
    [S' -> ·SS*, a], [S' -> ·SS*, *], [S' -> ·SS*, +]
    [S' -> ·a  , a], [S' -> ·a  , *], [S' -> ·a  , +]
I5:
    [S' -> SS+·, $], [S' -> SS+·, a]
I6:
    [S' -> SS*·, $], [S' -> SS*·, a]
I7:
    [S' -> SS·+, a], [S' -> SS·+, *], [S' -> SS·+, +]
    [S' -> SS·*, a], [S' -> SS·*, *], [S' -> SS·*, +]
    [S' -> S·S+, a], [S' -> S·S+, *], [S' -> S·S+, +]
    [S' -> S·S*, a], [S' -> S·S*, *], [S' -> S·S*, +]
    [S' -> ·SS+, a], [S' -> ·SS+, *], [S' -> ·SS+, +]
    [S' -> ·SS*, a], [S' -> ·SS*, *], [S' -> ·SS*, +]
    [S' -> ·a  , a], [S' -> ·a  , *], [S' -> ·a  , +]
I8:
    [S' -> SS+·, a], [S' -> SS+·, *], [S' -> SS+·, +]
I9:
    [S' -> SS*·, a], [S' -> SS*·, *], [S' -> SS*·, +]
```

2. LALR项集族:
```
I0:
    [S' -> ·S  , $] 
    [S' -> ·SS+, $], [S' -> ·SS+, a]
    [S' -> ·SS*, $], [S' -> ·SS*, a]
    [S' -> ·a  , $], [S' -> ·a  , a]
I1:
    [S' -> S·  , $] 
    [S' -> S·S+, $], [S' -> S·S+, a]
    [S' -> S·S*, $], [S' -> S·S*, a]
    [S' -> ·SS+, a], [S' -> ·SS+, *], [S' -> ·SS+, +]
    [S' -> ·SS*, a], [S' -> ·SS*, *], [S' -> ·SS*, +]
    [S' -> ·a  , a], [S' -> ·a  , *], [S' -> ·a  , +]
I2:
    [S' -> SS·+, a], [S' -> SS·+, *], [S' -> SS·+, +], [S' -> SS·+, $]
    [S' -> SS·*, a], [S' -> SS·*, *], [S' -> SS·*, *], [S' -> SS·*, $]
    [S' -> S·S+, a], [S' -> S·S+, *], [S' -> S·S+, +]
    [S' -> S·S*, a], [S' -> S·S*, *], [S' -> S·S*, +]
    [S' -> ·SS+, a], [S' -> ·SS+, *], [S' -> ·SS+, +]
    [S' -> ·SS*, a], [S' -> ·SS*, *], [S' -> ·SS*, +]
    [S' -> ·a  , a], [S' -> ·a  , *], [S' -> ·a  , +]
I3:
    [S' -> a·  , a], [S' -> a·  , *], [S' -> a·  , +], [S' -> a·  , $]
I4:
    [S' -> SS+·, a], [S' -> SS+·, *], [S' -> SS+·, +], [S' -> SS+·, $]
I5:
    [S' -> SS*·, a], [S' -> SS*·, *], [S' -> SS*·, +], [S' -> SS*·, $]
```