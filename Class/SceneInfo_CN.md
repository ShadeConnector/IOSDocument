# 场景类

### 1.属性

| 属性 | 说明 |
| ------ | ------ |
| sceneID | 场景识别码，标识场景的唯一性 |
| sceneName | 场景名称 |
| sceneLogo | 场景个性化图片url |
| sceneIcon | 场景个性化图标索引值|
| home | 场景所在Home |
| deviceCount | 场景控制的设备个数 |
| isCorTimers | 场景是否已关联添加了定时器 |



### 2.方法

* 获取场景对象

```
+(SceneInfo *)getSceneInfoWithSceneID:(NSString *)sceneID

参数: sceneID 场景识别码
返回: 场景对象详情

```

* 获取场景列表

```
+ (void)getSceneListWithUseCache:(BOOL) useCache
                        homeCode:(NSString*) homeCode
                     completion:(BridgeBlock)completion

参数: useCache YES-获取缓存的场景列表 NO-获取服务器上的场景列表
      homeCode 场景所属的Home唯一码
返回: 回调场景列表

```

* 校验场景名称是否已经存在

```
+(BOOL)checkSceneNameIsAlreadyExist:(NSString*) sceneName

参数: sceneName 场景名称
返回: YES-存在 NO-不存在

```

* 删除场景

```
-(void)deleteSceneWithcompletion:(BridgeBlock)completion

参数: 无
返回: 回调删除结果

```

* 更新场景名称

```
-(void)updateSceneNameWithSceneName:(NSString*) sceneName
                         completion:(BridgeBlock) completion

参数: sceneName 场景名称称
返回: 回调修改结果

```

* 修改场景图标和图片信息

```
- (void)updateSceneIconWithSceneLogo:(NSData *) sceneLogo
                           sceneIcon:(NSInteger) sceneIcon
                          completion:(BridgeBlock)completion

参数: sceneLogo 场景图片数据(选填)
      sceneIcon 场景图标索引值(选填，不设置请填-1)
返回: 回调修改结果

```

* 修改设备所属房间

```
- (void)updateSceneWithSceneName:(NSString *) sceneName
                       sceneLogo:(NSData *) sceneLogo
                       sceneIcon:(NSInteger) sceneIcon
                         actions:(NSMutableArray <ActionInfo *>*)actions
                      completion:(BridgeBlock) completion

参数: sceneName 场景名称
      sceneLogo 场景图片数据(选填)
      sceneIcon 场景图标索引值(选填，不设置请填-1)
      actions 场景控制信息
返回: 回调修改结果

```

* 获取场景控制信息列表

```
-(NSMutableArray <ActionInfo *>*)getSceneActionList

参数: 无
返回: 控制信息列表

```

* 场景执行

```
- (void)triggerSceneWithCompletion:(BridgeBlock)completion

参数: 无
返回: 回调控制结果

```

* 获取场景关联的定时器列表

```
- (NSMutableArray<TimerInfo*> *)getCorTimersWithSortType:(Timer_Sort_Type) sortType
参数: Timer_Sort_Type 定时器排序方式
返回: 定时器列表

```
