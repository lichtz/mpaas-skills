---
name: mpaas-gateway
description: mPaaS移动网关集成，提供统一的API管理、请求路由、协议转换和安全防护能力。
---

# mPaaS 移动网关

## 功能特点

- 统一 API 管理
- 请求路由转发
- 协议转换 (HTTP/HTTPS/WebSocket)
- API 认证与授权
- 流量控制与限流
- 日志监控

## 快速集成

### Android

```groovy
dependencies {
    implementation 'com.mPaaS:gateway:10.2.6'
}
```

```java
// 初始化网关
GatewayConfig config = new GatewayConfig();
config.setBaseUrl("https://api.yourdomain.com");
config.setTimeout(30);
Gateway.init(config);

// 发起请求
GatewayRequest request = new GatewayRequest("/api/user/info");
request.addHeader("Authorization", "Bearer " + token);

Gateway.execute(request, new Callback<UserInfo>() {
    @Override
    public void onSuccess(UserInfo userInfo) {
        // 处理成功结果
    }
    
    @Override
    public void onError(int code, String message) {
        // 处理错误
    }
});
```

### iOS

```ruby
pod 'mPaaS_Gateway'
```

```objc
// 初始化
MPSGatewayConfig *config = [[MPSGatewayConfig alloc] init];
config.baseURL = @"https://api.yourdomain.com";
config.timeout = 30;
[[MPSGateway sharedGateway] initWithConfig:config];

// 发起请求
MPSGatewayRequest *request = [[MPSGatewayRequest alloc] init];
request.path = @"/api/user/info";
request.method = MPSGatewayMethodGET;

[[MPSGateway sharedGateway] execute:request callback:^(id result, NSError *error) {
    if (error) {
        NSLog(@"请求失败: %@", error);
    } else {
        NSLog(@"用户信息: %@", result);
    }
}];
```

### 鸿蒙

```typescript
import gateway from '@mpaas/gateway';

// 初始化
gateway.init({
    baseUrl: 'https://api.yourdomain.com',
    timeout: 30
});

// 发起请求
let response = await gateway.request('/api/user/info', {
    method: 'GET',
    headers: {
        'Authorization': `Bearer ${token}`
    }
});
```

## 网关配置

### 控制台配置

1. 创建 API 分组
2. 配置路由规则
3. 设置认证方式
4. 配置限流策略
5. 添加监控告警

### 认证方式

- **AppKey + Secret**: 简单认证
- **OAuth 2.0**: 标准授权
- **JWT**: Token 认证
- **自定义**: 扩展认证

## 注意事项

- 配置正确的网关地址
- 处理网络异常情况
- 设置合理的超时时间
- 实现请求重试机制
