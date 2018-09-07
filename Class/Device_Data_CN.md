# 设备辅助分类

### 方法

*  读取双向设备最新数据点信息(对TDBU无效)

```
- (void)readDeviceDataWithCompletion:(BridgeBlock)completion

参数: 无
返回: 回调设备最新对象详情

```

* 读取双向设备最新数据点信息

```
- (void)readDeviceDataWithOperation:(NSDictionary*) operation
                         completion:(BridgeBlock)completion

参数: operation 设备数据点组包信息
返回: 回调设备最新对象详情

```