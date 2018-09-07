# 房间类

### 1.属性

| 属性 | 说明 |
| ------ | ------ |
| roomCode | 房间识别码，标识房间的唯一性 |
| roomName | 房间名称 |
| parentZoneCode | 房间所在区域的识别码 |
| roomLogo | 房间个性化图片url |
| deviceCount | 房间内设备个数 |
| isShared | 区域是否是他人分享得到 |
| sharedBy | 区域分享者账户，isShared为YES有效 |
| roomIcon | 房间个性化图标索引值 |


### 2.方法

* 获取房间对象

```
+ (RoomInfo *)getRoomInfoWithRoomCode:(NSString*) roomCode

参数: roomCode 房间识别码,唯一标识
返回: 房间对象详情

```

* 校验房间名称是否已经存在

```
+(BOOL)checkRoomNameIsAlreadyExist:(NSString*) roomName

参数: roomName 房间名称
返回: YES-存在 NO-不存在

```

* 获取当前房间下的所有设备列表

```
- (void)getDeviceListWithUseCache:(BOOL) useCache
                       completion:(BridgeBlock)completion

参数: YES-获取缓存的设备列表 NO-获取服务器上的设备列表
返回: 设备列表

```

* 获取当前房间下的所有缓存设备列表

```
- (NSMutableArray <DeviceInfo*> *)getDeviceListCache

参数: 无
返回: 设备列表

```

* 对当前房间下的所有设备列表排序

```
- (void)sortDeviceWithDeviceList:(NSMutableArray<DeviceInfo *>*)deviceList

参数: deviceList 排序后的设备列表
返回: 无

```

* 删除房间

```
- (void)deleteRoomWithcompletion:(BridgeBlock)completion

参数: 无
返回: 回调删除结果

```

* 修改房间个性化图片和个性化图标索引值

```
- (void)updateRoomInfoRoomIcon:(NSInteger ) roomIcon
                      roomLogo:(NSData *) roomLogo
                    completion:(BridgeBlock)completion

参数: roomIcon 图标索引值(选填)
      roomLogo 个性化图片数据
返回: 回调修改结果

```

* 修改房间详情信息

```
- (void)updateRoomWithRoomName:(NSString *)roomName
                      roomLogo:(NSData *)roomLogo
                      roomIcon:(NSInteger)roomIcon
                    completion:(BridgeBlock)completion

参数: roomName 房间名称
      roomIcon 图标索引值(选填)
      roomLogo 个性化图片数据
返回: 回调修改结果

```

* 修改房间名称

```
- (void)updateRoomNameWithRoomName:(NSString *)roomName
                        completion:(BridgeBlock)completion

参数: roomName 房间名称
返回: 回调修改结果

```

* 修改房间名称

```
- (void)updateRoomNameWithRoomName:(NSString *)roomName
                        completion:(BridgeBlock)completion

参数: roomName 房间名称
返回: 回调修改结果

```

* 房间内的设备批量控制

```
-(void)controlDevicesWithDevices:(NSArray*)devices
                      completion:(BridgeBlock)completion

参数: devices 组包好的设备列表
      devices保存的设备字典对象，其中字典包含如下几个Key
      key:data 组包好的数据点信息
      key:mac 设备mac地址
      key:type 设备类型
返回: 回调控制命令发送结果

```

* 房间内的设备批量控制

```
-(void)controlDevices:(NSArray <NSDictionary *>*)dataList
           completion:(BridgeBlock)completion

参数: devices 组包好的设备列表，格式参照设备单控
返回: 回调控制命令发送结果

```
