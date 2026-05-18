# Upgrade to V6

V6 is a major release with a series of breaking changes, mainly for iOS. It adds support for `scene_delegate` and Swift Package Manager. Below are the key things to pay attention to when migrating to V6:

- You now need to configure Universal Links manually; the SDK no longer handles this automatically.
- You now need to configure the URL scheme manually; the SDK no longer handles this automatically.
- You now need to configure `LSApplicationQueriesSchemes` manually; the SDK no longer handles this automatically.
- The logging toggle is temporarily unavailable for now.

> [!WARNING]
> For no_pay version, you switch to `fluwx_no_pay` package, which is a separate package without payment features.

If you are not familiar with setting up Universal Links, URL schemes, and `LSApplicationQueriesSchemes`, please refer to the [official documentation](https://developers.weixin.qq.com/doc/oplatform/Mobile_App/Access_Guide/iOS.html).

**Any previous iOS configuration via `pubspec.yaml` is no longer effective.**

There are no changes on Android; continue using the previous approach to register the API and call interfaces.
