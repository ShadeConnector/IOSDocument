# 用户类

### 1.属性

| 属性 | 说明 |
| ------ | ------ |
| userCode | 用户识别码，标识用户的唯一性 |
| email | 用户邮箱 |
| mobileNo | 用户手机号 |
| nickName | 用户呢称 |
| logo | 用户头像url |
| sex | 性别 |
| name | 用户真实姓名 |
| birthday | 用户生日 |
| location | 用户联系地址 |
| securityNum | 用户身份证号码 |
| remark | 用户备注 |


### 2.方法

* 获取当前登录用户信息

```
+(UserInfo *)getUserInfo

参数: 无
返回: 用户对象详情

```

* 刷新用户详情数据

```
-(void)refreshUserDetail:(BridgeBlock) completion

参数: 无
返回: 回调,responsobject返回为布尔值 TRUE-刷新成功 FALSE-刷新失败

```

* 校验用户是否存在

```
+(void)checkUserIsExistWithName:(NSString*) name
                     Completion:(BridgeBlock) completion

参数: name 用户名
返回: 回调responsobject返回为布尔值 TRUE-存在 FALSE-不存在

```

* 获取手机验证码(暂时仅支持中国大陆手机号)

```
+(void)requestVerifyCodeWithMobileNo:(NSString *)mobileNo
                          completion:(BridgeBlock)completion

参数: mobileNo 手机号
返回: 回调获取结果

```

* 注册校验手机验证码(暂时仅支持中国大陆手机号)

```
+(void)registerCheckVerifyCodeWithMobileNo:(NSString*)mobileNo
                                verifyCode:(NSString*)verifyCode
                                  completion:(BridgeBlock)completion

参数: mobileNo 手机号
      verifyCode 验证码
返回: 回调校验结果

```

* 重置密码校验手机验证码(暂时仅支持中国大陆手机号)

```
+(void)resetPasswordCheckVerifyCodeWithMobileNo:(NSString *)mobileNo
                                     verifyCode:(NSString*)verifyCode
                                     completion:(BridgeBlock)completion

参数: mobileNo 手机号
      verifyCode 验证码
返回: 回调校验结果

```

* 手机号账户重置密码(暂时仅支持中国大陆手机号)

```
+(void)resetPasswordWithMobileNo:(NSString *)mobileNo
                      verifyCode:(NSString*)verifyCode
                        password:(NSString*)password
                      completion:(BridgeBlock)completion

参数: mobileNo 手机号
      verifyCode 验证码
      password 用户设置的新密码
返回: 回调重置结果

```

* 注册账户

```
+ (void)registerWithUserName:(NSString *)userName
                        pass:(NSString *)pass
                  completion:(BridgeBlock)completion

参数: userName 用户名(邮箱或中国大陆手机号)
      password 用户设置的密码
返回: 回调注册结果

```

* 邮箱用户忘记密码

```
+(void)forgotPwdWithUserName:(NSString *)userName
                  completion:(BridgeBlock)completion

参数: userName 用户名(邮箱或中国大陆手机号)
返回: 回调操作结果

```

* 更新用户头像

```
- (void)updateUserInfoWithIcon:(NSData *)image
                    completion:(BridgeBlock)completion

参数: image 用户头像信息
返回: 回调操作结果

```

* 修改用户头像及昵称

```
- (void)updateUserInfoWithIcon:(NSData *)image
                      nickNmae:(NSString*)nickName
                    completion:(BridgeBlock)completion

参数: image 用户头像信息
      nickName 用户昵称
返回: 回调操作结果

```

* 登陆后修改用户密码

```
- (void)updatePwdWithPassword:(NSString *)password
                       oldPwd:(NSString *)oldPwd
                   completion:(BridgeBlock)completion

参数: password 用户设置的新密码
      oldPwd 用户原来密码
返回: 回调操作结果

```

* 登陆后修改用户密码

```
- (void)updateUserInfoWithNickName:(NSString *)nickName
                             email:(NSString *)email
                          mobileNo:(NSString *)mobileNo
                               sex:(NSString *)sex
                          realName:(NSString *)realName
                          birthday:(NSString *)birthday
                          location:(NSString *)location
                       securityNum:(NSString *)securityNum
                            remark:(NSString *)remark
                        completion:(BridgeBlock)completion

参数: nickName 用户昵称
      email 邮箱
      mobileNo 手机号
      sex 性别
      realName 真实姓名
      birthday 生日
      location 联系地址
      securityNum 身份证号
      remark 备注信息(要求存放json格式数据)
返回: 回调操作结果

```
