# Ajax

## ajax相关配置

	

```js
 $.ajax({
     url: '/admin/upload', //请求的地址
     type: 'post', // 请求的方式	
     data: formData, // 传输的数据
     processData: false, // jQuery不要去处理发送的数据
     contentType: false, // jQuery不要去设置Content-Type请求头
     cache：fasle，  //是否进行缓存 (true/ fasle) 默认fasle   type为get时需要设置true (缓存)
     async：true， //同步/异步设置 true异步(默认)/ false(同步)
     timeout: 1000, //超时设置 多少ms之后 仍未接收到后盾返回的数据 则结束本次请求  进入error方法中
     //使用FormData对象时需要修改的配置项
     contentTyoe:false, //头信息设置, 使用FormData对象时设置该值为false 其他情况会自动设置
     processData:false, //处理数据方式, 使用FormData对象时设置该值为false  其他情况会自动设置
     success: function (response) { //发送成功后执行的回调函数 其参数是后端程序的返回数据
                console.log(response);
                }，
     error: function (xhr（xhr对象）, errMsg（错误信息）, e（可选 异常对象） ) {
            if (errMsg == 'timeout') {
                    alert('请求超时');
            } else {
                alert()
                }
 			}，
	 complete：function（）{}，//Ajax完成时执行的回调函数
     beforeSend:function() {} // 发送Ajax之前执行的回调函数
        });
    
    
```

用户信息. 图片的提交

1. 首先获取file表单控件 
2. 为其注册change事件(当有文件上传的时候触发)，
3. 创建上传表单对象， 专门用来做ajax的二进制文件上传
4. 将用户选择的图像文件添加到上传表单对象中
5. 发送头像上传的请求
  6.这里需要配置两个属性  
  processData: false, // jQuery不要去处理发送的数据
  contentType: false, // jQuery不要去设置Content-Type请求头
6. 将上传的头像显示在页面中
7. 最后将头像的地址储存在 隐藏域中

