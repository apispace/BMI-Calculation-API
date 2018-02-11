## eoLinker-API Shop
### 基于Python的标准体重计算器API接口调用代码示例
#### 一、接口名称：标准体重计算器
#### 二、接口描述：身体质量指数 (Body Mass Index, 简称BMI), 通过身高和体重来计算您的身材是否标准
#### 三、接口平台：eoLinker-API Shop （apishop.net）

该套接口包含两个接口：

**接口一：获取标准体重参考**
**接口二：计算BMI值**

**1、接口一：获取标准体重参考**

本代码示例是基于Python的eoLinker-API Shop** 获取标准体重参考** API服务请求的代码示例，使用前你需要：

①：通过https://www.apishop.net/#/api/detail/?productID=104 申请API服务

**以下是完整代码示例：**
```
//post请求
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# 测试环境: python2.7
# 安装requests依赖 => pip install requests/ easy_install requests

# 导入requests依赖
import requests
import json
import sys

reload(sys)
sys.setdefaultencoding("utf-8")
   '''
   转发请求到目的主机
   @param method str 请求方法
   @param url str 请求地址
   @param params dict 请求参数
   @param headers dict 请求头
   '''
   if method == "POST":
       return requests.post(url=url, data=params, headers=headers)
   elif method == "GET":
       return requests.get(url=url, params=params, headers=headers)
   else:
       return None

method = "POST"
url = "https://api.apishop.net/common/BMI/getStandardWeightTable
headers = None
params = {
   apiKey : "参数1"
}
result = apishop_send_request(method=method, url=url, params=params, headers=headers)
if result:
   body = result.text
   response = json.loads(body)
   status_code = response["statusCode"]
   if (status_code == "000000"):
       # 状态码为000000, 说明请求成功
       print("请求成功：%s" % (body,))
   else:
       # 状态码非000000, 说明请求失败
       print("请求失败: %s" % (body,))
   else:
       # 返回内容异常，发送请求失败
       print("发送请求失败"")  
```

**2、接口二：计算BMI值**

本代码示例是基于Python的eoLinker-API Shop **计算BMI值** API服务请求的代码示例，使用前你需要：

①：通过https://www.apishop.net/#/api/detail/?productID=104 申请API服务

**以下是完整代码示例：**
```
//post请求
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# 测试环境: python2.7
# 安装requests依赖 => pip install requests/ easy_install requests

# 导入requests依赖
import requests
import json
import sys

reload(sys)
sys.setdefaultencoding("utf-8")
   '''
   转发请求到目的主机
   @param method str 请求方法
   @param url str 请求地址
   @param params dict 请求参数
   @param headers dict 请求头
   '''
   if method == "POST":
       return requests.post(url=url, data=params, headers=headers)
   elif method == "GET":
       return requests.get(url=url, params=params, headers=headers)
   else:
       return None

method = "POST"
url = "https://api.apishop.net/common/BMI/computeBMI
headers = None
params = {
   apiKey : "参数1",
   weight : "参数2",
   height : "参数3"
}
result = apishop_send_request(method=method, url=url, params=params, headers=headers)
if result:
   body = result.text
   response = json.loads(body)
   status_code = response["statusCode"]
   if (status_code == "000000"):
       # 状态码为000000, 说明请求成功
       print("请求成功：%s" % (body,))
   else:
       # 状态码非000000, 说明请求失败
       print("请求失败: %s" % (body,))
   else:
       # 返回内容异常，发送请求失败
       print("发送请求失败"")
```