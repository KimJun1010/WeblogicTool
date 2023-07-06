# WeblogicTool
## 简介
迫于目前现有的weblogic工具没怎么更新、payloayjdk适用版本等问题，所以基于superman18、sp4zcmd等项目，写一个weblogic工具，工具运行版本要求jdk 8（深信服深蓝实验室天威战队强力驱动）

## 免责声明
本工具仅能在取得足够合法授权的企业安全建设中使用，在使用本工具过程中，您应确保自己所有行为符合当地的法律法规。 如您在使用本工具的过程中存在任何非法行为，您将自行承担所有后果，本工具所有开发者和所有贡献者不承担任何法律及连带责任。 除非您已充分阅读、完全理解并接受本协议所有条款，否则，请您不要安装并使用本工具。 您的使用行为或者您以其他任何明示或者默示方式表示接受本协议的，即视为您已阅读并同意本协议的约束

## 支持漏洞
```
CVE-2023-21931（JNDI）
CVE-2023-21839（JNDI）
CVE-2020-2551（JRMP）
CVE-2020-2551
CVE-2020-2555
CVE-2020-2883
CVE-2020-14882 未授权访问
CVE-2018-2894
CVE-2018-2628（JRMP）
CVE-2018-2893（JRMP）
CVE-2018-3245（JRMP）
CVE_2018_3252（JRMP）
CVE_2018_3191
CVE-2016-3510
CVE-2016-0638
CVE-2017-10271
CVE-2017-3248（JRMP）
CVE-2015-4852
......
```

## 漏洞检测
支持最近的CVE-2023-21839漏洞T3&&IIOP，JNDI和JRMP类型漏洞需要填写自定义的dnslog地址，防止waf拦截常用的dnslog域名

## 命令执行
先检测漏洞是否存在
<img width="894" alt="image" src="https://github.com/KimJun1010/WeblogicTool/assets/49397311/485e76d6-5ee7-46c5-b1c9-df2b694a8566">

  
ECHO类型漏洞，支持执行命令，支持自定义返回数据编码格式
<img width="899" alt="image" src="https://github.com/KimJun1010/WeblogicTool/assets/49397311/0fc9d254-8d4f-4bc9-a5fa-020d4735744a">


## JRMP攻击
jrmp类型的漏洞只能使用jrmp模块进行攻击，在vps上使用yso启动jrmp，工具中填入vps的jrmp地址即可  

```java -cp ./ysoserial.jar ysoserial.exploit.JRMPListener 9999 CommonsCollections3 'touch /tmp/1.txt' ```
<img width="897" alt="image" src="https://github.com/KimJun1010/WeblogicTool/assets/49397311/2b5517ba-a3d5-4d9b-97cf-8d91839c29d1">


## JNDI 
与jrmp漏洞使用方法一样，需要启动vps服务端   

## 内存马注入
目前支持哥斯拉4 Servlet Filter、冰蝎3.11 Servlet、蚁剑Custom Filter
![image](https://user-images.githubusercontent.com/49397311/232308056-fb517990-bf79-4228-8130-5c33cb262048.png)  
![image](https://user-images.githubusercontent.com/49397311/232308062-0bb61d73-a56c-43ed-b944-6f5d23ed8ea8.png)

## 密码解密
说明
1. 支持Weblogic 3DES和AES解密 
2. 由于bcprov jar包签名问题，所以首次解密会出现异常：PBEWITHSHAAND128BITRC2-CBC SecretKeyFactory not available。需要手动下载 ```https://repo1.maven.org/maven2/org/bouncycastle/bcprov-jdk15on/1.56/bcprov-jdk15on-1.56.jar``` 然后将文件存在本地安装的JDK路径下，例如 ```E:\Java\jdk1.8.0_60\jre\lib\ext```
![image](https://user-images.githubusercontent.com/49397311/232308083-058b42bb-3360-43ad-b90b-d9472ccfcdc0.png)


## 协议探测
目前支持批量探测T3、IIOP协议开放状态，内网IP地址（IIOP实现），常见的接口
<img width="1012" alt="image" src="https://github.com/KimJun1010/WeblogicTool/assets/49397311/a7389507-5fd3-4f0e-b4e3-2f125e611846">


## Star趋势
[![Star History Chart](https://api.star-history.com/svg?repos=KimJun1010/WeblogicTool&type=Date)](https://star-history.com/#KimJun1010/WeblogicTool&Date)

