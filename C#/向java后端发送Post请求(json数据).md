## 问题描述：使用HttpClient()中的PostAsJsonAsync<>向若依后端发送json数据时报出json格式化错误
> 问题解决：改用StringContent类和PostAsync方法发送,如下
```Csharp
    using(var httpClient = new HttpClient()){

        var apiUrl = "接口地址";
        var result = "发送的数据";
        //StringContent用于构建请求参数
        var Content = new StringContent(result, Encoding.UTF8, "application / json");
        //发送Post请求
        var response = httpClient.PostAsync(apiUrl,Content);
        //获取相应
        var res = response.Content.ReadAsStringAsync();
    }
```