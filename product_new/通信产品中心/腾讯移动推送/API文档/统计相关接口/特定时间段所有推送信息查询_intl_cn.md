##  接口说明

**请求方式**：POST
**调用频率限制**：200次/小时。
```shell
https://api.tpns.tencent.com/v3/statistics/get_push_record
```
**接口功能**：查询特定时间段内所有任务的基本信息和设置。



## 参数说明
#### 请求参数

| 参数名称  | 必选 | 类型   | 描述       |
| --------- | ---- | ------ | ---------- |
| startDate | 是   | string | 查询起始日期，<li>格式：YYYY-MM-DD<li>查询限制：当前日期3个月内 |
| endDate | 是 | string | 查询截止日期，格式：YYYY-MM-DD |
| msgType | 否 | string | 消息类型：<li>notify：通知<li>message：静默消息 |
| pushType | 否 | string | 推送类型：<li>all：全推<li>tag：标签推<li>token：设备列表/设备单推<li>account：账号列表/账号单推 |
| offset | 否 | int | 分页查询起始偏移 |
| limit | 否 | int | 分页查询每页消息数 （最大限制为200） |

#### 应答参数

| 参数名称       | 类型      | 描述                                     |
| -------------- | --------- | ---------------------------------------- |
| retCode        | int       | 返回状态码                               |
| errMsg         | string    | 错误信息                                 |
| pushRecordData | JsonArray | 返回结果，pushRecordData 结构变量见下表 |
|count  | int  |  符合条件记录数  |

#### pushRecordData

| 参数名称         | 类型               | 说明                   | 取值说明                                                     |
| ---------------- | ------------------ | ---------------------- | ------------------------------------------------------------ |
| date             | string             | 推送时间               | 格式：YYYY-MM-DD hh:mm:ss                                    |
| pushId           | int                | 消息 ID                 | -                                                            |
| title            | string             | 推送标题               | -                                                            |
| content          | int                | 推送内容               | -                                                            |
| status           | string             | 推送状态               | <li>PUSH_INIT //任务已创建<li>PUSH_WAIT; // 等待任务被调度<li>PUSH_STARTED; // 推送中<li>PUSH_FINISHED; // 推送完成<li>PUSH_FAILED; //推送失败<li>PUSH_CANCELED; // 用户取消推送<li>PUSH_DELETED; // 推送被删除 |
| pushType         | string             | 推送目标               | <li>all //全推<li>tag //标签推送<li>token_list //设备列表<li>account_list //账号列表<li>package_account_push //号码包推送 |
| messageType      | string             | 推送类型               | <li>notify //通知<li>message //消息                              |
| environment      | string             | 推送环境               | <li>product //生产环境<li>dev //开发环境                         |
| expireTime       | uint32             | 过期时间               | 单位 s                                                       |
| xgMediaResources | string             | 富媒体信息             | -                                                            |
| multiPkg         | bool               | 是否多包名推送         | -                                                            |
| targetList       | jsonArrary(string) | 推送账号或推送设备列表 | pushType 为 token_list 或 account_list 时有效                     |
| tagSet           | JsonObject         | 标签设置               | pushType 为 tag 时有效<br>数据结构：<code><br>{<br>"op":"OR", //标签间逻辑操作<br>"tagWithType":[<br>{ "tagTypeName":"xg_user_define", //标签类型<br>"tagValue":"test68" //标签值}<br>]<br>}</code> |
| uploadId         | uint32             | 号码包 ID               | pushType 为 package_account_push 时有效                         |
| pushConfig       | JsonObject         | 推送配置信息           | <br>"Android"： Android 推送相关配置信息，具体参考下述代码<br>"iOS"：iOS 推送相关配置信息， 具体参考下述代码<br> |


## 配置信息
#### Android 推送配置信息

```json
"android":{
 "ring":1, //响铃
 "vibrate":0, //震动
 "lights":1, //呼吸灯
 "clearable":1, //是否可清除
 "action":{
 // 动作类型，1，打开activity或app本身；2，打开浏览器；3，打开Intent
 "action_type":1
 },
 "custom_content":"{}" //自定义参数
}
```

#### iOS 推送配置信息

```json
"ios":{
 "aps": {
 "alert": {
 "subtitle": "my subtitle"
 },
 "badge_type": 5, //App显示的角标数(可选) -2 自增，-1 不变，
 "sound":"通知音效", //缺省代表默认音效
 "category": "INVITE_CATEGORY",
 "mutable-content" : 1
 }
}
```

## 示例说明

#### 请求示例
```json
{
 "limit": 50,
 "startDate": "2019-07-01",
 "endDate": "2019-08-01",
 "msgType": "notify",
 "pushType": "all",
 "offset": 0
}
```
####  应答示例
>盲水印可抵抗裁剪、涂抹、变色等多种图片盗取攻击，防盗效果与原图大小及攻击程度相关。如需详细咨询请 [提交工单](https://console.cloud.tencent.com/workorder/category)。

```json
{
    "retCode": 0,
    "errMsg": "NO_ERROR",
    "count": 126,
    "pushRecordData": [
        {
            "date": "2019-11-18 11:26:54",
            "pushId": "12",
            "title": "测试标题",
            "content": "测试日志",
            "status": "PUSH_FINISHED",
            "pushType": "all",
            "targetList": null,
            "tagSet": null,
            "uploadId": 0,
            "groupId": "",
            "expireTime": 43200,
            "messageType": "notify",
            "xgMediaResources": "",
            "environment": "product",
            "pushConfig": {
                "android": {
                    "n_id": 0,
                    "builder_id": 0,
                    "ring": 1,
                    "ring_raw": "",
                    "vibrate": 1,
                    "lights": 1,
                    "clearable": 1,
                    "icon_type": 0,
                    "icon_res": "",
                    "style_id": 0,
                    "small_icon": "",
                    "action": {
                        "action_type": 3,
                        "activity": "",
                        "aty_attr": null,
                        "browser": null,
                        "intent": ""
                    },
                    "custom_content": ""
                },
                "ios": null,
                "iot": null
            },
            "multiPkg": true,
            "source": "api"
        }
    ]
}
```
