---
name: mpaas-android-quickstart
description: Android应用接入mPaaS框架的快速入门指南，包括Android Studio插件集成、项目配置和核心功能集成。
---

# mPaaS Android 快速接入

## 快速开始

1. 安装 Android Studio 最新版本
2. 安装 mPaaS Android Studio 插件
3. 开通 mPaaS 产品
4. 集成业务功能

## 环境准备

- **Android Studio**: 2023.0+
- **mPaaS 插件**: 最新版本
- **阿里云账号**: 已开通 mPaaS
- **Android SDK**: 21+

## 项目配置

### build.gradle 配置

```groovy
android {
    defaultConfig {
        targetSdkVersion 34  // 最新基线
        ndk {
            abiFilters 'armeabi-v7a', 'arm64-v8a'
        }
    }
}

dependencies {
    implementation 'com.mPaaS:mPaaS:10.2.6'
    implementation 'com.mPaaS:nebula:10.2.6'       // 离线包
    implementation 'com.mPaaS:scan:10.2.6'         // 扫码
    implementation 'com.mPaaS:gateway:10.2.6'      // 网关
    implementation 'com.mPaaS:push:10.2.6'         // 推送
}
```

## 核心组件集成

- **统一扫码**: 集成扫码能力
- **移动网关**: API统一管理
- **离线包**: H5页面加速
- **热修复**: Bug即时修复
- **消息推送**: 推送通知
- **数据同步**: 离线数据支持

## 详细指南

- **扫码能力**: [扫码开发指南](扫码开发指南)
- **网关配置**: [网关集成指南](网关集成指南)
- **离线包**: [离线包配置](离线包配置)
- **热修复**: [热修复配置](热修复配置)
- **推送集成**: [推送配置](推送配置)

## 注意事项

- 确保已开通 mPaaS 产品
- 配置正确的包名和签名
- 测试多机型兼容性
- 遵循 Android 开发规范
