您可以通过控制台或者 API 的方式，在购买的专用宿主机上创建云服务器实例。

## 前提条件
在专用宿主机上分配子机前，您需要根据实际情况选择完成以下工作：
- 要创建网络类型为私有网络（VPC）的 CVM 实例时，需要在目标地域 [创建一个 VPC](https://intl.cloud.tencent.com/zh/document/product/215/8113)，并且在 VPC 下的目标可用区 [创建一个子网](https://intl.cloud.tencent.com/zh/document/product/215/8114)。
- 不使用系统自动创建的默认项目时，需要创建一个项目。
- 不使用系统自动创建的默认安全组时，需要在目标地域[创建一个安全组]()并添加能满足您业务需求的安全组规则。
- 创建 Linux 实例时需要绑定 SSH 密钥对，需要在目标项目下[创建一个 SSH 密钥]()。
- 创建一个自定义镜像的子机时，需要 [创建自定义镜像](https://intl.cloud.tencent.com/zh/document/product/213/4942) 或者 [导入镜像](https://intl.cloud.tencent.com/zh/document/product/213/4945)。

## 使用控制台创建子机

1. 进入子机分配页面
 1. 登录 [专用宿主机控制台](https://console.cloud.tencent.com/cvm/cdh)。
 2. 选择相应的地域，勾选专用宿主机，单击上方【分配云主机】。
![创建云主机入口](https://main.qcloudimg.com/raw/449fd0352f70f7b530ff0e3c5b8b667c.png)

2. 选择子机 CPU、内存配置
您可根据您所选中的宿主机/宿主机资源池的剩余资源情况自定义子机的 CPU、内存配置。您所指定的子机资源配置将影响创建子机的数量。
![设置CPU内存](https://main.qcloudimg.com/raw/19246bbf58a97cdc1d8f9dc025068983.png)

3. 选择镜像
根据不同来源，腾讯云提供镜像类型有：公共镜像、自定义镜像、共享镜像。更多关于镜像类型的介绍，请参考 [镜像类型介绍](https://intl.cloud.tencent.com/zh/document/product/213/4941)。
![选择镜像](https://main.qcloudimg.com/raw/687824b62a6647f17e9efce72bea0b4e.png)

4. 选择系统盘和数据盘
子机支持的存储类型有：本地硬盘/本地 SSD 硬盘、云硬盘、高效云硬盘、SSD 云硬盘。
更多关于云硬盘的介绍，请参考 [云硬盘分类]()。
 - 系统盘：必选项，用于安装操作系统。您可以选择系统盘所用的云盘类型和容量。地域不同会影响可供选择的云盘类型。系统盘默认容量为 50GB。
 - 数据盘：可选项。您可以选择在创建实例后再添加数据盘，也可以在购买时添加数据盘，并选择数据盘的云盘类型和容量。您可以创建空数据盘，也可以使用数据盘快照创建数据盘。
![选择磁盘类型](https://main.qcloudimg.com/raw/d6624835fc0aed2a315ddee0641013b2.png)

5. 设置网络信息
专用宿主机上的子机网络仅支持按流量计费，若需要为子机分配一个公网 IP 地址，您需要选择 **现在购买**。通过这种方式分配的 IP 地址不能直接与实例解绑，但是可以将该公网 IP 转换成弹性公网 IP 再进行解绑。
 - 基础网络：2017 年 8 月 3 日起新上线地域对所有用户均不再支持基础网络，2017 年 6 月 13 日后新注册的部分账号也不再支持基础网络。
 - 私有网络：必须选择 VPC 和子网，若没有事先创建 VPC 和子网，可以选择默认 VPC 和子网。更多关于基础网络和私有网络的介绍，请参考 [私有网络概述](https://cloud.tencent.com/document/product/215/535)。
![设置网络](https://main.qcloudimg.com/raw/044ed130ea9bbff02664ef0b3b0e0b53.png)

6. 确定服务器数量

7. 设置所属项目、主机名、登录方式以及安全组
 - 主机名：
     - 您可以选择在购买时主机命名方式为【立即命名】并填入有语义的名字，但限制在 60 个字符以内。
     - 也可以选择【创建后命名】，则创建后的云服务器名字为“未命名”。该名称仅在控制台显示，并非云服务器的 hostname。
 - 登录方式：
     - 对于镜像选择了 Linux 类型的云服务器，登录方式可选【设置密码】、【立即关联密钥】以及【自动生成密码】。
     - 对于镜像选择了 Windows 类型的云服务器，登录方式可选【设置密码】以及【自动生成密码】。
 - 安全组：
     - 如果您自己没有创建安全组，可选择【新建安全组】；
     - 如果已有安全组，请选择【已有安全组】。
同时可以预览安全组规则，关于安全组规则的介绍，请参考 [安全组]()。
![主机信息](https://main.qcloudimg.com/raw/20ba29ea87e44cd2d0d7cdde37737c69.png)

8. 选择安装安全加固和云监控组件
 - 安全加固：免费开通 DDoS 防护、WAF 和云镜主机防护，更多介绍请参考 [主机安全](https://intl.cloud.tencent.com/zh/document/product/296/2221)。
 - 云监控：免费开通云产品监控，安装组件获取主机监控指标并以监控图标形式展示，且支持设置自定义告警阈值等。更多介绍，请参考 [云监控概述]()。

>云服务器创建好后用户将会收到站内信，内容包括实例名称、公网 IP 地址、内网 IP 地址、登录名、初始登录密码（选择自动生成密码情况下）等信息，您可以使用这些信息登录和管理实例。

## 使用 API 创建子机
使用 RunInstances 接口可以在指定专用宿主机上创建子机，具体用法详见 [创建实例 API ](https://intl.cloud.tencent.com/zh/document/api/213/15730)。