# C+Y Pulse – Android & iOS app

Native app shell (Capacitor) for the live C+Y Pulse site, `https://pulse.cydesignstudioph.com/`.
Your PHP/MySQL system stays on your host. The app opens it full-screen, with its own icon and splash
screen, location (time-in geofence) and camera/photo-upload permissions, and an offline screen.
Any change you upload to the website shows up in the app at once, with no app update needed.

If the site's address changes, edit `server.url` in `capacitor.config.json` and `www/index.html`.

## Android (easiest: no Android Studio)
1. Create a free GitHub repo and upload this folder's contents.
2. Go to **Actions → Build Android APK → Run workflow**.
3. Download `cy-pulse-debug-apk` from the finished run, unzip, and install `app-debug.apk` on any
   Android phone (allow "install unknown apps").

Local build instead: install Node 22, JDK 21 and Android Studio, then
`npm install && npm run add:android && npm run open:android` and press Run / Build APK.

## iOS (needs a Mac with Xcode 16+)
iOS apps can only be built on macOS.
1. `npm install && npm run add:ios && npm run open:ios`
2. In Xcode: App target → Signing & Capabilities → choose your Apple Developer team.
3. Plug in an iPhone and press Run, or use Product → Archive → Distribute (TestFlight / App Store).
Without a Mac you can use a cloud Mac service such as Codemagic or a GitHub `macos` runner.

## Publishing notes
- Google Play needs a signed release bundle (`./gradlew bundleRelease` plus your own keystore) and a $25 developer account.
- Apple needs a $99/year developer account. App Store review can reject apps that only wrap a website;
  for staff-only use, TestFlight or Apple Business/Custom Apps distribution is the safer route.
- Change the app id (`com.cydesignstudio.pulse`) in `capacitor.config.json` before the first build if you want another one.
- Icons come from `resources/icon.png` (1024px) and `resources/splash.png`; replace them and re-run `npm run assets`.
