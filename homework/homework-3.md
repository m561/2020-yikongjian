# 第三节：js基础 ---作业
### csrf表单提交
```
        <form name="form1" action="" method="post" enctype="application/x-www-form-urlencoded">
            <label>账号</label><input type="text" value="dabai" name="name"/>
            <label>密码</label><input type="password" value="dabai" name="pass"/>
            <input type="submit" name="" id="sub" value="提交"/>
            <!-- <input type="button" value="submit" onclick="tsbu()"/> -->
        </form>
        <script>
            document.forms["form1"]["name"].value.submit();//提交的是具体的值，否则会提交成元素形式，无法获取具体的值
            //alert(document.forms["form1"]["name"].value);
        </script> 
```

### 邮箱校验
```
        <!-- 邮箱校验例子 -->
        <form name="ename" action="" method="POST" enctype="application/x-www-form-urlencoded">
            <label>email</label><input type="text" value="" name="email" placeholder="input email,like xxx@xx.com"/>
            <input type="button" value="submit" onclick="emailSubmit()"/>
            <!-- <input type="submit" name="" id="sub" value="submit"/> -->
        </form>
        <script>
            function emailSubmit(){
                var evalue = document.forms["ename"]["email"].value;
                // alert(evalue);
                var re = /^\w+@[a-z0-9]+\.[a-z]{2,4}$/;
                if(re.test(evalue)){  //test()方法，测试参数字符串是否满足正则表达式的验证，如果满足，返回true，否则，返回false
                    alert("提交成功")
                }else{
                    alert("邮箱格式错误，请重新提交")
                }
            }
        </script>
```

### html、css、js写一个好看的首页
```

```
