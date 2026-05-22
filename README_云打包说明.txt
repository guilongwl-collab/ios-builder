AI伴侣 iOS 完整 Xcode 工程包

项目类型：原生 iOS WKWebView 壳
App 名称：AI伴侣
打开地址：https://kuangjia2.wenanku.cc/
Bundle ID：cc.wenanku.kuangjia2.aicompanion
最低系统：iOS 14.0

目录说明：
- AiCompanion.xcodeproj：完整 Xcode 工程
- AiCompanion/：Swift 源码、Info.plist、图标资源、启动页
- codemagic.yaml：Codemagic 云构建参考配置
- ExportOptions.plist：Xcode 导出 IPA 参考配置

本包用途：
1. Mac + Xcode 打开 AiCompanion.xcodeproj 后可编译。
2. 云 Mac / Codemagic / Bitrise / Appcircle 可上传本工程后编译。
3. 编译成功后生成 .app 或 .ipa，再用全能签/爱思助手签名安装。

注意：
- iosgodsipa、Diawi、爱思助手不能直接编译源码，只能处理已生成的 .ipa 或 Payload/*.app。
- 生成真正 IPA 仍然需要 Xcode 编译环境，或者云 Mac / 云 CI。
- 如需正式签名，需要上传 p12 证书和 mobileprovision 描述文件。

Codemagic 基本流程：
1. 把本工程上传到 GitHub 私有仓库。
2. Codemagic 新建 App，选择该仓库。
3. 选择 workflow：ios-webview-debug。
4. 如果只是验证编译，可先使用 CODE_SIGNING_ALLOWED=NO。
5. 如果要导出可安装 IPA，需要在 Codemagic 后台配置 Apple 证书、描述文件和签名步骤。

Xcode 本地流程：
1. Mac 安装 Xcode。
2. 双击 AiCompanion.xcodeproj。
3. 修改 Bundle Identifier 或 Team。
4. Product -> Archive。
5. Distribute App -> Development/Ad Hoc -> Export IPA。
