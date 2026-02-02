---
name: mpaas-ios-quickstart
description: iOS应用接入mPaaS框架的快速入门指南，包括CocoaPods集成、项目配置和核心功能集成。
---

# mPaaS iOS 快速接入

## 快速开始

1. 安装 Xcode 最新版本
2. 配置 CocoaPods 依赖
3. 初始化 mPaaS 组件
4. 集成业务功能

## 环境准备

- **Xcode**: 14.0+
- **CocoaPods**: 1.12.0+
- **iOS SDK**: 13.0+
- **mPaaS SDK**: 最新版本

## 项目配置

### Podfile 配置

```ruby
platform :ios, '13.0'
use_frameworks!

target 'YourApp' do
  pod 'mPaaS', '~> 10.2'
  pod 'mPaaS_Nebula'      # 离线包
  pod 'mPaaS_Scan'        # 扫码
  pod 'mPaaS_Gateway'     # 网关
  pod 'mPaaS_推送'         # 消息推送
end
```

## 核心组件集成

- **统一扫码**: 集成扫码能力
- **移动网关**: API统一管理
- **离线包**: H5页面加速
- **热修复**: Bug即时修复
- **消息推送**: 推送通知

## 详细指南

- **扫码能力**: [扫码开发指南](扫码开发指南)
- **网关配置**: [网关集成指南](网关集成指南)
- **离线包**: [离线包配置](离线包配置)
- **热修复**: [热修复配置](热修复配置)

## 注意事项

- 确保已开通 mPaaS 产品
- 配置正确的 Bundle ID
- 测试真机兼容性
- 遵循 iOS 开发规范
