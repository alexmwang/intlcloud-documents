## 免费额度

| 用户对象 | 免费期限 | 免费额度	 |如何获取|
|---------|---------|---------|------|
| 新用户 | 开通服务后半年内 | 免费享受 COS 提供的一定量的标准存储容量，详见 [免费额度](https://intl.cloud.tencent.com/document/product/436/6240)	 |开通 COS 即可，[前往体验](https://console.cloud.tencent.com/cos5)

> !在使用免费额度期间内产生的低频存储/归档存储容量、请求、流量等非标准存储容量计费项，不属于免费范畴。


## 计费方式

对象存储 COS 的计费方式为按量计费，说明如下：

| 计费方式           | 支持地域                                                     |
| ------------------ | ------------------------------------------------------------ |
| 按量计费（后付费） | 提供服务的所有地域，具体请参见 [地域与访问域名](https://intl.cloud.tencent.com/document/product/436/6224) |


## 计费项

对象存储 COS 的计费项包括：存储容量费用、请求费用、数据取回费用、流量费用、和管理功能费用。如下图所示，更多介绍请参见 [计费项](https://intl.cloud.tencent.com/document/product/436/33776)。

![](https://main.qcloudimg.com/raw/3e01aac7cc85df17e6551f88e6a3261f.png)


## 计费周期

对象存储 COS 各项计费项的计费周期和计费顺序说明如下：

<table>
   <tr>
      <th>计费项</th>
      <th>计费周期</th>
      <th>计费周期说明</th>
      <th>计费顺序</th>
   </tr>
   <tr>
      <td nowrap="nowrap">存储容量费用</td>
      <td rowspan="3">月</td>
      <td rowspan="3">每月3日到5日为账单结算日，对上月产生的费用进行结算，输出账单</td>
      <td nowrap="nowrap">免费额度 > 按量计费</td>
   </tr>
   <tr>
      <td>请求费用</td>
      <td>按量计费</td>
   </tr>
   <tr>
      <td  nowrap="nowrap">数据取回费用</td>
      <td>按量计费</td>
   </tr>
   <tr>
      <td>流量费用</td>
      <td>日</td>
      <td>每日对上一日产生的费用进行结算，输出账单</td>
      <td>按量计费</td>
   </tr>
   <tr>
      <td>清单功能费用</td>
      <td>日</td>
      <td>每日对上一日产生的费用进行结算，输出账单</td>
      <td> 按量计费</td>
   </tr>
   <tr>
      <td>检索功能费用</td>
      <td>日</td>
      <td>每日对上一日产生的费用进行结算，输出账单</td>
      <td> 按量计费</td>
   </tr>
</table>







## 相关链接


1. 关于 COS 的费用详细计算及不同场景下的计费详情，请参见 [计费示例](https://intl.cloud.tencent.com/document/product/436/6241)。
2. 关于 COS 的欠费停服策略：数据的保留和销毁时间、以及相关计费说明，请参见 COS [欠费说明](https://intl.cloud.tencent.com/document/product/436/10044)。
3. 若您对 COS 计费仍有疑问，可参见计费 [常见问题](https://intl.cloud.tencent.com/document/product/436/32532) 寻求答案。



