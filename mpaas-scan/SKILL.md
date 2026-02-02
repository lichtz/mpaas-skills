---
name: mpaas-scan-integration
description: mPaaS统一扫码能力集成，支持Android、iOS、鸿蒙平台的扫码功能开发。
---

# mPaaS 扫码功能

## 平台支持

- ✅ Android
- ✅ iOS
- ✅ 鸿蒙

## 快速集成

### Android

```groovy
dependencies {
    implementation 'com.mPaaS:scan:10.2.6'
}
```

```java
// 初始化扫码服务
ScanManager.getInstance().init(context);

// 启动扫码
ScanManager.getInstance().startScan(activity, new ScanCallback() {
    @Override
    public void onScanResult(ScanResult result) {
        // 处理扫码结果
        String content = result.getContent();
    }
});
```

### iOS

```ruby
pod 'mPaaS_Scan'
```

```objc
// 导入头文件
#import <mPaasScan/MPScanManager.h>

// 初始化
[[MPScanManager sharedManager] initWithAppKey:@"your-app-key"];

// 扫码
[[MPScanManager sharedManager] startScanWithController:self 
                                              callback:^(MPScanResult *result) {
    NSLog(@"扫码结果: %@", result.content);
}];
```

### 鸿蒙

```typescript
// 导入扫码模块
import scan from '@mpaas/scan';

// 初始化
scan.init(this.context);

// 扫码
scan.startScan({
    onResult: (result) => {
        console.info('扫码结果: ' + result.content);
    }
});
```

## 支持的码类型

- 一维码: EAN-13, EAN-8, Code-39, Code-128, ITF
- 二维码: QR Code, Data Matrix, PDF-417

## 详细配置

### 自定义扫码界面

```java
ScanConfig config = new ScanConfig();
config.setScanAreaColor(Color.parseColor("#FFFFFF"));
config.setScanLineColor(Color.parseColor("#FF0000"));
ScanManager.getInstance().setScanConfig(config);
```

## 注意事项

- 需要在 mPaaS 控制台开通扫码服务
- 配置正确的 App Key
- 处理相机权限
- 测试多种码类型的识别率
