---
name: mpaas-offline-package
description: mPaaS离线包能力集成，支持H5页面离线化，加速加载速度，提升用户体验。
---

# mPaaS 离线包

## 功能特点

- H5 页面离线化
- 预加载策略
- 版本管理
- 增量更新
- 灰度发布

## 快速集成

### Android

```groovy
dependencies {
    implementation 'com.mPaaS:nebula:10.2.6'
}
```

```java
// 初始化离线包
Nebula.init(context);

// 配置离线包管理器
NebulaConfig config = new NebulaConfig();
config.setPreloadEnabled(true);
Nebula.configure(config);

// 预加载离线包
Nebula.preload("your-app-id");
```

### iOS

```ruby
pod 'mPaaS_Nebula'
```

```objc
// 导入头文件
#import <mPaasNebula/MPSNebulaAdapter.h>

// 初始化
[[MPSNebulaAdapter sharedAdapter] initWithAppKey:@"your-app-key"];

// 预加载
[[MPSNebulaAdapter sharedAdapter] preloadNebulaWithAppId:@"your-app-id"];
```

### 鸿蒙

```typescript
import nebula from '@mpaas/nebula';

// 初始化
nebula.init(context);

// 预加载
nebula.preload('your-app-id');
```

## 离线包管理

### 控制台配置

1. 在 mPaaS 控制台创建应用
2. 上传离线包文件
3. 配置版本和发布策略
4. 设置灰度比例

### 版本更新

```java
// 检查更新
Nebula.checkUpdate("your-app-id", new UpdateCallback() {
    @Override
    public void onCheckResult(UpdateResult result) {
        if (result.hasUpdate()) {
            // 有新版本，下载更新
            Nebula.downloadUpdate("your-app-id");
        }
    }
});
```

## 发布策略

- **全量发布**: 所有用户可见
- **灰度发布**: 按比例推送
- **定向发布**: 指定用户群
- **定时发布**: 定时生效

## 注意事项

- 控制台配置正确的离线包
- 设置合理的预加载策略
- 处理网络异常情况
- 监控离线包使用情况
