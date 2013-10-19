# 第45讲 hashCode与equals深度剖析与源码详解

**Object类**的equals方法的特定

* （1）自反性：x.equals(x)应该返回true
* （2）对称性：x.equals(y)为true，那么y.equals(x)也为true
* （3）传递性：x.equals(y)为true，并且y.equals(z)为true，那么x.equals(z)也应该为true
* （4）一致性：x.equals(y)的第一次调用为true，那么x.equals(y)的第二次、第三次、第n次调用也应该为true，前提条件是在
比较之间没有修改x也没有修改y。
* (5)对于非空应用x，x.equals(null)返回false。


































