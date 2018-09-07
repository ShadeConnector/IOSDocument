# SDK管理

### 1.方法
* SDK生产环境初始化方法

```
-(void)initLibWithAppId:(NSString*) appId

参数: appId 厂商分配的App唯一标识
返回: 无

```
* SDK指定环境初始化方法

```
-(void)initLibWithAppId:(NSString*) appId
              debugMode:(BOOL) debugMode

参数: appId 厂商分配的App唯一标识
	  debugMode Yes-测试环境 NO-生产环境
返回: 无

```

* 获取SDK版本号

```
-(NSString*)version

参数: 无
返回: SDK版本号

```

* 用户登录

```
-(void)loginWithName:(NSString*)name
                Pass:(NSString*)pass
          Completion:(BridgeBlock)completion

参数: name 用户名
	  pass 密码
返回: 回调登录结果

```

* 用户登出

```
-(void)logOut

参数: 无
返回: 无

```

* 用户是否已登陆

```
-(BOOL)isLogin

参数: 无
返回: Yes-已登陆 NO-未登陆

```

* 获取上一次用户登录的账号

```
-(NSString *)getLastUserName

参数: 无
返回: 最近一次登陆的账号

```

* 获取上一次用户登录的密码

```
-(NSString *)getLastPassword

参数: 无
返回: 最近一次登陆的密码

```

* 上传日志

```
-(void)uploadLogCompletion:(BridgeBlock)completion

参数: 无
返回: 回调上报结果

```

* 日志打印开关(默认关闭)

```
-(void)printLog:(BOOL) print

参数: 无
返回: print YES-打印 NO-不打印

```

### 2.代理
* 通知设备状态变化的代理

```
-(void)deviceStatusChangeWithDeviceInfo:(DeviceInfo *)deviceInfo

参数: deviceInfo 设备详情

```

* 设备上下线代理

```
-(void)deviceOnlineChangeWithDevices:(NSArray <DeviceInfo*> *)devices
                               online:(BOOL)online

参数: devices 所有在线状态发生变化的设备列表
	  online	YES-上线 NO-离线

```

* 账户下所有设备和房间缓存已刷新

```
-(void)allDeviceAndRoomCacheRefresh

参数: 无

```

* 账户下所有场景缓存已刷新

```
-(void)allSceneCacheRefresh

参数: 无

```

* 账户下所有定时器缓存已刷新

```
-(void)allSceneCacheRefresh

参数: 无

```

* 服务器长连接状态的变化代理

```
-(void)didChangeServerConnectState:(ServerConnectState)state

参数: state 服务器的状态

```

* 版本升级进度更新

```
-(void)versionUpdateWithRateValue:(NSInteger)rateValue mac:(NSString*)mac

参数: rateValue 升级进度值(0-100)
	  mac WiFi设备或者网关mac地址	
```

* 登录Token失效,App需要退出重新登录

```
-(void)tokenAlreadyInvalid

参数: 无

```
