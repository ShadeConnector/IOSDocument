# HomeInfo类

### 1.属性

| 属性 | 说明 |
| ------ | ------ |
| homeCode | Home识别码,标识Home的唯一性 |
| homeName | Home名称 |
| homeLogo | Home个性化图片url |
| location | Home所在的地理位置 |
| isDefault | Home是否是默认生成的,YES时则该home不允许删除 |
| isShared | Home是否是他人分享得到 |
| sharedBy | Home分享者账户，isShared为YES有效 |
| homeIcon | Home个性化图标索引值 |
| roomCount | Home里的房间个数 |
| zoneCount | Home里的区域个数 |


### 2.方法
##### 2.1 Home相关操作
* 获取Home对象

```
+(HomeInfo *)getHomeInfoWithHomeCode:(NSString*) homeCode

参数: homeCode Home唯一标识
返回: Home对象详情

```

* 获取账号下所有Home缓存列表

```
+(NSMutableArray <HomeInfo*> *)getCacheHomeList

参数: 无
返回: Home列表

```

* 获取账号下缓存的Home个数

```
+(NSInteger)getCacheHomeCount

参数: 无
返回: Home个数

```

* 获取home列表(默认排序方式)

```
+(void)getHomeListWithUseCache:(BOOL) useCache
                   	completion:(BridgeBlock)completion

参数: useCache YES-获取缓存的Home列表 NO-获取服务器上的Home列表
返回: 回调Home列表

```

* 获取home列表(分享得到的Home排序在后)

```
+ (void)getHomeListWithUseCache_sort:(BOOL)useCache
                        	completion:(BridgeBlock)completion

参数: useCache YES-获取缓存的Home列表 NO-获取服务器上的Home列表
返回: 回调Home列表

```

* 只获取自己创建的home列表(不包含其他用户分享来的Home)

```
+ (void)getHomeListWithUseCache_createSelf:(BOOL) useCache
                                completion:(BridgeBlock)completion

参数: useCache YES-获取缓存的Home列表 NO-获取服务器上的Home列表
返回: 回调Home列表

```

* 添加Home

```
+ (void)addHomeWithHomeName:(NSString *)homeName
                   homeLogo:(NSData *)homeLogo
                   homeIcon:(NSInteger)homeIcon
                   location:(CLLocation*)location
                 completion:(BridgeBlock)completion

参数: homeName Home名称
      homeLogo home个性化图片(选填)
      homeIcon home个性化图标索引值(选填)
      location home所在位置(选填)
返回: 回调Home添加结果

```

* 校验Home名称是否已经存在

```
+(BOOL)checkHomeNameIsAlreadyExist:(NSString*) homeName

参数: homeName Home名称
返回: YES-存在 NO-不存在

```

* 删除Home

```
- (void)deleteHomeWithcompletion:(BridgeBlock)completion

参数: 无
返回: 回调删除结果

```

* 修改Home个性化图片

```
- (void)updateHomeInfoWithIcon:(NSData *)image
                    completion:(BridgeBlock)completion

参数: image 图片数据
返回: 回调修改结果

```

* 修改Home位置信息

```
- (void)updateHomeInfoWithLocation:(CLLocation *)location
                        completion:(BridgeBlock)completion

参数: location Home位置
返回: 回调修改结果

```

* 修改Home信息

```
- (void)updateHomeWithHomeName:(NSString *)homeName
                      homeLogo:(NSData *)homeLogo
                      homeIcon:(NSInteger)homeIcon
                      location:(CLLocation*)location
                    completion:(BridgeBlock)completion

参数: homeName Home名称
      homeLogo home个性化图片(选填)
      homeIcon home个性化图标索引值(选填)
      location home所在位置(选填)
返回: 回调修改结果

```
  
##### 2.2 区域相关操作

* 在当前Home下添加区域  


```
- (void)addZoneWithZoneName:(NSString *)zoneName
                   zoneLogo:(NSData *)zoneLogo
                   zoneIcon:(NSInteger)zoneIcon
                 completion:(BridgeBlock)completion

参数: zoneName 区域名称
      zoneLogo 区域个性化图片(选填)
      zoneIcon home个性化图标索引值(选填)
返回: 回调添加结果

```

* 获取当前Home下的所有缓存的区域列表

```
- (NSMutableArray <ZoneInfo *>*)getAllZoneInfo

参数: 无
返回: 区域列表

```

##### 2.3 房间相关操作

* 获取当前home里面的所有房间列表

```
- (void)getRoomListWithUseCache:(BOOL) useCache
                     completion:(BridgeBlock)completion

参数: useCache YES-获取缓存的房间列表 NO-获取服务器上的房间列表
返回: 回调房间列表

```

* 当前Home下添加房间(添加到Home下默认区域里)

```
- (void)addRoomWithRoomName:(NSString *)roomName
                   roomLogo:(NSData *)roomLogo
                   roomIcon:(NSInteger)roomIcon
                 completion:(BridgeBlock)completion

参数: roomName 房间名称
      roomLogo 房间个性化图片(选填)
      roomIcon 房间个性化图标索引值(选填)
返回: 回调房间列表

```

* 当前Home下添加房间(添加到Home下默认区域里)

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

* 获取当前Home下缓存的所有房间及设备列表

```
- (NSMutableArray*)getRoomAndRoomDevices

参数: 无
返回: 设备和房间列表

```

* 获取当前Home里面的所有缓存的房间列表

```
- (NSMutableArray<RoomInfo*>*)getRoomListCache

参数: 无
返回: 房间列表

```

* 获取当前Home里面的所有缓存的房间列表

```
- (NSMutableArray<RoomInfo*>*)getRoomListCache

参数: 无
返回: 房间列表

```

* 获取当前Home下缓存的房间个数

```
-(NSInteger)getCacheRoomCount

参数: 无
返回: 房间个数

```

* 对当前Home下房间进行排序

```
- (void)sortRoomWithRoomList:(NSMutableArray <RoomInfo *>*)roomList

参数: roomList 排序后的房间列表
返回: 无

```

##### 2.4 设备相关操作

* 获取当前Home下所有设备列表

```
-(void)getDeviceListWithUseCache:(BOOL) useCache
                      completion:(BridgeBlock)completion

参数: useCache YES-获取缓存的设备列表 NO-获取服务器上的设备列表
返回: 回调设备列表

```

* 获取当前Home下所有缓存的设备

```
- (NSMutableArray <DeviceInfo *>*)getDeviceListCache

参数: 无
返回: 设备列表

```

* 获取当前Home下缓存的设备个数

```
-(NSInteger)getCacheDeviceCount

参数: 无
返回: 设备个数

```

* 获取当前Home下缓存的所有没有分配房间的设备列表

```
- (NSMutableArray <DeviceInfo *>*)getUnassignedDeviceListCache

参数: 无
返回: 设备列表

```

* 对当前Home下设备进行排序

```
- (void)sortDeviceList:(NSMutableArray <DeviceInfo *>*)deviceList

参数: deviceList 排序后的设备列表
返回: 无

```

##### 2.5 场景相关操作

* 获取当前Home下所有场景列表

```
- (void)getSceneListWithUseCache:(BOOL) useCache
                      completion:(BridgeBlock)completion

参数: useCache YES-获取缓存的场景列表 NO-获取服务器上的场景列表
返回: 回调场景列表

```

* 获取当前Home下缓存的场景个数

```
-(NSInteger)getCacheSceneCount

参数: 无
返回: 场景个数

```

* 对当前Home下的场景排序

```
- (void)sortSceneWithSceneList:(NSMutableArray<SceneInfo *>*)sceneList

参数: 排序后的场景列表
返回: 无

```

* 当前Home下添加场景

```
- (void)addSceneWithSceneName:(NSString *) sceneName
                    sceneLogo:(NSData *) sceneLogo
                    sceneIcon:(NSInteger ) sceneIcon
                      actions:(NSMutableArray <ActionInfo *>*)actions
                   completion:(BridgeBlock)completion

参数: sceneName 场景名称
      sceneLogo 场景个性化图片数据 (选填。如设置，则sceneIcon失效)
      sceneIcon 场景个性化图标索引值(选填，值大于0，不设置请置-1。如设置，则sceneLogo失效)
      actions 场景控制的设备动作列表
返回: 回调添加结果

```

* 当前Home下添加场景并给场景添加定时器

```
- (void)addSceneWithSceneName:(NSString *) sceneName
                    sceneLogo:(NSData *) sceneLogo
                    sceneIcon:(NSInteger ) sceneIcon
                      actions:(NSMutableArray <ActionInfo *>*)actions
                       timers:(NSMutableArray <TimerInfo *>*)timers
                   completion:(BridgeBlock)completion

参数: sceneName 场景名称
     sceneLogo 场景个性化图片数据 (选填。如设置，则sceneIcon失效)
     sceneIcon 场景个性化图标索引值(选填，值大于0，不设置请置-1。如设置，则sceneLogo失效)
     actions 场景控制的设备动作列表
     timers 场景关联的定时器列表
返回: 回调添加结果

```
##### 2.6 定时器相关操作
* 新增定时器

```
- (void)addTimerWithTimerInfo:(TimerInfo *)timer
                    completion:(BridgeBlock)completion

参数: timer 待添加的定时器对象，注意action属性和scene属性不能同时设置
返回: 回调添加结果

```

* 获取当前Home下所有定时器列表

```
- (void)getTimerListWithUseCache:(BOOL) useCache
                        sortType:(Timer_Sort_Type) sortType
                      completion:(BridgeBlock)completion

参数: useCache YES-获取缓存的定时器列表 NO-获取服务器上的定时器列表
返回: 回调定时器列表

```

* 获取当前Home下缓存的定时器个数

```
-(NSInteger)getCacheTimerCount

参数: 无
返回: 定时器个数

```

* 对当前Home的定时器排序

```
- (void)sortTimerWithTimerList:(NSMutableArray<TimerInfo *>*)timerList

参数: timerList 排序后的定时器列表
返回: 定时器个数

```

##### 2.7 分享功能相关操作

* 获取当前Home已分享的账户列表

```
- (void)getSharedUserListWithCompletion:(BridgeBlock)completion

参数: 无
返回: 回调账户列表

```

* 将当前Home分享给指定账户

```
- (void)shareToUserWithUserName:(NSString*)userName
                     completion:(BridgeBlock)completion

参数: userName 账户名
返回: 回调分享结果

```

* 取消当前Home对指定用户的分享

```
- (void)shareToUserWithUserName:(NSString*)userName
                     completion:(BridgeBlock)completion

参数: userName 账户名
返回: 回调取消分享结果

```

##### 2.8 网关相关操作

* 获取当前Home下的网关列表

```
- (void)getHubListWithUseCache:(BOOL) useCache
                      completion:(BridgeBlock)completion

参数: useCache YES-获取缓存的网关列表 NO-获取服务器上的网关列表
返回: 回调网关列表

```

* 获取当前Home下缓存的网关个数

```
-(NSInteger)getCacheHubCount

参数: 无
返回: 网关个数

```

* 获取当前Home下缓存的网关列表

```
- (NSMutableArray <HubInfo *>*)getHubListCache

参数: 无
返回: 网关列表

```


