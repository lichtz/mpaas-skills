---
name: mpaas-hotfix
description: mPaaS热修复能力集成，支持Android、iOS、鸿蒙平台的Bug即时修复，无需重新发版。
---

# mPaaS 热修复

## 功能特点

- 即时修复 Bug
- 无需重新发版
- 增量更新
- 灰度验证
- 秒级生效

## 快速集成

### Android

```groovy
dependencies {
    implementation 'com.mPaaS:hotfix:10.2.6'
}
```

```java
// 初始化热修复
Hotfix.init(context);

// 检查修复
Hotfix.checkPatch(new PatchCallback() {
    @Override
    public void onCheckResult(PatchResult result) {
        if (result.hasPatch()) {
            // 下载并应用修复
            Hotfix.applyPatch();
        }
    }
});

// 手动触发修复
Hotfix.applyPatch();
```

### iOS

```ruby
pod 'mPaaS_Hotpatch'
```

```objc
// 导入头文件
#import <mPaasHotpatch/MPSHotpatchManager.h>

// 初始化
[[MPSHotpatchManager sharedManager] initWithAppKey:@"your-app-key"];

// 检查修复
[[MPSHotpatchManager sharedManager] checkPatchWithCallback:^(BOOL hasPatch) {
    if (hasPatch) {
        // 应用修复
        [[MPSHotpatchManager sharedManager] applyPatch];
    }
}];
```

### 鸿蒙

```typescript
import hotfix from '@mpaas/hotfix';

// 初始化
hotfix.init(context);

// 检查修复
hotfix.checkPatch((hasPatch) => {
    if (hasPatch) {
        hotfix.applyPatch();
    }
});
```

## 热修复管理

### 控制台配置

1. 上传修复包
2. 配置修复范围
3. 设置灰度比例
4. 发布修复

### 修复范围

- **全量修复**: 所有用户
- **灰度修复**: 按比例验证
- **定向修复**: 指定用户
- **紧急修复**: 优先推送

## 注意事项

- 控制台配置正确的修复包
- 先在灰度环境验证
- 监控修复效果
- 避免频繁修复
