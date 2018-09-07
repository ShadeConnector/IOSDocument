# 网关类

### 1.属性

| 属性 | 说明 |
| ------ | ------ |
| mac | 网关Mac地址，标识网关的唯一性 |
| hubName | 网关名称 |
| hubType | 网关类型 |
| online | 在线标识|
| ssid | 网关链接的网络ssid |
| ip | 网关内网IP地址 |
| fwVersion | 固件版本 |
| deviceCount | 网关已配对设备个数 |
| home | 网关绑定的Home |
| autoSetTime | 网关是否已开启自动对时 |
| modelCode | 网关数据点模板Code |
| signCode | 网关特征码 |
| serialNo | 网关序列号 |
| data | 网关数据点数据 |


### 2.方法

* 获取网关对象

```
+(instancetype)getHubDetailInfoWithMac:(NSString*) mac

参数: mac 网关Mac地址
返回: 网关对象详情

```

* 修改网关名称

```
- (void)updateHubNameWithName:(NSString*)name
                   completion:(BridgeBlock)completion

参数: name 网关名称
返回: 回调修改结果

```

* 绑定网关到Home下

```
- (void)bindHubToHomeWithHomeCode:(NSString *)homeCode
                       completion:(BridgeBlock)completion

参数: homeCode Home识别码
返回: 回调绑定结果

```

* 删除网关

```
- (void)deleteHubWithCompletion:(BridgeBlock)completion

参数: 无
返回: 回调删除结果

```

* 配对单双向设备

```
- (void)pairDeviceWithCurtainType:(NSInteger) curtainType
                       deviceType:(NSString*) deviceTye
                       completion:(BridgeBlock) completion

参数: curtainType 成品帘类型
      deviceTye 设备类型
返回: 回调配对结果结果

```

* 配对单双向设备

```
- (void)pairDeviceWithCurtainType:(NSInteger) curtainType
                       deviceType:(NSString*) deviceTye
                          timeOut:(NSTimeInterval)timeOut
                       completion:(BridgeBlock) completion

参数: curtainType 成品帘类型
      deviceTye 设备类型
      timeOut 超时时间
返回: 回调配对结果结果

```

* 校验Hub名称是否已经存在

```
+(BOOL)checkHubNameIsAlreadyExist:(NSString*) hubName

参数: hubName 场景名称
返回: YES-存在 NO-不存在

```

* 获取当前Hub最新固件版本

```
-(void)getHubRecentVersion:(BridgeBlock)completion

参数: 无
返回: 回调最新固件版本

```

* 获取当前Hub最新固件版本

```
+(void)getHubRecentVersionWithHubType:(NSString*)hubType
                           completion:(BridgeBlock)completion

参数: hubType - 网关类型
返回: 回调最新固件版本

```

* 网关升级

```
-(void)updateHubVersionWithVersionCode:(NSString*) versionCode
                               version:(NSString*) version
                            completion:(BridgeBlock) completion

参数: versionCode 版本识别码
      version 固件版本号
返回: 升级结果

```

* 网关配网添加网关

```
+(void)configNetWorkWithWifiSSID:(NSString *)ssid
                        password:(NSString *)password
                         timeOut:(NSInteger)timeOut
                         hubType:(NSString*)hubType
                      completion:(BridgeBlock)completion

参数: ssid 需要链接的网络SSID
      password 需要链接的网络密码
      timeOut 超时时间
      hubType 网关类型
返回: 回调配网添加结果

```

* 更新网关网络

```
-(void)updateNetWorkWithWifiSSID:(NSString *)ssid
                        password:(NSString *)password
                         timeOut:(NSInteger)timeOut
                      completion:(BridgeBlock)completion
参数: ssid 需要链接的网络SSID
      password 需要链接的网络密码
      timeOut 超时时间
返回: 回调网络更新结果

```
