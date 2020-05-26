# mockbank
test result
基本实现需求
读取文件路径path值可配置成常量 也可放入项目的resource中，通过GetResource.class.getClassLoader().getResource("xx/xx.txt").getPath();来获取
关于汇率转换 考虑到最后Map中的value为数据类型，破坏类型影响累加 就选择在输出的方法中通过字符串拼接简单实现 如果在实际项目中 倾向引入汇率转换相关的工具类进行转换输出（否者要手写很多case）
也可以将BANK的数据类型设为map<string,map<BigInteger,double>>：
我的基本思路就是把控制台和文档中输入的数据做合法校验，通过后放入ConcurrentHashMap（Bank）中，在bank中根据相同key值做累加，累加之后stream掉为0的数据并遍历输出，在输出判断非USD字段进行转换拼接字符串
通过线程的sleep实现每分钟输出一次，在累加过程中 给BANK加sync锁来实现线程的安全
