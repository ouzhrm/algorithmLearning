# 1、基本数据类型的包装类
* 一般先判断用instanceof判断是否一致，如果一致，再比较值。
~~~
底层代码如下：
举例Boolean吧：
    public boolean equals(Object obj) {
        if (obj instanceof Boolean) {
            return value == ((Boolean)obj).booleanValue();
        }
        return false;
    }
~~~
也就是说，比较的是值。

# 2、String
* 上代码：
~~~
    public boolean equals(Object anObject) {
        if (this == anObject) {
            return true;
        }
        if (anObject instanceof String) {
            String anotherString = (String) anObject;
            int n = value.length;
            if (n == anotherString.value.length) {
                char v1[] = value;
                char v2[] = anotherString.value;
                int i = 0;
                while (n-- != 0) {
                    if (v1[i] != v2[i])
                            return false;
                    i++;
                }
                return true;
            }
        }
        return false;
    }
~~~
String先比较地址，然后比较内容，内容是拆分成字符数组，一个一个字符对应比较。

# 3、对象类型的，Object
~~~
    public boolean equals(Object obj) {
        return (this == obj);
    }
~~~
直接比较的是地址。。。。
