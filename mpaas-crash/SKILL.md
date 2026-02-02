---
name: mpaas-crash-analytics
description: mPaaS崩溃分析服务，提供崩溃监控、堆栈追踪、错误统计和实时告警能力。
---

# mPaaS 崩溃分析

## 功能特点

- 崩溃实时监控
- 堆栈追踪分析
- 错误统计报表
- 设备信息收集
- 实时告警通知
- 版本对比分析

## 快速集成

### Android

```groovy
dependencies {
    implementation 'com.mPaaS:crash:10.2.6'
}
```

```java
// 初始化崩溃分析
CrashConfig config = new CrashConfig();
config.setEnableANR(true); // 捕获ANR
config.setEnableNative(true); // 捕获Native崩溃
config.setUploadEnabled(true); // 自动上传
CrashAnalytics.init(context, config);

// 自定义错误上报
try {
    // 业务代码
} catch (Exception e) {
    CrashAnalytics.reportException(e, "业务模块");
}

// 设置告警回调
CrashAnalytics.setAlertHandler(new AlertHandler() {
    @Override
    public void onAlert(CrashAlert alert) {
        // 发送告警通知
        sendNotification(alert);
    }
});
```

### iOS

```ruby
pod 'mPaaS_Crash'
```

```objc
// 初始化
MPSCrashConfig *config = [[MPSCrashConfig alloc] init];
config.enableANR = YES;
config.enableNative = YES;
config.autoUpload = YES;
[[MPSCrashAnalytics sharedAnalytics] initWithConfig:config];

// 自定义错误上报
@try {
    // 业务代码
} @catch (NSException *exception) {
    [[MPSCrashAnalytics sharedAnalytics] reportException:exception 
                                                 withModule:@"业务模块"];
}
```

### 鸿蒙

```typescript
import crash from '@mpaas/crash';

// 初始化
crash.init({
    enableANR: true,
    enableNative: true,
    uploadEnabled: true
});

// 错误上报
try {
    // 业务代码
} catch (error) {
    crash.reportException(error, '业务模块');
}
```

## 崩溃分析

### 崩溃类型

- **Java 崩溃**: Java 代码异常
- **Native 崩溃**: C/C++ 代码异常
- **ANR 卡顿**: 主线程阻塞
- **资源崩溃**: 内存/文件异常

### 分析维度

- **按版本**: 版本崩溃率
- **按设备**: 设备兼容性
- **按时间**: 趋势分析
- **按堆栈**: 问题定位

## 注意事项

- 合理配置采集策略
- 保护用户隐私
- 设置告警阈值
- 定期分析报表
