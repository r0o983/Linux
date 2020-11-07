# Nessus

安装软件包

```bash
sudo atp update && sudo apt upgrade
```

https://www.tenable.com/downloads/nessus

安装好之后会在本地开启一个8834的端口

```bash
sudo apt install ./nessus.deb
#安装软件包
sudo /etc/init.d/nessusd start
#开启服务
```

在网页端直接访问localhos:8834

选择essentials版本注册，当然，你可以选择其他的

填写好资料后，下一步...... 输入邮箱，获得激活代码

创建好用户后登录，这时会下载并编译所有的插件，会比较费时间。

## 设置扫描

点击New Scan按钮，选择基础网络扫描（basic network scan。

填写项目名称和目标机器（name，target

修改需要扫描的端口，点击（discovery   选择扫描模式

* 常见端口扫描
* 扫描全部端口
* 自定义

选择自定义后可以在左侧边栏选择需要扫描的端口以及扫描方式

设置完成后直接保存运行即可

**扫描完成后点击IP地址即可进入详情页进行查看当前扫描结果**

点击过滤器可以修改想要查看的结果类型，选择可利用的选项，并应用（exploit available

有些时候会产生误报，所以还需要进一步测试才能确定漏洞是否真实存在

## Authenticated Scanning With Nessus / 验证扫描

note：作为渗透测试人员，在大多数情况下，如果没有目标网络管理员的明确许可和明确沟通，我们将不会执行经过身份验证的扫描，因为生产系统无意中断的潜在风险更高。

1. 点击New Scan
2. 选择Credentialed Patch audit
3. 填写项目名称以及目标IP地址
4. 选择凭据选项卡（Credentials，选择authenticate method 然后选择ssh，设置用户名为root，密码根据具体的机器密码具体设置
5. 保存，并开启攻击。
6. 扫描完成后即可查看当前扫描出的系统漏洞

## Scanning with Individual Nessus Plugins /使用独立的插件来进行扫描

使用高级扫描模版，与之前使用的基本网络扫描和认证补丁审计模版不同，高级扫描不使用扫描配置建议，然而这个模版确实提供了一些高级默认值，这些默认值对于其他模版通常是隐藏或不可用的

Note：advanced Scan 允许我们使用单独的插件，这个选项对于大多数其他模版是不可用的

1. 点击New Scan
2. 选择advanced Scan
3. 填写项目名称以及目标IP地址
4. 选择左侧的设置选项（discovery，由于我们知道主机是存活的，所以在这关闭掉ping功能，并取消扫描端口，将端口设置为111
5. 选择插件（点击Plugins，然后选择需要的插件，这次需要使用到nfs导出共享信息公开的一个插件，首先点击插件RPC，接下来在右侧点击全部禁用，然后选择我们需要的NFS Exported Share Information Disclosure插件，点击即可
6. 保存，并开启扫描