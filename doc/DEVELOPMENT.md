# Development


This repository is a **Melos monorepo** containing two packages: `fluwx` (with WeChat Pay) and `fluwx_no_pay` (without Pay, for App Store compliance). The following steps are for contributors who want to build or run the project locally.

### Prerequisites

- Flutter SDK (stable channel)
- Dart SDK ≥ 3.10
- Melos 7.5.1: `dart pub global activate melos 7.5.1`
- For iOS: Xcode + CocoaPods (`sudo gem install cocoapods`)

### Clone & Bootstrap

```bash
git clone https://github.com/OpenFlutter/fluwx.git
cd fluwx

# Install workspace dependencies and link packages
dart pub get
melos bootstrap
```

> **Note:** The repo relies on symlinks (shared native source between `fluwx` and `fluwx_no_pay`). On macOS/Linux these are preserved by git automatically. On Windows, make sure git is configured with `core.symlinks=true`.

Verify all symlinks are intact after bootstrapping:

```bash
melos run symlinks:check
```

### Run the Example App

```bash
# fluwx (with Pay)
cd packages/fluwx/example
flutter pub get
flutter run

# fluwx_no_pay (without Pay)
cd packages/fluwx_no_pay/example
flutter pub get
flutter run
```

### iOS — CocoaPods vs SPM

The project supports both CocoaPods and Swift Package Manager. Set the mode globally before building:

```bash
# CocoaPods mode
flutter config --no-enable-swift-package-manager
cd packages/fluwx/example/ios && pod install

# SPM mode
flutter config --enable-swift-package-manager
```

### Analyze & Test All Packages

```bash
melos exec -- flutter analyze
melos exec -- flutter test
```

---