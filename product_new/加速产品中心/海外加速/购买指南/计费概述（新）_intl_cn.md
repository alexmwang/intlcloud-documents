>海外加速（GCD）产品的通用计费模式将于2020年1月1日00:00起，从按量付费按月结算，升级为按量付费按日结算。本文档为升级后的计费模式，将于2020年1月1日起生效。 [计费概述（旧）](<https://intl.cloud.tencent.com/document/product/1014/33472>)为升级前的计费模式，有效期截止至2019年12月31日。
## 计费区域
腾讯云海外加速计费区域分为：亚太1区、亚太2区、亚太3区、中东区、欧洲区、北美区、南美区、非洲区，共计8个计费大区，其中：
- 亚太1区：中国香港、中国澳门、新加坡、越南、泰国
- 亚太2区：中国台湾、日本、马来西亚、印尼、韩国
- 亚太3区：菲律宾、印度、澳大利亚及其它亚太国家和地区

>
- 海外加速计费区域按腾讯云 CDN 节点服务器所在地区进行划分。
- 每个大区的 CDN 消耗费用按该大区的单价和用量分别进行结算。

## 计费总览
海外加速为您提供了两种计费方式： **带宽计费** 和 **流量计费**，均为 **后付费按日结算**，前一天00:00:00 - 23:59:59产生的总消耗，会在第二天18:00前进行计算扣费。
>若您的账号欠费，会为您保留24小时的缓冲时间，在缓冲时间内若产生费用也会正常进行计算扣费。

### 通用计费方式说明

通用 **带宽计费** 和 **流量计费** 方式，均为 **后付费按日分区域结算**，前一天00:00:00 - 23:59:59产生的总消耗，会在第二天18:00前进行计算扣费。

<table  style="width:900">
<thead>
	<tr>
		<th colspan = "2"scope="col" style="text-align: center;font-weight:700;">计费模式</th>
		<th scope="col" style="width: 25%;text-align: center;font-weight:700;">描述</th>
		<th scope="col" style="width: 39%;text-align: center;font-weight:700;">适用场景</th>
		<th scope="col" style="width: 17%;text-align: center;font-weight:700;">计费详情</th>
	</tr>
</thead>
<tbody>
	<tr>
		<td colspan = "2" style="text-align: center;">带宽计费</td>
		<td>按每日的峰值带宽计费。每5分钟统计一个带宽数据，每日得到288个值，取其中的最大值。<br>付费方式：后付费按日结算<br>计费规则：采用阶梯到达模式</td>
		<td>若您的带宽利用率超过50%，表明您业务的曲线较为平稳，建议您采用带宽计费方式。<br>带宽利用率的计算方法参见 <a href="#m6">计费方式选择</a>。</td>
		<td style="text-align: center;">参见 <a href="#m1">计费详情</a></td>
	</tr>
	<tr>
	<td colspan = "2" style="text-align: center;">流量计费<br>（默认）</td>
		<td>按每日从腾讯云 CDN 节点流出的实际流量计费。<br>付费方式：后付费按日结算<br>计费规则：月度阶梯累进结算</td>
		<td>若您的带宽利用率小于50%，表明您业务的曲线波动较大，建议您采用流量计费方式。<br>带宽利用率的计算方法参见 <a href="#m6">计费方式选择</a>。</td>
		<td style="text-align: center;">参见 <a href="#m2">计费详情</a></td>
	</tr>
</tbody>
</table>

### 大客户计费方式说明
如果您的海外加速服务月消费金额大于2万美元或预期超过2万美元，腾讯云海外加速可以为您提供更灵活优惠的按月计费方式。您可以 [联系腾讯云商务](<https://intl.cloud.tencent.com/contact-sales>) 洽谈接入。

<table  style="width:900">
<thead>
	<tr>
		<th scope="col" style="width: 136px;text-align: center;font-weight:700;">计费模式</th>
		<th scope="col" style="width: 300px;text-align: center;font-weight:700;">描述</th>
		<th scope="col" style="text-align: center;font-weight:700;">适用场景</th>
		<th scope="col" style="width: 144px;text-align: center;font-weight:700;">计费详情</th>
	</tr>
</thead>
<tbody>
	<tr>
		<td style="text-align: center;">日峰带宽取月均</td>
		<td>CDN 每日带宽统计点共288个，对所有有效天的峰值取平均，得到计费带宽，再根据商务签订的合同价格计算费用。</td>
		<td colspan="1" rowspan="3">CDN 月消费金额大于2万美元或预期超过2万美元的用户，请联系我们进行商务洽谈。</td>
		<td style="text-align: center;">参见 <a href="#m3">计费详情</a></td>
	</tr>
	<tr>
		<td style="text-align: center; ">月95带宽</td>
		<td>CDN 每日带宽统计点共288个，从当月1号起，每一个有效日（产生消耗）的所有统计点进行排序，去掉前5%的统计点，剩下的最大的统计点，即为计费带宽，再根据合同价格计算费用。</td>
		<td style="text-align: center;">参见 <a href="#m3">计费详情</a></td>
	</tr>
	<tr>
		<td style="text-align: center; ">月流量</td>
		<td>月度累计使用的所有流量和，根据合同价格计算费用。</td>
		<td style="text-align: center; ">/</td>
	</tr>
</tbody>
</table>


>   
> - 各 CDN 节点会实时记录流量数据，上报至计算中心，汇总为域名总流量数据。带宽计费时，使用每5分钟粒度数据进行结算，即相应的带宽值 = 5分钟粒度总流量 / 300秒。例如：5分钟内产生的总流量为30MB，根据换算规则：1MB = 8Mb，即相应的带宽为<nobr>（30 * 8）/ 300 = 0.8Mbps</nobr>。
> - 进制换算规则：1GB = 1000MB、1 MB= 1000 KB; 1Gbps = 1000Mbps、1Mbps = 1000Kbps。

## 计费详情
<span ID ="m1"></span>
### 峰值带宽计费
#### 阶梯价格
海外加速分区域 **每日峰值带宽** 计费采用 **阶梯到达** 模式，价格阶梯如下所示：

|带宽阶梯<br/>（美元/Mbps/天）|北美 - NA|欧洲 - EU|亚太1区 - AP1|亚太2区 - AP2|亚太3区 - AP3|中东 - ME|非洲 - AA|南美 - SA|
|----------------------------------|-----------|------------|-------------------|---------------------|--------------|-------------|--|--|
|0Mbps - 500Mbps（含）| 0.2941    |0.2941|0.4412|0.5882| 0.6471        | 0.8529    | 0.6471    | 0.6471    |
|500Mbps - 5Gbps（含）| 0.2471    | 0.2471    | 0.3882        | 0.5294        | 0.5941        | 0.7824    | 0.5941    | 0.5941    |
|5Gbps - 50Gbps（含）| 0.1824    | 0.1824    | 0.3412        | 0.4706        | 0.5471        | 0.7059    | 0.5471    | 0.5471    |
|大于 50Gbps| 0.1294    | 0.1294    | 0.2941        | 0.4118        | 0.5           | 0.6176    | 0.5       | 0.5       |

#### 计算方式
假设前一日 **北美区域** 海外加速的峰值带宽为 X，阶梯计算方式如下：
1. 若 X ≤ 500Mbps，则账单费用为 X \* 0.2941。
2. 若 500Mbps < X ≤ 5000Mbps，则账单费用为 X \* 0.2471。
3. 若 5000Mbps < X ≤ 50000Mbps，则账单费用为 X \* 0.1824。
4. 若 X ＞ 50000Mbps，则账单费用为 X \* 0.1294。

其他计费大区的海外加速消耗费用也按该大区的单价和用量分别进行结算。

<span ID ="m2"></span>
### 流量按量计费	
#### 阶梯价格
海外加速分区域 **日流量** 计费采用 **月度阶梯累进** 结算，计费阶梯如表所示：

|流量阶梯<br/>（美元/GB）|北美 - NA|欧洲 - EU|亚太1区 - AP1|亚太2区 - AP2|亚太3区 - AP3|中东 - ME|非洲 - AA|南美 - SA|
|---------------------------|---------------|------------|-----------|----------|-----------|-----------|-----------|-----------|
|0TB - 2TB（含）| 0.0547    | 0.0547    | 0.0812        | 0.1094        | 0.12          | 0.1588    | 0.12      | 0.12      |
|2TB - 10TB（含）| 0.0459    | 0.0459    | 0.0724        | 0.1024        | 0.1129        | 0.1465    | 0.1129    | 0.1129    |
|10TB - 50TB（含）| 0.0388    | 0.0388    | 0.0653        | 0.0935        | 0.1059        | 0.1359    | 0.1059    | 0.1059    |
|50TB - 100TB（含）| 0.0318    | 0.0318    | 0.0582        | 0.0847        | 0.0988        | 0.1253    | 0.0988    | 0.0988    |
|大于 100TB| 0.0247    | 0.0247    | 0.0547        | 0.0759        | 0.0918        | 0.1147    | 0.0918    | 0.0918    |

#### 计算方式
流量计费与带宽计费不同，按照月度流量进行阶梯累进，计算方式示例如下：
+ 若1月1日 **北美区域** 产生流量为3TB，如下图所示。图中灰色为实际计费阶梯，绿色为1月1日产生的流量，其中2TB落入0TB - 2TB的计费阶梯，1TB落入2TB - 10TB的计费阶梯，因此1月1日这一天的实际费用为：2 \* 1000 \* 0.0547 + 1 \* 1000 \* 0.0459。
  ![](https://mc.qcloudimg.com/static/img/bfdae242f6cca57421a65e46a96b0c67/image.png)
+ 若1月2日这一天也产生了3TB的流量，如下图所示。流量计费采用月度累计，因此1月2日产生的流量均落入2TB - 10TB的计费阶梯，因此1月2日这一天的实际费用为：3 \* 1000 \* 0.0459。
  ![](https://mc.qcloudimg.com/static/img/f62d1056c1c2cab249cec62ad6e74ddc/image.png)
+ 若1月3日这一天产生了7TB的流量，如下图所示。此时3号的7TB中，有4TB落入2TB - 10TB的计费阶梯，3TB落入10TB - 50TB的计费阶梯，因此1月3日这一天的实际费用为：4 \* 1000 \* 0.0459 + 3 \* 1000 \* 0.0388。
  ![](https://mc.qcloudimg.com/static/img/954e2d483e31afd411f9a91ebd7f66c8/image.png)

以此类推，计算出当月每一天的费用（每个大区分别结算），当2月1日开始计费时，一切从0开始重新阶梯累进。

<span ID ="m3"></span>

### 日峰带宽取月均计费
1. 例如客户从2017年2月1日正式开始计费，签订的某区域合同价格为：P 美元/Mbps/月。
2. 有效天：该区域产生的消耗 ＞ 0，则记为有效天。
3. 假设客户2月份该区域有14天产生的消耗 ＞ 0，这14天每一天的288个统计点最大值为：Max_1、Max_2、Max_3... Max_14，计费带宽为 Average(Max_1, Max_2, ..., Max_14)，2月该区域的费用为：Average(Max_1, Max_2, ..., Max_14)  \*  P  \*  14 / 28。


### 月95带宽计费	
1. 例如客户从2017年2月1日正式开始计费，签订的某区域合同价格为：P 美元/Mbps/月。
2. 有效天：该区域产生的消耗 ＞ 0，则记为有效天。
3. 假设客户2月份该区域有14天产生的消耗 ＞ 0，则计费带宽为这14天的所有统计点14 \* 288个，去掉最高的5%的点，剩余统计点中最高的为 Max95，Max95 即为计费带宽，2月该区域的费用为：Max95 \* P \* 14 / 28。

<span ID ="m6"></span>
## 计费方式选择
**选择方式：**
海外加速为您提供了两种计费方式：**流量计费**和**带宽计费**，您可以根据自身业务形态选择合适的计费方式。您所选择的计费方式将应用于海外加速全部计费区域。

+ 若您的带宽利用率超过50%，表明您业务的曲线较为平稳，建议您采用带宽计费方式。
+ 若您的带宽利用率小于50%，表明您业务的曲线波动较大，建议您采用流量计费方式。

**计算示例：**
您可以通过计算带宽利用率来选择适用的计费方式，带宽利用率计算方式示例如下：
假设用户昨日00:00 - 24:00的消耗流量为200GB，曲线图如下所示，此时流量消耗可以理解为图中曲线所占面积：
![](https://mc.qcloudimg.com/static/img/3ecfe86a031782ebeaf0b1f7595cc69f/image.png)
假设用户昨日00:00 - 24:00的带宽峰值为40Mbps，一天为86400秒，根据流量 = 带宽 * 时间，此时一天的流量为40(Mbps) * 86400(s) = 3456000(Mb)，又根据换算规则8Mb = 1MB、1000MB = 1GB，将单位折算为GB，即3456000(Mb) = 3456000 / 8 / 1000 = 432GB ，此时可以理解为图中矩形所占面积：
![](https://mc.qcloudimg.com/static/img/b80d043b6e7f461d62fd2d87abf67005/image.png)
此时带宽利用率为：200GB / 432GB \* 100% = 46%，带宽利用率小于50%，故而此示例建议采用流量计费方式。

<span ID ="m5"></span>

## 欠费说明
### 通过实名认证的用户
若您是已经通过个人或企业实名认证、而后开通海外加速服务的用户，当您的腾讯云账户处于欠费状态时，腾讯云会通过短信、邮件等多种方式提醒您欠费状态，并为您保留**24小时**的缓冲时间。在24小时后，系统会停止您的海外加速服务。您的账户欠费冲正后，需通过控制台手动开启加速服务。
>欠费导致加速服务停止后，您的所有域名全部下线，访问全部回源处理。CDN 控制台仅支持查询操作，不能进行配置修改等操作。您的海外加速相关域名、配置信息会为您保留12个月。
