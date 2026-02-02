---
name: mpaas-authentication
description: mPaaS用户认证服务，支持多种登录方式、OAuth授权、Token管理和SSO单点登录。
---

# mPaaS 用户认证

## 功能特点

- 多方式登录 (手机号/邮箱/账号)
- OAuth 2.0 授权
- Token 管理与刷新
- SSO 单点登录
- 生物识别认证
- 设备绑定

## 快速集成

### Android

```groovy
dependencies {
    implementation 'com.mPaaS:auth:10.2.6'
}
```

```java
// 初始化认证服务
AuthConfig config = new AuthConfig();
config.setAuthType(AuthType.ALL);
config.setTokenExpiresIn(7 * 24 * 60 * 60); // 7天
AuthService.init(context, config);

// 手机号登录
AuthService.loginByPhone("13800138000", "123456", new AuthCallback() {
    @Override
    public void onSuccess(AuthResult result) {
        String token = result.getToken();
        UserInfo user = result.getUserInfo();
    }
    
    @Override
    public void onError(int code, String message) {
        // 登录失败
    }
});

// 获取当前用户
UserInfo user = AuthService.getCurrentUser();
String token = AuthService.getToken();

// 登出
AuthService.logout();
```

### iOS

```ruby
pod 'mPaaS_Auth'
```

```objc
// 初始化
MPSAuthConfig *config = [[MPSAuthConfig alloc] init];
config.authTypes = MPSAuthTypePhone | MPSAuthTypeEmail;
config.tokenExpiresIn = 7 * 24 * 60 * 60;
[[MPSAuth sharedAuth] initWithConfig:config];

// 手机号登录
[[MPSAuth sharedAuth] loginWithPhone:@"13800138000" 
                            password:@"123456" 
                            callback:^(MPSAuthResult *result, NSError *error) {
    if (error) {
        NSLog(@"登录失败: %@", error);
    } else {
        NSLog(@"登录成功: %@", result.user.nickname);
    }
}];
```

### 鸿蒙

```typescript
import auth from '@mpaas/auth';

// 初始化
auth.init({
    authType: 'all',
    tokenExpiresIn: 7 * 24 * 60 * 60
});

// 手机号登录
let result = await auth.loginByPhone('13800138000', '123456');

// 获取当前用户
let user = auth.getCurrentUser();
let token = auth.getToken();

// 登出
auth.logout();
```

## 认证方式

- **账号密码**: 传统登录
- **手机验证码**: 短信登录
- **第三方OAuth**: 微信/支付宝登录
- **生物识别**: 指纹/面容
- **设备认证**: 设备绑定

## 注意事项

- 安全存储 Token
- 实现 Token 刷新机制
- 处理登录过期
- 保护用户隐私
