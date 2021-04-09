# 在青云公有云上部署 KubeSphere


## 部署准备

1. 创建一个安全组，参考下图放行端口。

   ![安全组](png/安全组.png)

2. 创建一个 VPC 网络，并绑定到安全组。

   ![VPC](png/VPC.png)

3. 申请一个公网 IP ，并绑定到 VPC 网络。

  ![绑定IP](png/绑定IP.png)

4. 创建私有网络。

  ![创建私有网络](png/创建私有网络.png)

5. 将私有网络加入到 VPC 网络中。

  ![加入VPC](png/加入VPC.png)

## 步骤一：在应用商城部署

1. 新建 KubeSphere ，按需求选择配置参数，并绑定私有网络。

   ![绑定私有网络](png/绑定私有网络.png)

2. 勾选**OpenPitrix 应用商店**，开启应用商店。

  ![开启应用商店](png/开启应用商店.png)

3. 勾选确认用户协议，并点击提交。

  ![提交](png/提交.png)

4. KubeSphere 已部署成功。

  ![部署成功](png/部署成功.png)

## 步骤二：配置网络环境

以下以通过 VPC 转发方式配置访问 KubeSphere 为示例。

1. 配置目标集群网络参数。
   在**配置参数**中填写 IP 地址并将放行端口改为’16443‘，单击**保存**，应用修改后配置。
   ![配置ip](png/配置ip.png)

2. 获取目标集群主节点 IP。

   ![主节点IP](png/主节点IP.png)

3. 修改 VPC 网络配置。
   进入 VPC 中修改如下图端口转发配置，其中转发的内网 IP 为主节点 IP。
   ![转发](png/转发.png)

4. 获取 **Kubeconfig** 配置信息。  
   如图，获取目标集群 **Kubeconfig** 配置信息。需确保 server 的值设置为 **VPC绑定的公网IP** : **VPC端口转发源端口**，如图示例中应为139.198.29.214:16443。

   ![kubeconfig](png/kubeconfig.png)

5. 新建并配置 **admin.conf** 文件。
   如图，进入目标节点客户端。
   新建 **admin.conf** 文件，并将 **Kubeconfig** 中配置信息拷贝到 **admin.conf** 文件。
   ![进入客户端](png/进入客户端.png)


## 访问 KubeSphere
