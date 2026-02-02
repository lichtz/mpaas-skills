---
name: mpaas-push-integration
description: mPaaS消息推送能力集成，支持Android、iOS、鸿蒙平台的统一消息推送。
---

# mPaaS 消息推送

## 功能特点

- 统一推送管理
- 多渠道触达
- 消息模板
- 定时推送
- 推送统计

## 快速集成

### Android

```groovy
dependencies {
    implementation 'com.mPaaS:push:10.2.6'
}
```

```java
// 初始化推送
Push.init(context);

// 获取推送 ID
String pushId = Push.getPushId();

// 接收消息
Push.setMessageHandler(new MessageHandler() {
    @Override
    public void onMessageReceived(Message message) {
        // 处理消息
        String title = message.getTitle();
        String content = message.getContent();
    }
});

// 点击通知
Push.setNotificationClickHandler(new ClickHandler() {
    @Override
    public void onClick(Message message) {
        // 处理点击事件
    }
});
```

### iOS

```ruby
pod 'mPaaS_推送'
```

```objc
// 导入头文件
#import <mPaasPush/MPSPushManager.h>

// 初始化
[[MPSPushManager sharedManager] initWithAppKey:@"your-app-key"];

// 获取推送 ID
NSString *pushId = [[MPSPushManager sharedManager] getPushId];

// 接收消息
[[MPSPushManager sharedManager] setMessageHandler:^(MPSMessage *message) {
    NSLog(@"收到消息: %@", message.content);
}];
```

### 鸿蒙

```typescript
import push from '@mpaas/push';

// 初始化
push.init(context);

// 获取推送 ID
let pushId = push.getPushId();

// 接收消息
push.onMessage((message) => {
    console.info('收到消息: ' + message.content);
});
```

## 推送管理

### 控制台配置

1. 配置推送证书
2. 创建消息模板
3. 设置推送策略
4. 查看推送统计

### 推送类型

- **通知栏消息**: 系统通知
- **透传消息**: 业务自定义
- **本地通知**: 定时提醒

## 消息模板

```json
{
  "templateId": "template-001",
  "title": "活动提醒",
  "content": "您有一个新活动待参与",
  "extras": {
    "action": "open_activity",
    "activityId": "12345"
  }
}
```

## 注意事项

- 控制台配置正确的推送证书
- 处理消息权限申请
- 统计推送效果
- 避免过度推送
