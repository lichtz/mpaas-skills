---
name: mpaas-performance
description: mPaaS性能监控服务，提供应用性能指标采集、网络监控、内存分析和启动时间优化。
---

# mPaaS 性能监控

## 功能特点

- 应用性能指标 (APM)
- 网络性能监控
- 内存使用分析
- 启动时间优化
- 卡顿检测分析
- 自定义埋点

## 快速集成

### Android

```groovy
dependencies {
    implementation 'com.mPaaS:performance:10.2.6'
}
```

```java
// 初始化性能监控
PerformanceConfig config = new PerformanceConfig();
config.setEnableNetworkMonitor(true); // 网络监控
config.setEnableMemoryMonitor(true); // 内存监控
config.setEnableFPSMonitor(true); // FPS监控
config.setSamplingRate(0.1); // 采样率10%
PerformanceMonitor.init(context, config);

// 启动时间监控
PerformanceMonitor.startupTrace("app_start", new StartupCallback() {
    @Override
    public void onStartupComplete(StartupTrace trace) {
        long totalTime = trace.getTotalTime();
        long initTime = trace.getInitTime();
        long renderTime = trace.getRenderTime();
        // 上报启动时间
    }
});

// 自定义埋点
PerformanceMonitor.beginTrace("business_operation");
try {
    // 业务操作
} finally {
    PerformanceMonitor.endTrace("business_operation");
}
```

### iOS

```ruby
pod 'mPaaS_Performance'
```

```objc
// 初始化
MPSPerformanceConfig *config = [[MPSPerformanceConfig alloc] init];
config.enableNetworkMonitor = YES;
config.enableMemoryMonitor = YES;
config.enableFPSMonitor = YES;
config.samplingRate = 0.1;
[[MPSPerformanceMonitor sharedMonitor] initWithConfig:config];

// 启动时间监控
[[MPSPerformanceMonitor sharedMonitor] startStartupTrace:@"app_start" 
                                                callback:^(MPSStartupTrace *trace) {
    NSLog(@"启动时间: %lldms", (long long)trace.totalTime);
}];

// 自定义埋点
[[MPSPerformanceMonitor sharedMonitor] beginTrace:@"business_operation"];
// 业务操作
[[MPSPerformanceMonitor sharedMonitor] endTrace:@"business_operation"];
```

### 鸿蒙

```typescript
import performance from '@mpaas/performance';

// 初始化
performance.init({
    enableNetworkMonitor: true,
    enableMemoryMonitor: true,
    enableFPSMonitor: true,
    samplingRate: 0.1
});

// 启动时间监控
performance.startupTrace('app_start', (trace) => {
    console.info(`启动时间: ${trace.totalTime}ms`);
});

// 自定义埋点
performance.beginTrace('business_operation');
// 业务操作
performance.endTrace('business_operation');
```

## 监控指标

### 应用指标

- **启动时间**: 冷启动/热启动时间
- **内存使用**: 堆内存/Native内存
- **CPU 使用率**: 进程CPU占用
- **FPS**: 帧率稳定性
- **电量消耗**: 耗电分析

### 网络指标

- **请求耗时**: 接口响应时间
- **请求成功率**: 接口成功率
- **流量消耗**: 网络流量统计
- **错误率**: 请求错误率

## 注意事项

- 合理设置采样率
- 避免性能影响
- 保护用户隐私
- 设置告警阈值
