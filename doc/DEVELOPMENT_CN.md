# 开发指南

本仓库是一个 **Melos monorepo**，包含两个 package：`fluwx`（含微信支付）和 `fluwx_no_pay`（不含支付，用于通过 App Store 合规审核）。以下步骤适用于想要在本地构建或运行项目的贡献者。

### 前置要求

- Flutter SDK（stable 渠道）
- Dart SDK ≥ 3.10
- Melos 7.5.1：`dart pub global activate melos 7.5.1`
- iOS 开发：Xcode + CocoaPods（`sudo gem install cocoapods`）

### 克隆 & 初始化

```bash
git clone https://github.com/OpenFlutter/fluwx.git
cd fluwx

# 安装工作区依赖并链接各 package
dart pub get
melos bootstrap
```

> **注意：** 仓库使用了 symlink（在 `fluwx` 和 `fluwx_no_pay` 之间共享原生源码）。macOS / Linux 下 git 会自动保留 symlink；Windows 下请确保 git 配置了 `core.symlinks=true`。

初始化完成后验证所有 symlink 是否正常：

```bash
melos run symlinks:check
```

### 运行示例应用

```bash
# fluwx（含支付）
cd packages/fluwx/example
flutter pub get
flutter run

# fluwx_no_pay（不含支付）
cd packages/fluwx_no_pay/example
flutter pub get
flutter run
```

### iOS — CocoaPods 与 SPM

项目同时支持 CocoaPods 和 Swift Package Manager，构建前全局设置集成方式：

```bash
# CocoaPods 模式
flutter config --no-enable-swift-package-manager
cd packages/fluwx/example/ios && pod install

# SPM 模式
flutter config --enable-swift-package-manager
```

### 分析 & 测试所有 package

```bash
melos exec -- flutter analyze
melos exec -- flutter test
```

---