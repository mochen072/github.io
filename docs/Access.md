# Access注入
## <font color = #1E90FF>Access结构</font>
1. <B> 以.mdb后缀命名<B>
2. <B>一个文件就是一个库，和MySQL不同<B>
3. <B>打开方式用ffice或者第三方工具<B>
4. <B>表名-字段名-数据内容<B>

## <font color = #1E90FF>注入流程</font>
1. <B>判断注入是否存在<B>
2. <B>猜解表名<B>
3. <B>猜解字段数<B>
4. <B>猜解字段名<B>
5. <B>猜解内容长度<B>
6. <B>猜解内容<B>

### <font color = #FF0000>判断注入</font>

1. <B>单引号报错<B>
2. <B>逻辑型 And 1=1 and 1=2<B>
3. <B>变量做运算 - 减号<B>
