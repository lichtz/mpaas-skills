---
name: mpaas-data-sync
description: mPaaS数据同步能力，支持离线数据缓存、增量同步、冲突解决和多端数据一致性。
---

# mPaaS 数据同步

## 功能特点

- 离线数据缓存
- 增量数据同步
- 冲突自动解决
- 多端数据一致性
- 同步状态监控
- 断点续传

## 快速集成

### Android

```groovy
dependencies {
    implementation 'com.mPaaS:datasync:10.2.6'
}
```

```java
// 初始化同步服务
SyncConfig config = new SyncConfig();
config.setSyncInterval(5 * 60); // 5分钟
config.setMaxCacheSize(100 * 1024 * 1024); // 100MB
SyncService.init(context, config);

// 同步数据
SyncService.sync("user_data", new SyncCallback() {
    @Override
    public void onSuccess(SyncResult result) {
        // 同步成功
        List<DataItem> items = result.getData();
    }
    
    @Override
    public void onError(int code, String message) {
        // 同步失败
    }
});

// 监听同步状态
SyncService.addSyncListener(new SyncListener() {
    @Override
    public void onSyncProgress(SyncProgress progress) {
        // 同步进度
    }
});
```

### iOS

```ruby
pod 'mPaaS_DataSync'
```

```objc
// 初始化
MPSSyncConfig *config = [[MPSSyncConfig alloc] init];
config.syncInterval = 300; // 5分钟
config.maxCacheSize = 100 * 1024 * 1024;
[[MPSDataSync sharedSync] initWithConfig:config];

// 同步数据
[[MPSDataSync sharedSync] syncDataWithKey:@"user_data" 
                                 callback:^(MPSSyncResult *result, NSError *error) {
    if (error) {
        NSLog(@"同步失败: %@", error);
    } else {
        NSLog(@"同步成功: %lu 条数据", (unsigned long)result.data.count);
    }
}];
```

### 鸿蒙

```typescript
import sync from '@mpaas/datasync';

// 初始化
sync.init({
    syncInterval: 300,
    maxCacheSize: 100 * 1024 * 1024
});

// 同步数据
let result = await sync.sync('user_data');

// 监听同步状态
sync.onProgress((progress) => {
    console.info(`同步进度: ${progress.percent}%`);
});
```

## 同步策略

### 同步模式

- **实时同步**: 即时同步每次变更
- **定时同步**: 按设定间隔同步
- **手动同步**: 用户触发同步
- **增量同步**: 仅同步变更数据

### 冲突解决

- **服务端优先**: 以服务端数据为准
- **客户端优先**: 以客户端数据为准
- **时间戳优先**: 以最新时间为准
- **手动合并**: 用户自行选择

## 注意事项

- 合理设置同步间隔
- 处理网络异常
- 监控缓存使用情况
- 测试冲突解决逻辑
