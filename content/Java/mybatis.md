---
title : Mybatis
date : 2017-8-29 14:19
updated : 2017-8-29 14:20
collection : Java框架
---

### xml中特殊字符转义

```text
&lt;       <   小于

&lt;=      <=   小于或等于

&gt;       >    大于

&gt;=      >=    大于或等于

&lt;&gt;   <>   不等于

&amp;      &

&apos;     '

&quot;     "
```

也可以使用<[CDATA[ ]]>符号进行说明，将此类符号不进行解析 比如写 < > = 等

```xml
<![CDATA[ 这里写你的sql ]]>  
```

mysql like的写法

```sql
like concat('%',#{param},'%')  或者 like '%${param}%' ，推荐使用前者，可以避免sql注入。
```

[IDEA中使用Mybatis Generator](https://blog.csdn.net/u014330421/article/details/78805087)