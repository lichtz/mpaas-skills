---
name: mpaas-analytics
description: mPaaS移动数据分析服务，提供用户行为分析、埋点统计、漏斗分析和实时数据看板。
---

# mPaaS 移动分析

## 功能特点

- 用户行为追踪
- 自定义埋点
- 漏斗分析
- 留存分析
- 实时数据看板
- 多维数据报表

## 快速集成

### Android

```groovy
dependencies {
    implementation 'com.mPaaS:analytics:10.2.6'
}
```

```java
// 初始化分析服务
AnalyticsConfig config = new AnalyticsConfig();
config.setAppKey("your-app-key");
config.setChannel("your-channel");
config.setEnableAutoTrack(true); // 自动埋点
Analytics.init(context, config);

// 页面埋点
Analytics.pageStart("HomePage");
Analytics.pageEnd("HomePage");

// 事件埋点
Analytics.trackEvent("button_click", new HashMap<String, Object>() {{
    put("button_id", "login");
    put("button_type", "primary");
}});

// 用户属性
Analytics.setUserProperty("vip_level", "gold");
Analytics.setUserProperty("age", 25);
```

### iOS

```ruby
pod 'mPaaS_Analytics'
```

```objc
// 初始化
MPSAnalyticsConfig *config = [[MPSAnalyticsConfig alloc] init];
config.appKey = @"your-app-key";
config.channel = @"your-channel";
config.enableAutoTrack = YES;
[[MPSAnalytics sharedAnalytics] initWithConfig:config];

// 页面埋点
[[MPSAnalytics sharedAnalytics] pageStart:@"HomePage"];
[[MPSAnalytics sharedAnalytics] pageEnd:@"HomePage"];

// 事件埋点
[[MPSAnalytics sharedAnalytics] trackEvent:@"button_click" 
                                 withParams:@{@"button_id": @"login"}];

// 用户属性
[[MPSAnalytics sharedAnalytics] setUserProperty:@"vip_level" value:@"gold"];
```

### 鸿蒙

```typescript
import analytics from '@mpaas/analytics';

// 初始化
analytics.init({
    appKey: 'your-app-key',
    channel: 'your-channel',
    enableAutoTrack: true
});

// 页面埋点
analytics.pageStart('HomePage');
analytics.pageEnd('HomePage');

// 事件埋点
analytics.trackEvent('button_click', {
    button_id: 'login',
    button_type: 'primary'
});

// 用户属性
analytics.setUserProperty('vip_level', 'gold');
```

## 分析功能

### 漏斗分析

```java
// 定义漏斗
Funnel漏斗 = new Funnel("注册漏斗");
funnel.addStep("打开APP", 10000);
funnel.addStep("点击注册", 5000);
funnel.addStep("填写信息", 3000);
funnel.addStep("完成注册", 2000);
```

### 留存分析

```java
// 分析次日留存
RetentionReport report = Analytics.getRetentionReport(
    "2024-01-01", 
    "2024-01-07", 
    RetentionType.DAY_1
);
```

## 注意事项

- 合理设计埋点方案
- 保护用户隐私
- 控制埋点数量
- 定期分析数据
