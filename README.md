# cross-wxauth

微信获取用户信息，接口提供给没有服务号的用户使用，或者个人使用；

##官方微信授权步骤
- 第一步：用户同意授权，获取code

- 第二步：通过code换取网页授权access_token

- 第三步：刷新access_token（如果需要）

- 第四步：拉取用户信息(需scope为 snsapi_userinfo)


##使用方法

例如：在 A: http://xx.cn/xxx/index.html 域名下获得微信用户的信息

- 拼接 url 获得code 

	http://wx.wbh5.com/auth/?url=
  这里url 后面的地址 就是 上面的 A 地址 经过 encodeURIComponent 后，如下：

	http://wx.wbh5.com/auth/?url=http%3A%2F%2Fxx.cn%2Fxxx%2Findex.html  然后访问这个链接，在微信浏览器中打开，就会到授权页面

- A: 域名拿到 code 之后 请求用户数据

    接口地址： http://api.wbh5.com/cross/wxusers?callback=?  方式： GET

```

	var code = getQueryString('code');
	
	if (code) {
	    Ajax({
	        type: 'get',
	        url: 'http://api.wbh5.com/cross/wxusers?callback=?',
	        data: {code: code}
	    }, function (data) {
	        alert(JSON.stringify(data));
	    })
	
	}

```