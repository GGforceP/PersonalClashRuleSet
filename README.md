# 自用clash、clashmeta规则模板
芜湖起飞~~
先占个坑，以后慢慢的来弄


发现AI输出文本的时候，不能一次性输出太多的内容，于是例如国内域名、IP、端口这些规则，没法一次性全部收集完，于是在github找了找，最终决定直接引用ACL4SSR的一部分规则，省力点，哈哈

致谢[@ACL4SSR](https://github.com/ACL4SSR)



编写yaml的时候，发现导入clash之后，格式有问题，最终在clash party的帮助下解决yaml格式排版的问题

致谢[@clash-party](https://github.com/mihomo-party-org/clash-party)

更新日志：本来懒得写，又怕以后屎山堆起来了，不知道改了些啥，还是留个记录

    25.12.21：冬至
    
        1.优化了下常用AI规则，大文件拆分成各个小文件，方便后期维护
        
        2.优化了下AI规则集，去除KEYWORD和ASN匹配，提高了匹配精确度，降低了误匹配概率

