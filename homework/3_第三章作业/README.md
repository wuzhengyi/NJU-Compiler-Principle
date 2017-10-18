# 151220129 计科 吴政亿
###厚书 3.3.2
(3) 由a与b组成的，后缀为aaa,aab,aba,abb的串

###厚书 3.3.5
定义β为所有非元音小写字母的集合，则其正则表达式为$β^* a(a│β)^* e(e│β)^* i(i│β)^* o(o│β)^* u(u│β)^*$

###厚书 3.4.1
![1](http://img.blog.csdn.net/20170922085208205?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvanVzdGljZTA=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

![2](http://img.blog.csdn.net/20170922082156462?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvanVzdGljZTA=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

![34](http://img.blog.csdn.net/20170922085236963?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvanVzdGljZTA=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

###厚书 3.6.4
1. 0->1->0->1->2->3
2. 0->3->0->1->2->3

接受

###厚书 3.6.5
(2) 

状态 |    a   |   b   | $\varepsilon$
-----|-----|-----|-----
0   |{1}    |$\phi$ |{3}
1   |$\phi$ |{2}    |{0}
2   |$\phi$ |{3}    |{1}
3   |{0}    |$\phi$ |{2}     

###厚书 3.7.1
(3)一个状态

NFA状态   |DFA状态  |a  |b
--|--|--|--
{0,1,2,3}|A|A|A

![3.7.1](http://img.blog.csdn.net/20170922082156462?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvanVzdGljZTA=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)