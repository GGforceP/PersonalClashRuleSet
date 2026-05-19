使用方法：

        一.搭配substore（强烈推荐）：
        1.在“订阅”页面中，添加一个新的订阅，导入自己的订阅配置文件；
        2.然后再在“文件”页面中，添加一个新的mihomo配置文件；
        3.在下方的“JavaScript/YAML 覆写”设置中，添加一个新的“脚本操作”；
        4.选择“远程链接”，将本yaml的raw链接拷贝并复制在文本框中；
        5.先点击“即时预览”看看是否能正常拉取到脚本。
        6.是→点击保存，将生成的文件分享链接导入clash核心的代理软件，开始使用。
        7.否→想个办法连上github。再重复 6 。
        SubStore项目地址：https://github.com/sub-store-org/Sub-Store

        
        优势：
        ·一次部署，一劳永逸，后续不管进行任何规则修改操作，只需要在代理软件更新订阅，不需要任何其他操作。
        ·兼容性好，只要是clash/mihomo内核的代理软件（openclash、clash、clash mi、clash meta、flclash、stash、clash party、clash verge等）全都支持
        缺点：
        ·需要一台私有或云上服务器跑，如果需要wan访问，需要公网ip或者转发。
    
        二：直接在clash内核的代理软件中引用：
        以flclash为例：
        1.开启应用，进入“工具”页面，点击“进阶配置”；
        2.点击“脚本”，点击右上角“添加”；
        3.进入配置编辑页面后，点击右上角“···”，选择“外部获取”——“通过URL”导入；
        4.粘贴yaml的raw文件链接，下载配置文件，命名、保存后退出。、
        5.开启代理。
        优势：
        ·灵活性强，随时在自定义配置和默认配置切换。
        ·纯本地操作，无需另外的服务器跑，无公网ip要求，随时随地可用。
        缺点：
       ·兼容性差，有些代理软件不支持引用外部覆写资源。


鸣谢：@Aethersailor （Custom_OpenClash_Rules）
    项目地址：[Custom_OpenClash_Rules](https://github.com/Aethersailor/Custom_OpenClash_Rules)

由于本人主要使用openclash，因此主要为openclash服务，规则中使用的数据库均为openclash默认：

GEO数据库：    MMDB: [https://testingcf.jsdelivr.net/gh/alecthw/mmdb_china_ip_list@release/Country.mmdb](https://testingcf.jsdelivr.net/gh/alecthw/mmdb_china_ip_list@release/Country.mmdb)

GeoIP 数据库：    GEOIP: [https://testingcf.jsdelivr.net/gh/Loyalsoldier/v2ray-rules-dat@release/geoip.dat](https://testingcf.jsdelivr.net/gh/Loyalsoldier/v2ray-rules-dat@release/geoip.dat)

GeoSite 数据库：    GEOSITE: [https://testingcf.jsdelivr.net/gh/Loyalsoldier/v2ray-rules-dat@release/geosite.dat](https://testingcf.jsdelivr.net/gh/Loyalsoldier/v2ray-rules-dat@release/geosite.dat)

ASN：    ASN: [https://testingcf.jsdelivr.net/gh/xishang0128/geoip@release/GeoLite2-ASN.mmdb](https://testingcf.jsdelivr.net/gh/xishang0128/geoip@release/GeoLite2-ASN.mmdb)


如果有个性化需求的，可以fork一份，再自己编辑添加一些规则，geo规则库：[domain-list-community](https://github.com/v2fly/domain-list-community)
