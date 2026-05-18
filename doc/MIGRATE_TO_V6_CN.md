# 升级到V6

V6版本是一个重大版本，包含了一系列的破坏性更新，主要针对的是iOS，一是支持了scene_delegate，二是支持Swift Package Manager。以下是升级到V6的一些重要步骤注意事项：

- Universal link 需要自己手动配置，不再由SDK自动处理了。
- URL scheme 需要自己手动配置，不再由SDK自动处理了。
- LSApplicationQueriesSchemes 需要自己手动配置，不再由SDK自动处理了
- logging的开关暂时不可用，等我想想解决方案

> [!WARNING]
> 对于不需要支付功能的版本，你可以切换到`fluwx_no_pay`包，这是一个独立的包，没有支付功能。

如果不会设置Universal link，URL scheme，LSApplicationQueriesSchemes，请参考[官方文档](https://developers.weixin.qq.com/doc/oplatform/Mobile_App/Access_Guide/iOS.html)。

**过往iOS中通过`pubspec.yaml`中的配置都不再生效了！！！！！**

Android方面没有什么变化，继续使用之前的方式注册API和调用接口即可。

