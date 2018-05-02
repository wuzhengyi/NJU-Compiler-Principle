# 编译原理 作业8

**151220129 计科 吴政亿 nju_wzy@163.com**

## 6.4.3

![](C:\Users\91434\Documents\坚果云\NJU-Compiler-Principle\homework\8\6.4.3.png)

中间代码:

```
t1 = i * 16
t2 = j * 4
t3 = t1 + t2
t4 = b[t3]
t5 = t4 * 12
t6 = k * 4
t7 = c[t6]
t8 = t7 * 4
t9 = t5 + t8
t10 = a[t9]
x = t10
```



## 6.4.8

```
A[3,4,5] = [(3-1)*5*6 + (4-0)*6 +(5-5)] = 672
A[1,2,7] = [(1-1)*5*6 + (2-0)*6 +(7-5)] = 112
A[4,3,9] = [(4-1)*5*6 + (3-0)*6 +(9-5)] = 896
```




## 6.6.1

```
    S -> for (S1; B; S2) S3     S1.next = newlabel()
                                B.true = newlabel()
                                B.false = S.next
                                S2.next = S1.next
                                S3.next = newlabel()
                                S.code = S1.code
                                    || lable(S1.next) || B.code
                                    || lable(B.true) || S3.code
                                    || label(S3.next) || S2.code
                                    || gen('goto', S1.next)
```

