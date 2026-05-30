# TTN-Mapper.org Webapp (Android)

This project is an Android WebView application that loads **https://ttn-mapper.org** directly inside a native Android app.  
It provides a simple, installable wrapper for the TTN Mapper website, including support for JavaScript, DOM storage, and geolocation.

---

## Features

- Loads **https://ttn-mapper.org** inside a fullscreen WebView  
- Supports:
  - JavaScript
  - DOM Storage
  - Geolocation (GPS)
- Minimal and fast native wrapper
- Compatible with GitHub Actions (automatic APK builds)
- Works on all Android devices (Android 5.0+)

---

## Project Structure


TTN-Mapper-Webapp/
│
├── .github/
│   └── workflows/
│       └── android.yml              # GitHub Actions Build Workflow
│
├── app/
│   ├── build.gradle                 # Modul-spezifische Gradle-Konfiguration
│   │
│   └── src/
│       ├── main/
│       │   ├── AndroidManifest.xml  # App-Manifest (Permissions, Activity)
│       │   │
│       │   ├── java/
│       │   │   └── com/
│       │   │       └── example/
│       │   │           └── ttnmapperwebapp/
│       │   │               └── MainActivity.kt   # WebView-Code
│       │   │
│       │   └── res/
│       │       ├── mipmap-hdpi/     # App-Icons
│       │       ├── mipmap-mdpi/
│       │       ├── mipmap-xhdpi/
│       │       ├── mipmap-xxhdpi/
│       │       ├── mipmap-xxxhdpi/
│       │       └── values/
│       │           └── strings.xml  # App-Name (optional)
│       │
│       └── test/                    # Unit Tests (optional)
│
├── build.gradle                     # Projektweite Gradle-Konfiguration
├── settings.gradle                  # Modul-Definition
├── gradlew                          # Gradle Wrapper
├── gradlew.bat                      # Gradle Wrapper (Windows)
└── gradle/
    └── wrapper/
        ├── gradle-wrapper.jar
        └── gradle-wrapper.properties

        ---

## MainActivity

The app uses a simple WebView to load TTN Mapper:

```kotlin
val webView = WebView(this)
val settings = webView.settings

settings.javaScriptEnabled = true
settings.domStorageEnabled = true
settings.databaseEnabled = true
settings.setGeolocationEnabled(true)

webView.webViewClient = WebViewClient()
webView.webChromeClient = WebChromeClient()

webView.loadUrl("https://ttn-mapper.org")
setContentView(webView)
