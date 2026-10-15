# My Work Diary — Native Android Application (Kotlin & Jetpack Compose)

This is the production-ready native Android project for **My Work Diary** (`com.myworkdiary.app`), crafted with modern Kotlin, Jetpack Compose, Material Design 3, and Room SQLite for 100% offline data retention.

---

## 📱 Features Included
- **Daily Work Notebook**: Classic lined paper notebook with unlimited job lines, auto-totals, worker wages, and daily notes.
- **💰 Client / Owner Payments Received**:
  - Independent system tracking money received from site clients.
  - Separate ledger from Labour Payments.
  - Multiple payment methods: Bank Transfer, Easypaisa, JazzCash, Cash, Other.
  - Reference / Transaction IDs & Payment screenshot attachments.
  - Duplicate payment protection & automated warning.
- **Project Financial Summary**:
  - Total Contract / Amount Due.
  - Total Money Received From Client.
  - Total Labour Cost & Total Labour Paid.
  - Total Material Cost & Other Expenses.
  - Remaining Client Balance & Net Project Profit.
- **Labour Records & Profiles**: Worker skills, daily wages, phone numbers, and complete individual transaction ledgers with advance payments tracking.
- **Expense & Payment Ledger**: Categorized records (Labour, Material, Other Expense) with cash/bank filtering.
- **Photos & Receipts**: Camera capture & gallery attachment for site jobs and payment proofs.
- **Search & Calendar**: Instant offline lookup across dates, workers, site names, and notes.
- **Monthly Summary**: High-level financial reporting and profit calculations.
- **100% Offline Storage**: Powered by Room SQLite. No login or external server required. Each device's data is stored strictly locally.
- **Backup & Restore**: Portable JSON export and import.

---

## 🛠️ Requirements
- **Android Studio**: Android Studio Koala / Ladybug or newer.
- **JDK**: Java 17 (recommended standard for Android SDK 35 & Gradle 8).
- **Target SDK**: Android 15 (API level 35) — compliant with Google Play target SDK requirements.
- **Minimum SDK**: Android 7.0 (API level 24).

---

## 🚀 How to Build & Test

### Option 1: Using Android Studio (Recommended UI)
1. Open Android Studio.
2. Select **Open an existing project** and choose the `android` folder.
3. Allow Gradle to sync.
4. Connect your Android phone via USB (with **USB Debugging** enabled in Developer Options) or start an Android Emulator.
5. Click the green **Run (▶)** button.

### Option 2: Using the Command Line
From the `android` directory:

```bash
# Build Debug APK for testing on your phone:
./gradlew assembleDebug

# Build Release APK:
./gradlew assembleRelease

# Build Google Play Android App Bundle (.aab):
./gradlew bundleRelease
```

The output files will be created at:
- **Debug APK**: `android/app/build/outputs/apk/debug/app-debug.apk`
- **Release APK**: `android/app/build/outputs/apk/release/app-release.apk`
- **Play Store Bundle (.aab)**: `android/app/build/outputs/bundle/release/app-release.aab`

---

## 📲 How to Install the APK Directly on Your Android Phone
1. Transfer `app-debug.apk` (or `app-release.apk`) to your phone via USB cable, Google Drive, WhatsApp, or email.
2. On your phone, tap the APK file in your file manager / downloads.
3. If prompted with *"Install unknown apps"*, toggle **Allow from this source**.
4. Tap **Install** and then tap **Open**.
5. Your diary is now running natively on your phone without internet or login requirements!

---

## 🔐 Creating Your Production Signing Key
To upload to the Google Play Store, the app must be signed.

Generate your release keystore using `keytool` (included with Java/Android Studio):

```bash
keytool -genkey -v -keystore release-keystore.jks -alias myworkdiary -keyalg RSA -keysize 2048 -validity 10000
```

Keep your `release-keystore.jks` and passwords safe in a secure backup. Place `release-keystore.jks` in `android/app/` or supply your credentials via `gradle.properties`:

```properties
MYWORKDIARY_RELEASE_STORE_FILE=release-keystore.jks
MYWORKDIARY_RELEASE_STORE_PASSWORD=your_keystore_password
MYWORKDIARY_RELEASE_KEY_ALIAS=myworkdiary
MYWORKDIARY_RELEASE_KEY_PASSWORD=your_key_password
```

---

## 📦 How to Upload to Google Play Console
1. Log in to [Google Play Console](https://play.google.com/console).
2. Click **Create app**:
   - App name: **My Work Diary**
   - Default language: English
   - App or game: App
   - Free or paid: Free
3. In the left menu under **Release**, select **Production** (or **Testing > Internal testing** first).
4. Click **Create new release**.
5. Drag and drop `app-release.aab` from `android/app/build/outputs/bundle/release/`.
6. Add your release notes (e.g., *"Initial release of My Work Diary: Offline contractor & plumbing notebook with client payments & labour ledger"*).
7. Complete the standard Google Play Store listing:
   - App icon (512x512)
   - Feature graphic (1024x500)
   - Screenshots of the app
   - Privacy policy link
   - Content rating questionnaire & Data safety declaration (No data collected, offline storage).
8. Click **Review release** and then **Start rollout to Production**!
