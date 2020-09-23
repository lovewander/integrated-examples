这里是科学上网的优化集成配置示例。如是不太了解科学上网，建议先依次从简单到复杂参考及部署。

单一应用集成服务器端配置示例  
1、v2ray(vless\vmess+ws+tls)+caddy2\nginx （之前vmess协议时代，推荐部署。）  
2、v2ray(vless\vmess+h2)+caddy2 （h2优势：链路复用。）  
3、v2ray(SS+v2ray-plugin+tls)+caddy2\nginx（不常用，如需直接使用shadowsocks客户端可部署。）  
4、v2ray(vless+tcp+tls)+caddy2 （vless tcp应用下回落给caddy2。）  
5、v2ray(vless+tcp+tls)+nginx （vless tcp应用下回落给nginx。）  

综合应用集成服务器端配置示例  
1、v2ray为主，caddy2为辅。  
1）、v2ray(vless+tcp+tls+ws)+caddy2 （目前推荐部署，同时支持tcp与ws，回落给caddy2。）  
2）、v2ray(complete-tcp)+caddy2 （不含vless+tcp的v2ray综合应用。）  
3）、v2ray(complete)+caddy2 （v2ray综合应用。）  
4）、v2ray(complete)+naiveproxy （上一项应用+naiveproxy。）  
5）、v2ray(complete)+naiveproxy+trojan（上一项应用+trojan。各程序监听端口对外公开，同级对等。）  
6）、v2ray(complete)+naiveproxy+trojan+nginx （用nginx对上一项应用进行SNI分流，共用443端口。）  
2、v2ray为主，nginx为辅。  
1）、v2ray(vless+tcp+tls+ws)+nginx （目前推荐部署，同时支持tcp与ws，回落给nginx。）  
2）、v2ray(complete-h2)+nginx （不含vless\vmess+h2的v2ray综合应用。）  
3）、v2ray(complete-h2)+nginx+trojan（上一项应用+trojan。）  
4）、v2ray(complete-h2)+nginx+trojan+naiveproxy （上一项应用+naiveproxy。）  
注：  
1、naiveproxy=caddy2+forwardproxy。此程序文件已编译好，本github下载即可。  
2、complete表示包含v2ray的vless+tcp、vless\vmess+ws、vless\vmess+h2、SS+v2ray-plugin、vmess+kcp+seed的综合应用。  

service  
各程序service文件目录

client  
各客户端配置示例目录

贡献指南  
欢迎你将自己使用的配置制作模板，提交 PR。
