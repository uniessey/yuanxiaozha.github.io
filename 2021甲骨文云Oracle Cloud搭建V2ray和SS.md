# 2021甲骨文云Oracle Cloud搭建V2ray/SS

## 准备工作

1、oracle cloud账号，可以正常登录，可以进行创建免费VPS

2、下载Ssh Config Editor Pro破解版软件，用于连接虚拟机实例，下载地址如下

```html
https://www.macwk.com/soft/ssh-config-editor
```

3、vmess订阅链接生成

```bash
[https://tools.sprov.xyz/v2ray/](https://tools.sprov.xyz/v2ray/)
```

4、Clash订阅链接转换

```bash
https://acl4ssr-sub.github.io/
```

5、使用clash进行科学上网，教程如下

```bash
# mac版本clash科学上网教程
https://youtu.be/K2S_tTBsIOI

# IOS小火箭shadowrocket科学上网教程
https://youtu.be/DGz271mXR9s

# 安卓版本clash教程
https://youtu.be/LQzezmEyH80
```

## 整体步骤

1. 创建虚拟机实例
2. 设置安全策略，允许所有协议访问虚拟机
3. 连接虚拟机实例
4. 在虚拟机实例上安装V2ray/SS
5. 进行科学上网

## 搭建过程演示

### 1、创建虚拟机实例

- 登录成功后，点击左上角菜单按钮，找到【计算】→【实例数】，点击【实例数】，进入虚拟机实例列表页面

![2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled.png](2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled.png)

- 点击【Create Instance】，进入创建虚拟机实例页面

![2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%201.png](2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%201.png)

![2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%202.png](2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%202.png)

- 需要在【Add SSH keys】地方，【Save Public Key】保存公钥，【Save Private Key】保存私钥

![2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%203.png](2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%203.png)

- 然后选择【choose public key】,选择保存好的私钥，上传到服务器

![2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%204.png](2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%204.png)

- 点击页面最下方的【create】，进行虚拟机实例的创建，需要等待大约30s的样子，创建成功后，回到虚拟机实例列表页面，可以看到自己创建的虚拟机实例，如下图所示

![2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%205.png](2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%205.png)

2、设置安全策略，允许所有协议访问虚拟机

- 设置安全策略的目的，是为了trojan域名可以直接访问到我们的虚拟机机器，进行虚拟机列表，点击实例名称，进行虚拟机详情，点击虚拟云网络【Virtual Cloud Network】后面的链接，进入虚拟云网络配置

![2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%206.png](2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%206.png)

![2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%207.png](2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%207.png)

- 点击默认的安全策略，进入，点击【Add Ingress Rules】进行配置

![2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%208.png](2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%208.png)

![2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%209.png](2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%209.png)

- 添加完成，如下图所示

![2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%2010.png](2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%2010.png)

### 3、连接虚拟机实例

- 在虚拟列表，查看自己虚拟机的公网IP，用于下一步进行连接虚拟机实例

![2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%2011.png](2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%2011.png)

- 之前下载的私钥文件 ，执行命令，修改文件的访问权限为600

```bash
# 最后面是公钥文件的全路径
chmod 600 /users/why/ssh-key-2021-04-17.key
```

- 打开我们最开始安装的【Ssh Config Editor Pro】，进行如下配置，输入第一步找到的公网ip，用户名默认opc，选择自己的私钥文件，配置完成。双击左侧连接名称，进行连接。

![2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%2012.png](2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%2012.png)

![2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%2013.png](2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%2013.png)

- 成功连接虚拟机

![2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%2014.png](2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%2014.png)

### 4、在虚拟机实例上安装V2ray/SS

- 成功连接虚拟机之后，按照顺序，执行如下命令进行，按照v2ray/ss

```bash
# 1、切换到root用户
sudo -i

# 安装/卸载
bash <(curl -s -L https://git.io/v2ray.sh)
```

- 执行上面的命令，安装时间会比较长，大家耐心等待
- 安装成功后，界面如下

### 5、进行科学上网

- 使用ssh config editor pro连接虚拟机，执行下面的命令，可以获取到v2ray的节点配置消息

```bash
v2ray
```

![2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%2015.png](2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%2015.png)

- 【查看V2ray配置】可以获得V2ray配置信息，进入VMESS订阅链接生成网站，使用v2ray配置信息，生成VMESS订阅链接

```bash
https://tools.sprov.xyz/v2ray/
```

![2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%2016.png](2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%2016.png)

![2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%2017.png](2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%2017.png)

![2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%2018.png](2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%2018.png)

- 点击【复制链接】，进入clash订阅转换，把【vmess订阅链接】转化成【clash订阅链接】，订阅链接转换网址如下

```bash
https://acl4ssr-sub.github.io/
```

![2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%2019.png](2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%2019.png)

- 使用【一键导入clash】,导入到clash客户端，点击OK,就可以继续科学上网

![2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%2020.png](2021%E7%94%B2%E9%AA%A8%E6%96%87%E4%BA%91Oracle%20Cloud%E6%90%AD%E5%BB%BAV2ray%20SS%20c7ca5dcb24e34ebbb39fbe4d5ac5ac8d/Untitled%2020.png)