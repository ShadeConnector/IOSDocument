# 定时器类

### 1.常量值
* 定时器类型 Timer\_Ctrl_Type

| 属性 | 说明 |
| ------ | ------ |
| Timer\_Ctrl\_Type_Scene | 场景定时器 |
| Timer\_Ctrl\_Type_Device | 设备定时器 |

* 定时器循环方式 Timer\_Cycle_Type

| 属性 | 说明 |
| ------ | ------ |
| Timer\_Cycle\_Type_Invalid | 无效 |
| Timer\_Cycle\_Type_Dally | 按天循环 |
| Timer\_Cycle\_Type_Weekly | 按周循环 |
| Timer\_Cycle\_Type_None | 不循环 |

* 定时器时间值类型 Timer\_Time_Type

| 属性 | 说明 |
| ------ | ------ |
| Timer\_Time\_Type_Invalide | 无效 |
| Timer\_Time\_Type_Normal_Time | 普通时间值 |
| Timer\_Time\_Type_Sunset | 日落 |
| Timer\_Time\_Type_Sunrise | 日出 |

### 2.属性

| 属性 | 说明 |
| ------ | ------ |
| timerCode | 定时器识别码,标识定时器的唯一性 |
| timerAlias | 定时器名称 |
| timerIcon | 定时器个性化图标索引值 |
| isOpen | 定时器是否使能|
| cycleType | 定时器循环方式|
| dayCycle | 重复日期，数组格式:[1,2,3,....]。仅对按天循环方式有效|
| weekCycle | 重复星期。仅对按周循环方式有效|
| timeType | 时间值类型|
| timeValue | 触发时间值。仅对Timer\_Time\_Type\_Normal_Time有效|
| timeZone | 时区。例如Asia/Shanghai|
| timeOffset | 定时器触发时间偏移量(±60min) 仅对日出日落类型定时器有效|
| timerCtrlType | 定时器控制类型|
| action | 定时器控制的设备动作，仅当timerCtrlType为Timer\_Ctrl\_Type\_Device有效|
| action | 定时器控制的场景，仅当timerCtrlType为Timer\_Ctrl\_Type\_Scene有效|
| home | 定时器所在的Home|

### 3.方法

* 获取定时器对象

```
+(TimerInfo *)getTimerInfoWithTimerCode:(NSString *)timerCode

参数: timerCode 定时器识别码
返回: 定时器对象详情

```

* 获取指定Home下的定时器列表

```
+ (void)getTimerListWithUseCache:(BOOL) useCache
                        sortType:(Timer_Sort_Type) sortType
                        homeCode:(NSString*) homeCode
                      completion:(BridgeBlock)completion

参数: useCache YES-获取缓存的定时器列表 NO-获取服务器上的定时器列表
      sortType 排序方式
      homeCode Home识别码
返回: 回调定时器列表

```

* 删除定时器

```
- (void)deleteTimerWithcompletion:(BridgeBlock)completion

参数: 无
返回: 回调删除结果

```

* 校验定时器名称是否已经存在

```
+(BOOL)checkTimerNameIsAlreadyExist:(NSString*) timerName

参数: timerName 定时器名称
返回: YES-存在 NO-不存在

```

* 修改定时器信息(直接对成员属性修改之后，调用此方法)

```
- (void)updateTimerInfoCompletion:(BridgeBlock)completion

参数: 无
返回: 回调修改结果

```

* 修改定时器的使能状态

```
- (void)changeTimerStatus:(BOOL)isOpen completion:(BridgeBlock)completion

参数: isOpen YES-使能 NO-不使能
返回: 回调修改结果

```