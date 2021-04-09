# 在青云公有云上部署 KubeSphere

## 部署准备

创建一个安全组，放行如下端口。

![安全组](png/安全组.png)

创建一个 VPC 网络，绑定安全组。

![VPC](png/VPC.png)

申请一个公网 IP 绑定到 VPC。

![绑定IP](png/绑定IP.png)

创建私有网络。

![创建私有网络](png/创建私有网络.png)

将私有网络加入到 VPC 中。

![加入VPC](png/加入VPC.png)

## 部署步骤

新建 KubeSphere，按需求选择配置参数并绑定私有网络。

![绑定私有网络](png/绑定私有网络.png)

勾选 **OpenPitrix 应用商店** 开启应用商店。

![开启应用商店](png/开启应用商店.png)

勾选确认用户协议，单击提交。

![提交](png/提交.png)

KubeSphere 已部署成功。

![部署成功](png/部署成功.png)

## 配置步骤

以下示例为通过 VPC 转发方式配置访问 KubeSphere。

在 **配置参数** 中填写 IP 地址并将暴露端口改为 16443，单击 **保存** 应用修改。

![配置ip](png/配置ip.png)

查看并记录主节点 IP。

![主节点IP](png/主节点IP.png)

进入 VPC 中配置如下转发，其中转发的内网 IP 为刚刚查看的主节点 IP。

![转发](png/转发.png)

复制 kubeconfig 中内容，确保 server 的值设置为 **VPC绑定的公网IP** : **VPC端口转发源端口**，
示例中应为 139.198.29.214:16443。

![kubeconfig](png/kubeconfig.png)

进入客户端。

![进入客户端](png/进入客户端.png)

新建 admin.conf 文件，并将 kubeconfig 中内容拷贝到其中。

## 访问 KubeSphere
