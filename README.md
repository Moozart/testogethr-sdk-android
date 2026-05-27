# Testogethr Android SDK Showcase

[![GitHub stars](https://img.shields.io/github/stars/Moozart/testogethr-sdk-android?style=social)](https://github.com/Moozart/testogethr-sdk-android/stargazers)
[![Latest release](https://img.shields.io/github/v/release/Moozart/testogethr-sdk-android?display_name=tag&sort=semver)](https://github.com/Moozart/testogethr-sdk-android/releases/latest)

Public Android SDK showcase repository for Testogethr integration, releases, and issue tracking.

## Scope

- Android SDK integration guidance
- Public release/tag visibility
- Issue intake for integrators

This repository does **not** contain Testogethr SDK source code.
SDK source code remains private.

## Android Dependency

```kotlin
dependencies {
    implementation("com.testogethr:sdk:<version>")
}
```

Replace `<version>` with the latest stable release tag.

## SDK Access Token (Required)

Create your SDK token from the **Testogethr mobile app**:

1. Open Testogethr app
2. Go to **Profile**
3. Open **API Key Manager**
4. Generate/copy SDK access token

## Quick Links

- Android integration guide: [docs/android.md](docs/android.md)
- iOS integration guide: [docs/ios.md](docs/ios.md)
- Changelog: [CHANGELOG.md](CHANGELOG.md)
- iOS SwiftPM repo: <https://github.com/Moozart/testogethr-sdk-ios-spm>

## Releases and Tags

- Tags follow semantic versioning: `vMAJOR.MINOR.PATCH`
- Each public SDK release should have:
  - Git tag
  - GitHub Release notes
  - Updated integration notes (if API changed)

## Support and Issues

- Bug reports: use the Bug Report issue template
- Feature requests: use the Feature Request issue template
- Security reports: see [`.github/SUPPORT.md`](.github/SUPPORT.md)
