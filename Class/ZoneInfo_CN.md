# 区域类

### 1.属性

| 属性 | 说明 |
| ------ | ------ |
| zoneCode | 区域识别码，标识区域的唯一性 |
| zoneName | 区域名称 |
| parentHomeCode | 区域所在Home的识别码 |
| zoneLogo | 区域个性化图片url |
| isDefault | 区域是否是默认生成的,YES时则该区域不允许删除 |
| isShared | 区域是否是他人分享得到 |
| sharedBy | 区域分享者账户，isShared为YES有效 |
| zoneIcon | 区域个性化图标索引值 |


### 2.方法

* 获取区域对象

```
+ (ZoneInfo *)getZoneInfoWithZoneCode:(NSString*) zoneCode

参数: zoneCode 区域识别码,唯一标识
返回: 区域对象详情

```

* 获取区域下缓存的所有房间列表

```
- (NSMutableArray <RoomInfo *>*)getAllRoomInfo

参数: 无
返回: 房间列表

```

* 校验区域名称是否已经存在

```
+(BOOL)checkZoneNameIsAlreadyExist:(NSString*) zoneName

参数: zoneName 区域名称
返回: YES-存在 NO-不存在

```

* 删除区域

```
- (void)deleteZoneWithcompletion:(BridgeBlock)completion

参数: 无
返回: 回调删除结果

```

* 修改区域个性化图片

```
- (void)updateZoneInfoWithIcon:(NSData *)image
                    completion:(BridgeBlock)completion

参数: image 图片数据
返回: 回调修改结果

```

* 更新区域信息

```
- (void)updateZoneWithZoneName:(NSString *)zoneName
                      zoneLogo:(NSData *)zoneLogo
                      zoneIcon:(NSInteger)zoneIcon
                    completion:(BridgeBlock)completion

参数: zoneName 区域名称
      zoneLogo 区域个性化图片数据
      zoneIcon 区域个性胡图标索引值
返回: 回调修改结果

```

* 当前区域下添加房间

```
- (void)addRoomWithRoomName:(NSString *)roomName
                   roomLogo:(NSData *)roomLogo
                   roomIcon:(NSInteger)roomIcon
                 completion:(BridgeBlock)completion

参数: roomName 房间名称
      roomLogo 房间个性化图片(选填)
      roomIcon 房间个性化图标索引值(选填)
返回: 回调添加结果

```
