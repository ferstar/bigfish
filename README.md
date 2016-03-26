## 阿里大鱼短信 SDK for python3

最近一个项目刚好需要接入短信验证收发这一功能, 经过筛选以后敲定选择阿里大鱼的解决方案. 比较良心的是提供了 Python 的 SDK, 然而这是一份长了草的SDK, 为署名 lihao 的开发者在 2012 年更新的源码, 所以悲催的事情出现, 只支持 Python2.x, 经过一番爬坑修改后, 成功让短信验证功能跑通, 对应的接口是`AlibabaAliqinFcSmsNumSendRequest`, 别的接口没整:-)

## 例子

```
import top.api


req = top.api.AlibabaAliqinFcSmsNumSendRequest()
req.set_app_info(top.appinfo("appkey", "secret"))
req.sms_type = "normal"
req.rec_num = "要发送验证码的手机号码, 11位, 不能加0和+86"
req.sms_template_code="SMS_6775282"
req.sms_free_sign_name="注册验证"
req.sms_param = {"code": "666", "product": "霸王洗发露"}
resp = req.getResponse()
print(resp)

```

## 正确返回结果

```
{
    alibaba_aliqin_fc_sms_num_send_response: {
        request_id: "ztatb1sl97gu", 
        result: {
            err_code: "0", 
            model: "100992225259^1101460699829", 
            success: true
        }
    }
}
```

- 阿里大鱼 API 文档说明: 

<https://api.alidayu.com/doc2/apiDetail.htm?apiId=25450>
