# iOS Integration

## 1) Add package in Xcode

Use Swift Package URL:

`https://github.com/Moozart/testogethr-sdk-ios-spm`

Select `Up to Next Major` and choose your target SDK version.

## 2) Import and initialize

```swift
import TestogethrSdk

TestogethrSdkCompanion.shared.initialize(
    sdkAccessToken: "YOUR_SDK_ACCESS_TOKEN",
    config: TestogethrConfig(),
    debugLogger: { level, tag, message, throwable in
        if let throwable {
            print("[\(level)] \(tag): \(message) \(throwable)")
        } else {
            print("[\(level)] \(tag): \(message)")
        }
    }
)
```

## 3) Register schema and track events

```swift
let bossEvent = SharedDeclaredEvent(
    name: "boss_defeated",
    description: "Fired when the final boss is defeated"
)

TestogethrSdkCompanion.shared.get().registerSchema(
    isDiscoveryMode: true,
    events: [bossEvent]
)

TestogethrSdkCompanion.shared.get().trackEvent(
    event: bossEvent,
    metadata: nil
)
```

## 4) Handle session deep links

Parse `sessionToken` from incoming URL and call `startSession`.

```swift
if let components = URLComponents(url: url, resolvingAgainstBaseURL: false),
   let token = components.queryItems?.first(where: { $0.name == "sessionToken" })?.value,
   !token.isEmpty {
    TestogethrSdkCompanion.shared.get().startSession(sessionToken: token)
}
```
