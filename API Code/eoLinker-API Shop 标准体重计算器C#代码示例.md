## eoLinker-API Shop
### 基于C#的标准体重计算器API接口调用代码示例
#### 一、接口名称：标准体重计算器
#### 二、接口描述：身体质量指数 (Body Mass Index, 简称BMI), 通过身高和体重来计算您的身材是否标准
#### 三、接口平台：eoLinker-API Shop （apishop.net）

该套接口包含两个接口：

**接口一：获取标准体重参考**
**接口二：计算BMI值**

**1、接口一：获取标准体重参考**

本代码示例是基于C#的eoLinker-API Shop** 获取标准体重参考** API服务请求的代码示例，使用前你需要：

①：通过https://www.apishop.net/#/api/detail/?productID=104 申请API服务

**以下是完整代码示例：**
```
using System;
using System.Collections.Generic;
using System.IO;
using System.Net;
using System.Text;
using System.Web.Script.Serialization;

namespace apishop_sdk
{
   class Program
   {
       /**
        * 转发请求到目的主机
        * @param method string 请求方法
        * @param url string 请求地址
        * @param params Dictionary<string,string> 请求参数
        * @param headers Dictionary<string,string> 请求头
        * @return string
        * @return string
        **/
       static string apishop_send_request(string method, string url, Dictionary<string, string> param, Dictionary<string, string> headers)
       {
           string result = string.Empty;
           try
           {
               string paramData = "";
               if (param != null && param.Count > 0)
               {
                   StringBuilder sbuilder = new StringBuilder();
                   foreach (var item in param)
                   {
                       if (sbuilder.Length > 0)
                        {
                             sbuilder.Append("&");
                        }
                        sbuilder.Append(item.Key + "=" + item.Value);
                    }
                    paramData = sbuilder.ToString();
                }
                method = method.ToUpper();
                if (method == "GET")
                {
                    url = string.Format("{0}?{1}", url, paramData);
                }
                HttpWebRequest wbRequest = (HttpWebRequest)WebRequest.Create(url);
                if (method == "GET")
                {
                    wbRequest.Method = "GET";
                }
                else if (method == "POST")
                {
                    wbRequest.Method = "POST";
                    wbRequest.ContentType = "application/x-www-form-urlencoded";
                    wbRequest.ContentLength = Encoding.UTF8.GetByteCount(paramData);
                    using (Stream requestStream = wbRequest.GetRequestStream())
                    {
                        using (StreamWriter swrite = new StreamWriter(requestStream))
                        {
                            swrite.Write(paramData);
                        }
                    }
                }
                
                HttpWebResponse wbResponse = (HttpWebResponse)wbRequest.GetResponse();
                using (Stream responseStream = wbResponse.GetResponseStream())
                {
                    using (StreamReader sread = new StreamReader(responseStream))
                    {
                        result = sread.ReadToEnd();
                    }
                }
            }
            catch
            {
                return "";
            }
            return result;
        }
        
        class Response
        {
            public string statusCode;
        }
        static void Main(string[] args)
        {
            string method = "POST";
            string url = "https://api.apishop.net/common/BMI/getStandardWeightTable";
            Dictionary<string, string> param = new Dictionary<string, string>();
               param.Add("apiKey", "参数1");
            Dictionary<string, string> headers = null;
            string result = apishop_send_request(method, url, param, headers);
            string result = apishop_send_request(method, url, param, headers);
            {
                //返回内容异常，发送请求失败
                Console.WriteLine("发送请求失败");
                return;
            }
            
            Response res = new JavaScriptSerializer().Deserialize<Response>(result);
            if (res.statusCode == "000000")
            {
                //状态码为000000, 说明请求成功
                Console.WriteLine(string.Format("请求成功: {0}", result));
            }
            else
            {
                //状态码非000000, 说明请求失败
                 Console.WriteLine(string.Format("请求失败: {0}", result));
            }
            Console.ReadLine();
        }
    }
}
```
**2、接口二：计算BMI值**

本代码示例是基于C#的eoLinker-API Shop **计算BMI值** API服务请求的代码示例，使用前你需要：

①：通过https://www.apishop.net/#/api/detail/?productID=104 申请API服务

**以下是完整代码示例：**
```
using System;
using System.Collections.Generic;
using System.IO;
using System.Net;
using System.Text;
using System.Web.Script.Serialization;

namespace apishop_sdk
{
   class Program
   {
       /**
        * 转发请求到目的主机
        * @param method string 请求方法
        * @param url string 请求地址
        * @param params Dictionary<string,string> 请求参数
        * @param headers Dictionary<string,string> 请求头
        * @return string
        * @return string
        **/
       static string apishop_send_request(string method, string url, Dictionary<string, string> param, Dictionary<string, string> headers)
       {
           string result = string.Empty;
           try
           {
               string paramData = "";
               if (param != null && param.Count > 0)
               {
                   StringBuilder sbuilder = new StringBuilder();
                   foreach (var item in param)
                   {
                       if (sbuilder.Length > 0)
                        {
                             sbuilder.Append("&");
                        }
                        sbuilder.Append(item.Key + "=" + item.Value);
                    }
                    paramData = sbuilder.ToString();
                }
                method = method.ToUpper();
                if (method == "GET")
                {
                    url = string.Format("{0}?{1}", url, paramData);
                }
                HttpWebRequest wbRequest = (HttpWebRequest)WebRequest.Create(url);
                if (method == "GET")
                {
                    wbRequest.Method = "GET";
                }
                else if (method == "POST")
                {
                    wbRequest.Method = "POST";
                    wbRequest.ContentType = "application/x-www-form-urlencoded";
                    wbRequest.ContentLength = Encoding.UTF8.GetByteCount(paramData);
                    using (Stream requestStream = wbRequest.GetRequestStream())
                    {
                        using (StreamWriter swrite = new StreamWriter(requestStream))
                        {
                            swrite.Write(paramData);
                        }
                    }
                }
                
                HttpWebResponse wbResponse = (HttpWebResponse)wbRequest.GetResponse();
                using (Stream responseStream = wbResponse.GetResponseStream())
                {
                    using (StreamReader sread = new StreamReader(responseStream))
                    {
                        result = sread.ReadToEnd();
                    }
                }
            }
            catch
            {
                return "";
            }
            return result;
        }
        
        class Response
        {
            public string statusCode;
        }
        static void Main(string[] args)
        {
            string method = "POST";
            string url = "https://api.apishop.net/common/BMI/computeBMI";
            Dictionary<string, string> param = new Dictionary<string, string>();
               param.Add("apiKey", "参数1");
               param.Add("weight", "参数2");
               param.Add("height", "参数3");
            Dictionary<string, string> headers = null;
            string result = apishop_send_request(method, url, param, headers);
            string result = apishop_send_request(method, url, param, headers);
            {
                //返回内容异常，发送请求失败
                Console.WriteLine("发送请求失败");
                return;
            }
            
            Response res = new JavaScriptSerializer().Deserialize<Response>(result);
            if (res.statusCode == "000000")
            {
                //状态码为000000, 说明请求成功
                Console.WriteLine(string.Format("请求成功: {0}", result));
            }
            else
            {
                //状态码非000000, 说明请求失败
                 Console.WriteLine(string.Format("请求失败: {0}", result));
            }
            Console.ReadLine();
        }
    }
}
```