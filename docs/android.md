# Android Integration

## 1) Add Maven Central

```kotlin
repositories {
    mavenCentral()
}
```

## 2) Add SDK dependency

```kotlin
dependencies {
    implementation("com.testogethr:sdk:<version>")
}
```

Replace `<version>` with the latest stable SDK version.

## 3) Get SDK Access Token

Create your SDK token from the Testogethr app:

1. Open Testogethr app
2. Go to **Profile**
3. Open **API Key Manager**
4. Generate/copy your token

## 4) Initialize SDK

Initialize as early as possible (typically in `Application.onCreate`).

```kotlin
import android.app.Application
import android.util.Log
import com.testogethr.sdk.TestogethrConfig
import com.testogethr.sdk.TestogethrSdk

class MyApplication : Application() {
    override fun onCreate() {
        super.onCreate()

        TestogethrSdk.initialize(
            sdkAccessToken = "YOUR_SDK_ACCESS_TOKEN",
            config = TestogethrConfig(applicationContext),
            debugLogger = { level, tag, message, throwable ->
                Log.d("Testogethr", "[$level] $tag: $message", throwable)
            }
        )
    }
}
```

## 5) Register schema and track events

```kotlin
import com.testogethr.sdk.TestogethrSdk
import com.testogethr.shared.models.api.sdk.DeclaredEvent

val bossEvent = DeclaredEvent(
    name = "boss_defeated",
    description = "Fired when the final boss is defeated"
)

TestogethrSdk.get().registerSchema(
    isDiscoveryMode = true,
    events = listOf(bossEvent)
)

TestogethrSdk.get().trackEvent(event = bossEvent)
```

## 6) Start test session from deep link

Read the `sessionToken` query parameter and start the session.

```kotlin
private fun handleIntent(intent: Intent?) {
    val sessionToken = intent?.data?.getQueryParameter("sessionToken")
    if (sessionToken != null) {
        TestogethrSdk.get().startSession(sessionToken)
    }
}
```
