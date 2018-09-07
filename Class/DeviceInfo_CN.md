# 设备类

### 1.属性

| 属性 | 说明 |
| ------ | ------ |
| mac | 设备Mac地址，标识设备的唯一性 |
| deviceName | 设备名称 |
| deviceType | 设备类型 |
| curatinType | 窗帘类型 (对单双向设备有效)|
| fwVersion | 设备固件(对单双向设备无效) |
| isShared | 设备是否是他人分享得到 |
| sharedBy | 设备分享者账户，isShared为YES有效 |
| deviceIcon | 设备个性化图标索引值 |
| deviceLogo | 设备个性化图片url |
| battery | 设备电池电量(对锂电池电机有效) |
| modelCode | 设备模板Code |
| deviceSignCode | 设备特征码 |
| serialNo | 设备序列号 |
| status | 设备状态(1:激活 2:冻结) |
| deviceOnline | 设备在线标识 |
| devData | 设备数据点数据 |
| room | 设备所在房间信息，如未设置则为nil |
| isCorTimers | 设备是否已关联添加了定时器 |
| ssid | 设备所连接网络的SSID，仅对Wifi设备有效 |
| hub | 设备绑定的网关，对单双向设备有效 |


### 2.方法

* 获取设备对象

```
-(instancetype)initWithMac:(NSString *)mac

参数: mac 设备mac地址
返回: 设备对象详情

```

* 拷贝生成设备对象

```
- (instancetype)initWithDeviceInfo:(DeviceInfo*)otherDeviceInfo

参数: otherDeviceInfo 被拷贝对象
返回: 设备对象详情

```

* 设备控制

```
- (void)controlDeviceWithData:(NSDictionary*)data
                   completion:(BridgeBlock)completion

参数: data 根据设备数据点生成的控制模板
返回: 回到控制数据下发结果

```

* 绑定设备到指定Home下

```
- (void)bindDeviceToHomeWithHomeCode:(NSString *)homeCode completion:(BridgeBlock)completion

参数: homeCode Home识别码
返回: 绑定结果

```

* 绑定设备到指定区域下

```
- (void)bindDeviceToZoneWithZoneCode:(NSString *)zoneCode
                          completion:(BridgeBlock)completion

参数: zoneCode 区域识别码
返回: 绑定结果

```

* 绑定设备到指定房间下

```
- (void)bindDeviceToRoomWithRoomCode:(NSString *)roomCode
                          completion:(BridgeBlock)completion

参数: roomCode 房间识别码
返回: 绑定结果

```

* 删除设备

```
- (void)deleteDeviceWithCompletion:(BridgeBlock)completion

参数: 无
返回: 回调删除结果

```

* 修改设备详情

```
- (void)updateDeviceInfoWithName:(NSString*)name
                        roomCode:(NSString*)roomCode
                      deviceLogo:(NSData *) deviceLogo
                      deviceIcon:(NSInteger) deviceIcon
                      completion:(BridgeBlock)completion

参数: name 设备名称
      roomCode 设备所属房间
      deviceLogo 设备个性化图片数据(选填)
      deviceIcon 设备个性化图标索引值(选填)
返回: 回调修改结果

```

* 修改设备名称

```
- (void)updateDeviceNameWithName:(NSString*)name
                      completion:(BridgeBlock)completion

参数: name 设备名称
返回: 回调修改结果

```

* 修改设备所属房间

```
- (void)updateDeviceRoomWithRoomCode:(NSString*)roomCode
                          completion:(BridgeBlock)completion

参数: roomCode 设备新房间识别码
返回: 回调修改结果

```

* 修改设备个性化图标索引值或个性化图片

```
- (void)updateDeviceIconWithDeviceLogo:(NSData *) deviceLogo
                            deviceIcon:(NSInteger) deviceIcon
                          completion:(BridgeBlock)completion

参数: deviceLogo 设备个性化图片数据(选填)
      deviceIcon 设备个性化图标索引值(选填)
返回: 回调修改结果

```

* 移动设备到Home层级下

```
- (void)moveDeviceToHomeWithHomeCode:(NSString*)homeCode
                            completion:(BridgeBlock)completion

参数: homeCode 设备待移动到的Home识别码
返回: 回调移动结果

```

* 校验设备名称是否已经存在

```
+(BOOL)checkDeviceNameIsAlreadyExist:(NSString *)deviceName

参数: deviceName 设备名称
返回: YES-存在  NO-不存在

```

* 获取当前设备最新版本号(仅对WiFi设备有效)

```
-(void)getDeviceRecentVersion:(BridgeBlock)completion

参数: 无
返回: 回调设备版本信息

```

* 获取指定设备类型最新版本号(仅对WiFi设备有效)

```
-(void)getDeviceRecentVersion:(BridgeBlock)completion

参数: deviceType 设备类型
返回: 回调设备版本信息

```

* 设备升级

```
-(void)updateDeviceVersionWithVersionCode:(NSString*) versionCode
                                  version:(NSString*) version
                              completion:(BridgeBlock) completion

参数: versionCode 版本唯一标识
      veresion 最新版本号
返回: 回掉升级命令下发结果，升级进度请关注BridgeManagerDelegate

```

* 设备行程值设置保存

```
-(void)savePointWithData:(NSDictionary*)data
              completion:(BridgeBlock) completion
参数: data 数据点控制数据
返回: 回掉设置结果

```

* WiFi设备配网

```
+(void)configNetWorkWithWifiSSID:(NSString *)ssid
                        password:(NSString *)password
                        timeOut:(NSInteger)timeOut
                     deviceType:(NSString*)deviceType
                    completion:(BridgeBlock)completion
参数: ssid 需要连接网络的ssid
      password 需要连接网络的密码
      timeOut 连接超时时间
      deviceType 所配置设备类型
返回: 回掉配置结果。如若成功，则会回调配网成功的设备对象

```

* WiFi更新网络

```
-(void)updateNetWorkWithWifiSSID:(NSString *)ssid
                        password:(NSString *)password
                         timeOut:(NSInteger)timeOut
                      completion:(BridgeBlock)completion
参数: ssid 需要连接网络的ssid
      password 需要连接网络的密码
      timeOut 超时时间
返回: 网络更新结果

```

* 获取设备关联的定时器列表

```
- (NSMutableArray<TimerInfo*> *)getCorTimersWithSortType:(Timer_Sort_Type) sortType
参数: Timer_Sort_Type 定时器排序方式
返回: 定时器列表

```
