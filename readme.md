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

## form中img的单独提交提交

```js
<script type="text/javascript">
// 获取文件上传控件
   s var upfile = $('#upfile');// #upfile 是file表单控件的id
// 当用户选择文件的时候 为控件添加change事件
    upfile.on('change', function () {
        // console.log(this.files[0]);
        // 创建上传表单对象 专门用来做ajax的二进制文件上传
        var formData = new FormData(); // （）里也可以传递参数
        // 将用户选择的图像文件添加到上传表单对象中
        formData.append('avatar', this.files[0]);
        // 发送头像上传的请求
        $.ajax({
            url: '/admin/upload',
            type: 'post',
            data: formData,
            processData: false, // jQuery不要去处理发送的数据
            contentType: false, // jQuery不要去设置Content-Type请求头
            success: function (response) {
                if (response.success) {
                    // 将上传的头像显示在页面中
                    $('#preview').attr('src', response.path);
                    // 将头像的地址存储在隐藏域中
                    $('#avatar').val(response.path);
                }
            }
        })
    });
</script>
```


