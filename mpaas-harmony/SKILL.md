---
name: mpaas-harmony-quickstart
description: 鸿蒙(HarmonyOS)应用接入mPaaS框架的快速入门指南，包括环境配置、项目初始化和核心功能集成。
---

# mPaaS 鸿蒙快速接入

## 快速开始

1. 安装 DevEco Studio 最新版本
2. 配置 mPaaS 依赖
3. 初始化 mPaaS 组件
4. 集成业务功能

## 环境准备

- **DevEco Studio**: 华为官方IDE
- **HarmonyOS SDK**: 3.0+
- **mPaaS SDK**: 最新版本

## 项目配置

### build-profile.json 配置

```json
{
  "app": {
    "signingConfigs": [],
    "compileSdkVersion": 9,
    "compatibleSdkVersion": 9,
    "targetSdkVersion": 9
  }
}
```

## 核心组件集成

- **统一扫码**: 集成扫码能力
- **移动网关**: API统一管理
- **数据同步**: 离线数据支持
- **消息推送**: 推送通知

## 详细指南

- **扫码能力**: [扫码开发指南](扫码开发指南)
- **网关配置**: [网关集成指南](网关集成指南)
- **离线包**: [离线包配置](离线包配置)

## 注意事项

- 确保已开通 mPaaS 产品
- 遵循 HarmonyOS 开发规范
- 测试真机兼容性
