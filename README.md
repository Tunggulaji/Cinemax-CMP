![Cinemax](docs/images/cinemax-splash.svg)

# Cinemax

Cinemax is a Movies & TV Shows application for Android and iOS, built with Compose Multiplatform.

<a href='https://play.google.com/store/apps/details?id=com.maximillianleonov.cinemax&pcampaignid=pcampaignidMKT-Other-global-all-co-prtnr-py-PartBadge-Mar2515-1'><img alt='Get it on Google Play' src='https://play.google.com/intl/en_us/badges/static/images/badges/en_badge_web_generic.png' height='80' /></a>
[<img src="https://gitlab.com/IzzyOnDroid/repo/-/raw/master/assets/IzzyOnDroid.png"
     alt="Get it on IzzyOnDroid"
     height="80">](https://apt.izzysoft.de/fdroid/index/apk/com.maximillianleonov.cinemax)

or get the apk from the [Releases section](https://github.com/MaximillianLeonov/Cinemax/releases/latest).

# Preview

<img src="docs/images/screenshot-1-home.png" width="50%"><img src="docs/images/screenshot-2-home.png" width="50%">
<img src="docs/images/screenshot-3-list.png" width="50%"><img src="docs/images/screenshot-4-details.png" width="50%">
<img src="docs/images/screenshot-5-search.png" width="50%"><img src="docs/images/screenshot-6-search.png" width="50%">
<img src="docs/images/screenshot-7-wishlist.png" width="50%"><img src="docs/images/screenshot-8-settings.png" width="50%">

# Getting Started

- Generate an API key from [The Movie Database](https://www.themoviedb.org/).
- Put the key in the `local.properties` file.

```properties
cinemax.apikey=YOUR_API_KEY_HERE
```

# Development Environment

**Cinemax** uses the Gradle build system and can be imported directly into the latest stable version
of Android Studio (available [here](https://developer.android.com/studio)) or Fleet. For iOS development,
Xcode is required.

## Android

The Android app can be built and run using the default configuration in Android Studio.

```bash
./gradlew :composeApp:assembleDebug
```

## iOS

The iOS app requires Xcode and can be run from the `iosApp` directory.

1. Open `iosApp/iosApp.xcodeproj` in Xcode
2. Select a simulator or device
3. Build and run

Alternatively, build the iOS framework from command line:

```bash
./gradlew :composeApp:linkDebugFrameworkIosSimulatorArm64
```

# Build

The app contains the usual `debug` and `release` build variants.

For normal development use the `debug` variant. For UI performance testing use the `release`
variant.

# Architecture

The **Cinemax** app follows Clean Architecture principles with the following layers:

- **Presentation**: Compose UI with MVVM pattern using ViewModels
- **Domain**: Use cases and repository interfaces
- **Data**: Repository implementations, data sources, and mappers

![Architecture diagram](docs/images/architecture-1-overall.png)

# Tech Stack

| Category | Library |
|----------|---------|
| UI Framework | [Compose Multiplatform](https://www.jetbrains.com/lp/compose-multiplatform/) |
| Architecture | MVVM with Clean Architecture |
| Dependency Injection | [Koin](https://insert-koin.io/) |
| Networking | [Ktor](https://ktor.io/) |
| Database | [Room](https://developer.android.com/training/data-storage/room) (KMP) |
| Image Loading | [Coil](https://coil-kt.github.io/coil/) |
| Navigation | [Compose Navigation](https://www.jetbrains.com/help/kotlin-multiplatform-dev/compose-navigation-routing.html) |
| Preferences | [DataStore](https://developer.android.com/topic/libraries/architecture/datastore) |
| Serialization | [Kotlinx Serialization](https://github.com/Kotlin/kotlinx.serialization) |
| Async | [Kotlin Coroutines](https://kotlinlang.org/docs/coroutines-overview.html) |

# Project Structure

```
Cinemax/
├── composeApp/                    # Shared Kotlin Multiplatform module
│   ├── src/
│   │   ├── commonMain/           # Shared code for all platforms
│   │   │   ├── kotlin/com/cinemax/
│   │   │   │   ├── core/         # Core modules (data, domain, ui, network, database)
│   │   │   │   ├── feature/      # Feature modules (home, search, details, etc.)
│   │   │   │   └── di/           # Dependency injection setup
│   │   │   └── composeResources/ # Shared resources (drawables, fonts, strings)
│   │   ├── androidMain/          # Android-specific implementations
│   │   └── iosMain/              # iOS-specific implementations
│   └── build.gradle.kts
├── iosApp/                        # iOS application target
│   ├── iosApp/                   # Swift source files
│   └── iosApp.xcodeproj/         # Xcode project
├── build.gradle.kts              # Root build configuration
└── settings.gradle.kts           # Project settings
```

# UI

UI components are designed according to the custom design system and built entirely
using [Compose Multiplatform](https://www.jetbrains.com/lp/compose-multiplatform/).

The app has one dark theme that uses predefined colors.

![UI Layer Architecture](docs/images/architecture-2-ui-layer.png)

# Credits

- Design on [Figma](https://www.figma.com/community/file/1088719884686291024).

# License

```
Copyright 2022 Afig Aliyev

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
