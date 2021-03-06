[//]: # (chinagitpath:XXXXX)

## 概述
当将通过规则提取出来的消息字段转发给第三方服务时，用户可自定义如何处理这些数据。这种方式是提供给用户灵活性最高的一种消息处理方式。需注意第三方服务必须以 http 的方式提供服务。要配置转发第三方服务，需要提供支持 http 的网站 url 和端口。

下图展示了将数据转发给第三方服务的整个过程：
![image](https://mc.qcloudimg.com/static/img/b24d804514c29ee7f8810130e9cf6771/service_http2.png)
## 配置
1. 登录 [规则引擎](https://console.cloud.tencent.com/iotcloud/rules/rule) 控制台页面，点击所要配置的规则。
![](https://main.qcloudimg.com/raw/0a0a0e5bc48aa0d4492ac0b8d3c7413c.png)
2. 在规则详情页面，单击【添加行为】按钮。在弹出的“新增行为”窗口，选择行为“forward”，填写用户自己的 http 服务地址后，单击【创建】即可。物联网通信平台会将设备上报的数据转发至 http 服务地址。
![image](https://main.qcloudimg.com/raw/8bd5aa126ed065559667f9880850ba26.png)
