<div align="center">

<img src="https://raw.githubusercontent.com/expo/expo/main/templates/expo-template-blank/assets/splash.png" width="120" alt="Expo Logo" />

# 🚀 React Native Expo
## Complete Guide — Account Creation to Deployment

<p align="center">
  <img src="https://img.shields.io/badge/Expo%20SDK-51+-000020?style=for-the-badge&logo=expo&logoColor=white" />
  <img src="https://img.shields.io/badge/React%20Native-0.74+-61DAFB?style=for-the-badge&logo=react&logoColor=black" />
  <img src="https://img.shields.io/badge/EAS%20CLI-12.x-4630EB?style=for-the-badge&logo=expo&logoColor=white" />
  <img src="https://img.shields.io/badge/Node.js-20%20LTS-339933?style=for-the-badge&logo=node.js&logoColor=white" />
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Android-Supported-3DDC84?style=for-the-badge&logo=android&logoColor=white" />
  <img src="https://img.shields.io/badge/iOS-Supported-000000?style=for-the-badge&logo=apple&logoColor=white" />
  <img src="https://img.shields.io/badge/TypeScript-Ready-3178C6?style=for-the-badge&logo=typescript&logoColor=white" />
</p>

> **The definitive step-by-step guide** for building and shipping React Native apps with Expo EAS — from zero to both app stores.

📖 [Official Expo Docs](https://docs.expo.dev) &nbsp;·&nbsp; 🏗️ [EAS Build](https://docs.expo.dev/eas/) &nbsp;·&nbsp; 💬 [Expo Forums](https://forums.expo.dev) &nbsp;·&nbsp; 🐛 [Expo GitHub](https://github.com/expo/expo)

</div>

---

## 📋 Table of Contents

- [01 · Prerequisites & System Requirements](#01--prerequisites--system-requirements)
- [02 · Create Your Expo Account](#02--create-your-expo-account)
- [03 · Install Node.js, Git & Expo CLI](#03--install-nodejs-git--expo-cli)
- [04 · Create a New Expo Project](#04--create-a-new-expo-project)
- [05 · Project Structure Deep Dive](#05--project-structure-deep-dive)
- [06 · Configure app.json / app.config.js](#06--configure-appjson--appconfigjs)
- [07 · Running the App Locally](#07--running-the-app-locally)
- [08 · Using Expo Go & Dev Builds](#08--using-expo-go--dev-builds)
- [09 · Install & Configure EAS CLI](#09--install--configure-eas-cli)
- [10 · EAS Build — Initial Setup](#10--eas-build--initial-setup)
- [11 · Android Build & Deployment](#11--android-build--deployment)
- [12 · iOS Build & Deployment](#12--ios-build--deployment)
- [13 · OTA Updates with EAS Update](#13--ota-updates-with-eas-update)
- [14 · Environment Variables & Secrets](#14--environment-variables--secrets)
- [15 · CI/CD with GitHub Actions](#15--cicd-with-github-actions)
- [16 · Troubleshooting Common Issues](#16--troubleshooting-common-issues)
- [17 · Quick Reference Cheatsheet](#17--quick-reference-cheatsheet)

---

## 01 · Prerequisites & System Requirements

> 🔗 **Official Reference:** https://docs.expo.dev/get-started/set-up-your-environment/

### 📦 Core Requirements

| Requirement | Min Version | Notes |
|---|---|---|
| **Node.js** | 18.x LTS or 20.x LTS | Avoid odd-numbered (unstable) versions |
| **npm** | 9.x+ | Bundled with Node — or use yarn 3.x / pnpm 8.x |
| **Git** | 2.x+ | Required for EAS build commits |
| **Expo CLI** | Latest | Run via `npx expo` (no global install needed) |
| **EAS CLI** | Latest | `npm install -g eas-cli` |

### 🍎 For iOS Builds

| Requirement | Details |
|---|---|
| **macOS** | 13 (Ventura) or newer |
| **Xcode** | 15+ via [Mac App Store](https://apps.apple.com/app/xcode/id497799835) |
| **Apple Developer Account** | $99/year — [enroll here](https://developer.apple.com/programs/) |
| **iOS Device or Simulator** | iOS 16+ |

> 💡 **No Mac? No problem.** EAS Build runs on Expo's cloud macOS machines. You can build iOS apps from Windows or Linux using EAS without owning a Mac.
> 🔗 https://docs.expo.dev/build/introduction/

### 🤖 For Android Builds

| Requirement | Details |
|---|---|
| **Android Studio** | For emulator — [download here](https://developer.android.com/studio) |
| **JDK** | 17 — bundled inside Android Studio |
| **Google Play Account** | $25 one-time — [register here](https://play.google.com/console/) |

---

## 02 · Create Your Expo Account

> 🔗 **Official Reference:** https://expo.dev/signup

### Step 2.1 — Register

1. Go to **https://expo.dev/signup**
2. Enter your **Full Name**, **Email**, and **Password** *(min 8 chars)*
3. Click **"Create Account"**
4. Verify your email via the link from **noreply@expo.dev**

### Step 2.2 — Explore the Dashboard

After login at **https://expo.dev**, you have access to:

| Section | Purpose |
|---|---|
| **Projects** | All your Expo apps |
| **Builds** | EAS Build history & downloadable artifacts |
| **Updates** | OTA update channels |
| **Submissions** | App store submission history |
| **Credentials** | Keystores, certificates, provisioning profiles |
| **Secrets** | Encrypted environment secrets for builds |

### Step 2.3 — Create an Organization *(Recommended for Teams)*

1. Dashboard → **Settings** → **Organizations** → **Create Organization**
2. Invite team members by email
3. Assign roles: Owner / Admin / Developer / Viewer

> 🔗 Account types: https://docs.expo.dev/accounts/account-types/

---

## 03 · Install Node.js, Git & Expo CLI

> 🔗 **Official Reference:** https://docs.expo.dev/get-started/installation/

### Step 3.1 — Install Node.js via nvm *(Recommended)*

```bash
# macOS / Linux — install nvm
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
source ~/.bashrc   # or ~/.zshrc on macOS

# Install Node 20 LTS
nvm install 20
nvm use 20
nvm alias default 20

# Verify
node --version    # → v20.x.x
npm --version     # → 10.x.x
```

<details>
<summary><b>Windows — using nvm-windows</b></summary>

```powershell
# Download installer from:
# https://github.com/coreybutler/nvm-windows/releases

nvm install 20.0.0
nvm use 20.0.0

node --version
```

</details>

<details>
<summary><b>Direct Download (Alternative)</b></summary>

Download the LTS installer from: https://nodejs.org/en/download

</details>

---

### Step 3.2 — Install Git

```bash
# macOS
brew install git

# Ubuntu / Debian
sudo apt update && sudo apt install git

# Windows
# Download from: https://git-scm.com/download/win

# Verify
git --version    # → git version 2.x.x
```

---

### Step 3.3 — Expo CLI

```bash
# ✅ Recommended — always uses latest via npx
npx expo --version

# Optional: global install
npm install -g @expo/cli
expo --version
```

> ⚠️ **Deprecation Note:** The old `expo-cli` global package is deprecated. Use `npx expo` or `@expo/cli`.
> 🔗 https://docs.expo.dev/more/expo-cli/

---

### Step 3.4 — EAS CLI *(Required for Builds)*

```bash
# Install globally
npm install -g eas-cli

# Verify
eas --version    # → 12.x.x or higher
```

> 🔗 EAS CLI reference: https://docs.expo.dev/eas/

---

## 04 · Create a New Expo Project

> 🔗 **Official Reference:** https://docs.expo.dev/get-started/create-a-project/

### Step 4.1 — Initialize Project

```bash
# ✅ Recommended — blank TypeScript starter
npx create-expo-app@latest MyAwesomeApp --template blank-typescript

# With Expo Router (file-based navigation — recommended for new projects)
npx create-expo-app@latest MyAwesomeApp --template tabs

# Choose template interactively
npx create-expo-app@latest MyAwesomeApp --template
```

### 📐 Available Official Templates

| Template Flag | Use Case | Includes |
|---|---|---|
| `blank` | Minimal JS starter | Basic App.js |
| `blank-typescript` | Minimal TS starter | TypeScript, tsconfig |
| `tabs` | Tab navigation | Expo Router, TypeScript, NativeWind |
| `bare-minimum` | Bare React Native | No Expo managed workflow |

> 🔗 All templates: https://docs.expo.dev/more/create-expo/

---

### Step 4.2 — Install Dependencies & Open

```bash
cd MyAwesomeApp
npm install

# Open in VS Code
code .
```

---

## 05 · Project Structure Deep Dive

> 🔗 **Official Reference:** https://docs.expo.dev/develop/project-structure/

```
MyAwesomeApp/
│
├── 📁 app/                        # Expo Router screens (file-based routing)
│   ├── 📁 (tabs)/
│   │   ├── index.tsx              # Home tab screen
│   │   └── explore.tsx            # Explore tab screen
│   ├── _layout.tsx                # Root layout (navigation wrapper)
│   └── +not-found.tsx             # 404 / not found page
│
├── 📁 assets/                     # Static assets (auto-optimized by Expo)
│   ├── 📁 fonts/                  # Custom font files (.ttf, .otf)
│   ├── 📁 images/                 # App images & icons
│   ├── icon.png                   # App icon (1024×1024)
│   ├── adaptive-icon.png          # Android adaptive icon (1024×1024)
│   └── splash-icon.png            # Splash screen image
│
├── 📁 components/                 # Reusable React Native components
│   ├── 📁 ui/                     # Base UI atoms (Button, Input, etc.)
│   └── ThemedText.tsx             # Theme-aware Text component
│
├── 📁 constants/                  # App-wide constants
│   └── Colors.ts                  # Light / dark theme colors
│
├── 📁 hooks/                      # Custom React hooks
│   ├── useColorScheme.ts
│   └── useThemeColor.ts
│
├── 📁 .expo/                      # Auto-generated cache ← git-ignore this
│
├── ⭐ app.json                    # App config (name, version, icons, permissions)
├── ⭐ eas.json                    # EAS Build profiles (dev/preview/production)
├── babel.config.js                # Babel presets — do not delete
├── expo-env.d.ts                  # TypeScript Expo environment types
├── package.json                   # npm dependencies
├── tsconfig.json                  # TypeScript config
└── .gitignore
```

### Key Files

| File | Purpose |
|---|---|
| `app.json` | App metadata — name, version, icons, permissions, bundle IDs |
| `eas.json` | Build profiles — which credentials, which distribution channel |
| `babel.config.js` | Required Babel config — do NOT modify unless you know what you're doing |
| `expo-env.d.ts` | TypeScript types for Expo environment variables |

---

## 06 · Configure app.json / app.config.js

> 🔗 **Schema reference:** https://docs.expo.dev/versions/latest/config/app/  
> 🔗 **Workflow config:** https://docs.expo.dev/workflow/configuration/

### Step 6.1 — Full app.json Example

```json
{
  "expo": {
    "name": "My Awesome App",
    "slug": "my-awesome-app",
    "version": "1.0.0",
    "orientation": "portrait",
    "icon": "./assets/images/icon.png",
    "scheme": "myapp",
    "userInterfaceStyle": "automatic",
    "newArchEnabled": true,

    "splash": {
      "image": "./assets/images/splash-icon.png",
      "resizeMode": "contain",
      "backgroundColor": "#ffffff"
    },

    "ios": {
      "supportsTablet": true,
      "bundleIdentifier": "com.yourcompany.myawesomeapp",
      "buildNumber": "1",
      "infoPlist": {
        "NSCameraUsageDescription": "Used to capture photos.",
        "NSLocationWhenInUseUsageDescription": "Used for nearby features."
      }
    },

    "android": {
      "adaptiveIcon": {
        "foregroundImage": "./assets/images/adaptive-icon.png",
        "backgroundColor": "#ffffff"
      },
      "package": "com.yourcompany.myawesomeapp",
      "versionCode": 1,
      "permissions": [
        "CAMERA",
        "ACCESS_FINE_LOCATION",
        "READ_EXTERNAL_STORAGE"
      ]
    },

    "web": {
      "bundler": "metro",
      "output": "static",
      "favicon": "./assets/images/favicon.png"
    },

    "plugins": [
      "expo-router",
      "expo-font",
      ["expo-camera", {
        "cameraPermission": "Allow $(PRODUCT_NAME) to access your camera."
      }]
    ],

    "experiments": {
      "typedRoutes": true
    },

    "extra": {
      "eas": {
        "projectId": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
      }
    }
  }
}
```

> ⚠️ **Critical:** `expo.extra.eas.projectId` must match your project UUID on https://expo.dev/projects

---

### Step 6.2 — Dynamic Config with app.config.js

Use when you need environment-based configuration:

```js
// app.config.js
export default ({ config }) => ({
  ...config,
  name: process.env.APP_ENV === "production"
    ? "MyApp"
    : "MyApp (Dev)",
  slug: "my-awesome-app",
  version: "1.0.0",
  extra: {
    apiUrl: process.env.API_URL,
    eas: {
      projectId: "your-project-uuid"
    }
  }
});
```

---

### Step 6.3 — Icon & Splash Screen Size Reference

| Asset | Size | Format | Notes |
|---|---|---|---|
| **App Icon** (`icon.png`) | 1024×1024 px | PNG | No transparency |
| **Adaptive Icon** (Android) | 1024×1024 px | PNG | Transparency OK |
| **Splash Screen** | 1284×2778 px | PNG | Expo handles device scaling |
| **Favicon** (web) | 32×32 px | PNG | |

> 🔗 Icon guide: https://docs.expo.dev/develop/user-interface/splash-screen-and-app-icon/

---

## 07 · Running the App Locally

> 🔗 **Official Reference:** https://docs.expo.dev/develop/development-builds/introduction/

### Step 7.1 — Start Dev Server

```bash
# Standard start
npx expo start

# Clear Metro cache (fixes most "weird" bugs)
npx expo start --clear

# Tunnel mode (different network / internet testing)
npx expo start --tunnel

# Target a specific platform
npx expo start --android
npx expo start --ios
npx expo start --web
```

---

### Step 7.2 — Metro Bundler Keyboard Shortcuts

| Key | Action |
|---|---|
| `a` | Open Android emulator |
| `i` | Open iOS Simulator |
| `w` | Open in web browser |
| `r` | Reload the app |
| `m` | Toggle menu |
| `j` | Open JS debugger |
| `?` | Show all options |

---

### Step 7.3 — Install Packages the Right Way

```bash
# ✅ Always use expo install for Expo packages
# (installs the version compatible with your SDK)
npx expo install expo-camera
npx expo install expo-router react-native-safe-area-context react-native-screens

# ❌ Avoid npm install for Expo packages
# (may install incompatible version)
npm install expo-camera
```

> 🔗 https://docs.expo.dev/workflow/expo-cli/#install

---

### Step 7.4 — Check for Issues

```bash
# Checks all packages for SDK compatibility
npx expo doctor
```

---

## 08 · Using Expo Go & Dev Builds

> 🔗 **Official Reference:** https://docs.expo.dev/get-started/expo-go/

### Option A — Expo Go *(Quickest Start)*

| Platform | Download |
|---|---|
| iOS | [App Store](https://apps.apple.com/app/expo-go/id982107779) |
| Android | [Google Play](https://play.google.com/store/apps/details?id=host.exp.exponent) |

**How to use:**
1. Run `npx expo start`
2. QR code appears in terminal
3. **iOS** → Camera app → tap link notification
4. **Android** → Open Expo Go → Scan QR Code

> ⚠️ **Limitation:** Expo Go does NOT support custom native modules. For apps with native code, use a Development Build.

---

### Option B — Development Build *(Custom Native Code)*

```bash
# 1. Install the dev client package
npx expo install expo-dev-client

# 2. Build for Android device
eas build --profile development --platform android

# 3. Build for iOS Simulator
eas build --profile development --platform ios

# 4. Build for iOS physical device
eas build --profile development-device --platform ios
```

> 🔗 https://docs.expo.dev/develop/development-builds/create-a-build/

---

## 09 · Install & Configure EAS CLI

> 🔗 **Official Reference:** https://docs.expo.dev/eas/

### Step 9.1 — Login to Expo

```bash
eas login
# → Email: your@email.com
# → Password: ••••••••

# Confirm login
eas whoami
```

---

### Step 9.2 — Link Project to expo.dev

```bash
# Run from your project root
eas init
```

This will:
1. Let you select or create a project on expo.dev
2. Add the `projectId` to your `app.json`
3. Configure EAS for your project

---

### Step 9.3 — Verify Configuration

Check `app.json` after `eas init`:

```json
{
  "expo": {
    "extra": {
      "eas": {
        "projectId": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
      }
    }
  }
}
```

> 🔗 Full setup guide: https://docs.expo.dev/build/setup/

---

## 10 · EAS Build — Initial Setup

> 🔗 **Official Reference:** https://docs.expo.dev/build/introduction/

### Step 10.1 — Generate eas.json

```bash
eas build:configure
```

---

### Step 10.2 — Complete eas.json Reference

```json
{
  "cli": {
    "version": ">= 12.0.0",
    "requireCommit": true
  },
  "build": {
    "development": {
      "developmentClient": true,
      "distribution": "internal",
      "ios": { "simulator": true }
    },
    "development-device": {
      "developmentClient": true,
      "distribution": "internal",
      "channel": "development"
    },
    "preview": {
      "distribution": "internal",
      "channel": "preview",
      "android": { "buildType": "apk" }
    },
    "production": {
      "autoIncrement": true,
      "channel": "production",
      "android": { "buildType": "app-bundle" },
      "ios": { "credentialsSource": "remote" }
    }
  },
  "submit": {
    "production": {
      "android": {
        "serviceAccountKeyPath": "./google-service-account.json",
        "track": "production"
      },
      "ios": {
        "appleId": "your@appleid.com",
        "ascAppId": "YOUR_APP_STORE_CONNECT_APP_ID",
        "appleTeamId": "YOUR_APPLE_TEAM_ID"
      }
    }
  }
}
```

### Build Profile Comparison

| Profile | Purpose | Android Output | iOS Output |
|---|---|---|---|
| `development` | iOS Simulator testing | N/A | `.app` (Simulator) |
| `development-device` | Real device dev testing | `.apk` | `.ipa` (Ad Hoc) |
| `preview` | QA / internal testing | `.apk` | `.ipa` (Ad Hoc) |
| `production` | Store submission | `.aab` | `.ipa` (App Store) |

> 🔗 eas.json reference: https://docs.expo.dev/build/eas-json/

---

## 11 · Android Build & Deployment

> 🔗 **Official Reference:** https://docs.expo.dev/build/android/

### Step 11.1 — Set Package Name

```json
{
  "expo": {
    "android": {
      "package": "com.yourcompany.appname",
      "versionCode": 1
    }
  }
}
```

> ⚠️ **The package name is permanent.** Once your app is published on the Play Store, it cannot be changed. Use `com.companyname.appname` format.

---

### Step 11.2 — Manage Android Keystore

**Option A — Let EAS manage it *(Recommended)***

```bash
eas credentials --platform android
# Follow prompts → "Set up a new keystore"
# EAS generates and securely stores it on Expo's servers
```

**Option B — Generate your own keystore**

```bash
keytool -genkeypair -v \
  -storetype PKCS12 \
  -keystore my-upload-key.keystore \
  -alias my-key-alias \
  -keyalg RSA \
  -keysize 2048 \
  -validity 10000

# Then upload to EAS
eas credentials --platform android
```

> 🔗 Android credentials: https://docs.expo.dev/app-signing/android-credentials/

---

### Step 11.3 — Build Commands

```bash
# Internal test build (APK — sideloadable)
eas build --platform android --profile preview

# Production build (AAB — for Play Store)
eas build --platform android --profile production

# Build both platforms simultaneously
eas build --platform all --profile production

# Monitor build queue
eas build:list
```

> 📊 Track builds at: https://expo.dev/builds

---

### Step 11.4 — Install APK on Device

```bash
# Via ADB (Android Debug Bridge)
adb install path/to/app.apk

# Or scan the QR code from your Expo dashboard build page
```

---

### Step 11.5 — Google Play Console Setup

1. Sign in at **https://play.google.com/console/**
2. **Create app** → fill in:
   - App name, default language, type (app/game), pricing
3. Complete **Store listing**:
   - Short description *(max 80 chars)*
   - Full description *(max 4000 chars)*
   - App icon: **512×512 px PNG**
   - Feature graphic: **1024×500 px**
   - Screenshots: **min 2 per device type**
4. Fill **Content rating**, **Target audience**, **Privacy policy URL**

---

### Step 11.6 — Google Service Account *(For Auto-Submit)*

> 🔗 https://docs.expo.dev/submit/android/

1. **Play Console** → Setup → API access → Link Google Cloud Project
2. **Google Cloud Console** → Create Service Account
3. Grant the account **Release Manager** role in Play Console
4. Download JSON key → save as `google-service-account.json`

```bash
# Add to .gitignore immediately!
echo "google-service-account.json" >> .gitignore
```

---

### Step 11.7 — Submit to Google Play

```bash
# Automated via EAS Submit
eas submit --platform android --profile production

# Submit a specific build by ID
eas submit --platform android --id BUILD_ID
```

**Manual submission:**
1. Download `.aab` from Expo dashboard
2. Play Console → **Production** → **Create new release**
3. Upload AAB → Add release notes → **Review** → **Rollout to Production**

---

## 12 · iOS Build & Deployment

> 🔗 **Official Reference:** https://docs.expo.dev/build/ios/

### Step 12.1 — Apple Developer Account

1. Visit **https://developer.apple.com/programs/**
2. Enroll in **Apple Developer Program** — $99/year
3. Complete identity verification *(24–48 hrs)*
4. Access portal at **https://developer.apple.com/account/**

---

### Step 12.2 — Set Bundle Identifier

```json
{
  "expo": {
    "ios": {
      "bundleIdentifier": "com.yourcompany.appname",
      "buildNumber": "1",
      "supportsTablet": true
    }
  }
}
```

> ⚠️ **Bundle identifier is permanent** once published on App Store. Use reverse domain notation.

---

### Step 12.3 — Manage iOS Credentials

```bash
# Let EAS handle all credentials — highly recommended
eas credentials --platform ios

# EAS will create and manage:
# ✓ Distribution Certificate
# ✓ Provisioning Profile (Ad Hoc / App Store)
# ✓ Push Notification Key
```

> 🔗 iOS credentials guide: https://docs.expo.dev/app-signing/ios-credentials/

---

### Step 12.4 — Register Test Devices

```bash
# Registers testers' device UDIDs for Ad Hoc builds
eas device:create

# Tester opens the generated URL on their iPhone
# Installs a profile → UDID is registered
```

> 🔗 https://docs.expo.dev/build/internal-distribution/

---

### Step 12.5 — iOS Build Commands

```bash
# Build for iOS Simulator (no Apple account needed)
eas build --platform ios --profile development

# Build for internal distribution / TestFlight
eas build --platform ios --profile preview

# Build for App Store submission
eas build --platform ios --profile production
```

> 🏗️ Expo uses macOS cloud machines — no Mac required on your end.

---

### Step 12.6 — App Store Connect Setup

1. Go to **https://appstoreconnect.apple.com/**
2. **My Apps** → **+** → **New App**
3. Fill in:
   - Platform: iOS
   - Name: Your App Name
   - Bundle ID: *(must match `app.json` exactly)*
   - SKU: unique internal ID (e.g., `MYAPP2024`)
4. Save

---

### Step 12.7 — App Store Connect API Key *(For Auto-Submit)*

> 🔗 https://docs.expo.dev/submit/ios/

1. App Store Connect → **Users and Access** → **Integrations** → **App Store Connect API**
2. **Generate API Key** → Role: **App Manager**
3. Download `.p8` key file *(download once — cannot re-download)*
4. Note your **Key ID** and **Issuer ID**

```bash
# Upload API key to EAS credentials
eas credentials --platform ios
# → Select "App Store Connect API Key"

# Add .p8 to .gitignore
echo "*.p8" >> .gitignore
```

---

### Step 12.8 — Submit to App Store

```bash
# Automated via EAS Submit
eas submit --platform ios --profile production

# What this does:
# → Uploads IPA to App Store Connect via Transporter API
# → Processing takes 10–30 minutes
# → Build appears in TestFlight automatically
```

**Manual via Transporter *(macOS only)*:**
1. Download **Transporter** from Mac App Store
2. Sign in with Apple ID
3. Drag `.ipa` file → Click **Deliver**

---

### Step 12.9 — TestFlight Testing

1. App Store Connect → **TestFlight** tab
2. **Internal Testers** — up to 100 *(must be in your team — no review needed)*
3. **External Testers** — up to 10,000 *(requires Beta App Review: ~24–48 hrs)*
4. Send invitations via email

---

### Step 12.10 — App Store Review Submission

Complete in App Store Connect:

| Section | Required |
|---|---|
| App description & keywords | ✅ |
| Screenshots for all device sizes | ✅ |
| Privacy Policy URL | ✅ |
| App Category & Age Rating | ✅ |
| Pricing | ✅ |
| Build selected from TestFlight | ✅ |
| Demo account *(if login required)* | ✅ |

Click **Submit for Review** → typically 1–3 business days.

> 🔗 App Review Guidelines: https://developer.apple.com/app-store/review/guidelines/

---

## 13 · OTA Updates with EAS Update

> 🔗 **Official Reference:** https://docs.expo.dev/eas-update/introduction/

Push JavaScript/asset changes to users **without app store review**.

### Step 13.1 — Install expo-updates

```bash
npx expo install expo-updates
```

---

### Step 13.2 — Configure in app.json

```json
{
  "expo": {
    "updates": {
      "url": "https://u.expo.dev/YOUR_PROJECT_ID",
      "fallbackToCacheTimeout": 0
    },
    "runtimeVersion": {
      "policy": "appVersion"
    }
  }
}
```

> 🔗 Runtime versions: https://docs.expo.dev/eas-update/runtime-versions/

---

### Step 13.3 — Publish OTA Update

```bash
# Push to production channel
eas update --channel production --message "Bug fix: login screen"

# Push to preview channel for QA
eas update --channel preview --message "Testing new feature"

# Platform-specific update
eas update --channel production --platform android --message "Android fix"
```

---

### Step 13.4 — Manage Updates

```bash
# List all updates
eas update:list

# Rollback to previous update
eas update:rollback --channel production
```

---

### When OTA Works vs When You Need a New Build

| Change Type | OTA Update ✅ | New Build Required 🏗️ |
|---|---|---|
| JavaScript / TypeScript logic | ✅ | — |
| Images / asset files | ✅ | — |
| Text, styles, UI | ✅ | — |
| New native module added | — | ✅ |
| app.json changes | — | ✅ |
| Expo SDK version upgrade | — | ✅ |
| New permission added | — | ✅ |

---

## 14 · Environment Variables & Secrets

> 🔗 **Official Reference:** https://docs.expo.dev/build-reference/variables/

### Step 14.1 — Client-Side Variables

```bash
# .env (committed for shared defaults)
EXPO_PUBLIC_API_URL=https://api.example.com
EXPO_PUBLIC_MAPS_KEY=your_maps_key_here

# .env.local (not committed — local overrides)
EXPO_PUBLIC_API_URL=https://dev.api.example.com
```

> ⚠️ **All client-accessible variables MUST be prefixed with `EXPO_PUBLIC_`**. Without this prefix, they are NOT bundled into the app.

```typescript
// Access anywhere in your app
const apiUrl = process.env.EXPO_PUBLIC_API_URL;
```

---

### Step 14.2 — Build Secrets *(Sensitive Values)*

```bash
# Add a secret to EAS (encrypted, never in your code)
eas secret:create --scope project --name SENTRY_AUTH_TOKEN --value "super-secret"

# List all secrets
eas secret:list

# Delete a secret
eas secret:delete SENTRY_AUTH_TOKEN
```

Reference in `eas.json`:
```json
{
  "build": {
    "production": {
      "env": {
        "SENTRY_AUTH_TOKEN": "$SENTRY_AUTH_TOKEN"
      }
    }
  }
}
```

> 🔗 https://docs.expo.dev/build-reference/variables/#using-secrets-in-environment-variables

---

### Step 14.3 — .gitignore Checklist

```gitignore
# Environment
.env
.env.local
.env.production

# Credentials — NEVER commit these
google-service-account.json
*.p8
*.keystore
*.jks

# Expo cache
.expo/
dist/
```

---

## 15 · CI/CD with GitHub Actions

> 🔗 **Official Reference:** https://docs.expo.dev/build/building-on-ci/

### Step 15.1 — Generate & Add Expo Token

```bash
# Generate CI token
eas account:token:create --name github-ci-token
```

1. GitHub repo → **Settings** → **Secrets and variables** → **Actions**
2. **New repository secret** → Name: `EXPO_TOKEN` → Value: *(paste token)*

---

### Step 15.2 — Production Build & Submit Workflow

```yaml
# .github/workflows/production.yml
name: 🚀 Production Build & Deploy

on:
  push:
    branches: [main]

jobs:
  build-and-submit:
    name: Build and Submit to Stores
    runs-on: ubuntu-latest

    steps:
      - name: 📦 Checkout repository
        uses: actions/checkout@v4

      - name: 🟢 Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: 20.x
          cache: npm

      - name: 📥 Install dependencies
        run: npm ci

      - name: 🔧 Setup Expo & EAS
        uses: expo/expo-github-action@v8
        with:
          eas-version: latest
          token: ${{ secrets.EXPO_TOKEN }}

      - name: 🏗️ Build (Android + iOS)
        run: eas build --platform all --profile production --non-interactive

      - name: 🚢 Submit to stores
        run: eas submit --platform all --profile production --non-interactive
```

---

### Step 15.3 — PR Preview Build Workflow

```yaml
# .github/workflows/preview.yml
name: 🔍 PR Preview Build

on:
  pull_request:
    types: [opened, synchronize]

jobs:
  preview:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20.x
          cache: npm
      - run: npm ci
      - uses: expo/expo-github-action@v8
        with:
          eas-version: latest
          token: ${{ secrets.EXPO_TOKEN }}

      - name: 🏗️ Preview build (Android)
        run: eas build --platform android --profile preview --non-interactive

      - name: 📡 Publish OTA preview update
        run: eas update --channel preview --message "PR #${{ github.event.number }} preview" --non-interactive
```

> 🔗 EAS + GitHub Actions: https://docs.expo.dev/eas-update/github-actions/

---

## 16 · Troubleshooting Common Issues

> 🔗 **Official Reference:** https://docs.expo.dev/debugging/errors/

<details>
<summary><b>🔴 Metro Bundler Won't Start</b></summary>

```bash
# Step 1 — Clear Metro cache
npx expo start --clear

# Step 2 — Nuclear reset
rm -rf node_modules .expo
npm install
npx expo start --clear
```
</details>

<details>
<summary><b>🔴 "Unable to resolve module" Error</b></summary>

```bash
# Clear Watchman (macOS / Linux)
watchman watch-del-all

# Reset Metro bundler cache
npx expo start --reset-cache
```
</details>

<details>
<summary><b>🔴 EAS Build Fails — Credential Issues</b></summary>

```bash
# Regenerate credentials
eas credentials --platform android
eas credentials --platform ios

# View credential status
eas credentials:list
```
</details>

<details>
<summary><b>🔴 iOS — "No Provisioning Profile Found"</b></summary>

```bash
# Sync from Apple Developer Portal
eas credentials --platform ios
# → Select: Update provisioning profile
```
</details>

<details>
<summary><b>🔴 Android — Keystore Lost</b></summary>

> ⚠️ **Critical:** If your upload keystore is lost and you used manual keystores, you cannot update an existing published app with the same package name. If EAS manages your keystore, it's safely stored on Expo's servers.

```bash
# Check if EAS has your keystore
eas credentials --platform android
```
</details>

<details>
<summary><b>🔴 App Store Rejection — Common Reasons & Fixes</b></summary>

| Rejection Reason | Fix |
|---|---|
| Missing privacy policy URL | Add URL to App Store Connect listing |
| Permissions not explained | Update `NSUsageDescription` in `app.json` |
| Crashes during review | Test on older iOS devices (iPhone SE / iOS 16) |
| Missing iPad screenshots | Add iPad screenshots if `supportsTablet: true` |
| Login required — no credentials | Add demo account in "Notes for Reviewer" |
| Metadata incomplete | Fill all required fields in App Store Connect |
</details>

<details>
<summary><b>🔴 OTA Update Not Appearing in App</b></summary>

```bash
# List recent updates and check channel
eas update:list

# Verify:
# 1. Channel in app.json matches channel in eas.json
# 2. Runtime version is compatible
# 3. User has internet connection when app launches
```
</details>

---

### 🛠️ Useful Diagnostic Commands

```bash
npx expo config            # Show computed app configuration
npx expo doctor            # Check SDK/package compatibility
eas build:list             # List all builds
eas build:view BUILD_ID    # View build logs
eas update:list            # List OTA updates by channel
eas whoami                 # Check authenticated user
```

---

## 17 · Quick Reference Cheatsheet

### 📌 All Commands in One Place

```bash
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
#  PROJECT SETUP
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
npx create-expo-app@latest MyApp --template blank-typescript
cd MyApp && npm install
eas login
eas init
eas build:configure

# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
#  DEVELOPMENT
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
npx expo start                     # Start dev server
npx expo start --clear             # Start fresh (clears cache)
npx expo install <package>         # Install Expo-compatible package
npx expo doctor                    # Diagnose SDK compatibility issues

# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
#  BUILDS
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
eas build -p android -e preview           # Android APK (internal testing)
eas build -p android -e production        # Android AAB (Play Store)
eas build -p ios -e development           # iOS Simulator
eas build -p ios -e preview              # iOS TestFlight (ad hoc)
eas build -p ios -e production           # iOS App Store build
eas build -p all -e production           # Build both platforms

# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
#  SUBMISSIONS
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
eas submit -p android                     # Submit to Google Play
eas submit -p ios                         # Submit to App Store
eas submit -p all                         # Submit to both stores

# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
#  OTA UPDATES
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
eas update --channel production --message "Fix login"
eas update --channel preview --message "QA build"
eas update:list
eas update:rollback --channel production

# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
#  CREDENTIALS
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
eas credentials                           # Manage all credentials
eas credentials --platform android        # Android keystore
eas credentials --platform ios           # iOS certs & profiles

# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
#  MONITORING
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
eas build:list                            # Recent builds
eas build:view BUILD_ID                   # Specific build logs
eas whoami                                # Current logged-in user
```

---

### 📊 Build Profile → Output Format

| Command | Profile | Output | Destination |
|---|---|---|---|
| `eas build -p android -e preview` | preview | `.apk` | Sideload / QA |
| `eas build -p android -e production` | production | `.aab` | Google Play |
| `eas build -p ios -e development` | development | `.app` | iOS Simulator |
| `eas build -p ios -e preview` | preview | `.ipa` (Ad Hoc) | TestFlight Internal |
| `eas build -p ios -e production` | production | `.ipa` (App Store) | App Store |

---

### 🏪 Store Submission Requirements

| Requirement | Android | iOS |
|---|---|---|
| **Account Cost** | $25 one-time | $99 / year |
| **Review Time** | 2–7 days | 1–3 days |
| **Build Format** | `.aab` | `.ipa` |
| **Icon Size** | 512×512 px | 1024×1024 px |
| **Feature Graphic** | 1024×500 px | N/A |
| **Screenshots** | Min 2 per device | 6.5" + 5.5" required |
| **Privacy Policy** | Required | Required |
| **Auto-Submit CLI** | `eas submit -p android` | `eas submit -p ios` |

---

### 🌐 Important Links

| Resource | URL |
|---|---|
| 🏠 Expo Dashboard | https://expo.dev |
| 📖 Expo Docs | https://docs.expo.dev |
| 🏗️ EAS Build Docs | https://docs.expo.dev/eas/ |
| 📋 app.json Schema | https://docs.expo.dev/versions/latest/config/app/ |
| ⚙️ eas.json Reference | https://docs.expo.dev/build/eas-json/ |
| 📡 EAS Update Docs | https://docs.expo.dev/eas-update/introduction/ |
| 🔑 iOS Credentials | https://docs.expo.dev/app-signing/ios-credentials/ |
| 🔑 Android Credentials | https://docs.expo.dev/app-signing/android-credentials/ |
| 🤖 Google Play Console | https://play.google.com/console/ |
| 🍎 App Store Connect | https://appstoreconnect.apple.com/ |
| 🍎 Apple Developer | https://developer.apple.com/account/ |
| 🧪 Expo Snack (online) | https://snack.expo.dev/ |
| 💬 Expo Forums | https://forums.expo.dev/ |
| 🐛 Expo GitHub | https://github.com/expo/expo |

---

## 🗺️ Complete End-to-End Flow

```
┌─────────────────────────────────────────────────────────────────┐
│                   FULL EXPO DEPLOYMENT WORKFLOW                 │
└─────────────────────────────────────────────────────────────────┘

 Step 01 ── Create account at expo.dev/signup
 Step 02 ── Install Node.js (nvm), Git, EAS CLI
 Step 03 ── npx create-expo-app@latest MyApp --template blank-typescript
 Step 04 ── Configure app.json (bundle ID, icons, permissions)
 Step 05 ── eas login → eas init  (links project to expo.dev)
 Step 06 ── eas build:configure   (creates eas.json)
 Step 07 ── npx expo start        (test with Expo Go or Dev Build)
 Step 08 ── eas build -p android -e preview  → install & test APK
 Step 09 ── eas build -p ios -e preview      → test via TestFlight
 Step 10 ── eas build -p all -e production   → production builds
 Step 11 ── eas submit -p android            → Google Play Store
 Step 12 ── eas submit -p ios               → App Store Connect
 Step 13 ── JS changes? eas update --channel production (no review!)
```

---

<div align="center">

**Built with ❤️ using Expo & EAS**

<img src="https://img.shields.io/badge/Expo-SDK%2051+-000020?style=flat-square&logo=expo&logoColor=white" />
<img src="https://img.shields.io/badge/EAS-Build%20%7C%20Submit%20%7C%20Update-4630EB?style=flat-square&logo=expo&logoColor=white" />
<img src="https://img.shields.io/badge/License-MIT-green?style=flat-square" />

*Always check [docs.expo.dev](https://docs.expo.dev) for the latest — the Expo ecosystem evolves fast.*

</div>
