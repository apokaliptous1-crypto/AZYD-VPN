# AZYD VPN — Android source project

Starter Android app written in Kotlin + Jetpack Compose. Minimum Android 10 (API 29).

## Included
- Arabic UI and a global location picker (20 example locations).
- WireGuard tunnel integration using the embeddable Android tunnel library.
- Import a WireGuard `.conf` file for the selected location.
- Connect/disconnect controls and a per-session list of imported configurations.
- Branded AZYD shield/crown logo in the app header and Android launcher icon.
- AdMob banner configured with the owner-provided AZYD VPN banner unit ID.
- GitHub Actions workflow to build a debug APK automatically.

## Important: server infrastructure is not included
The country picker is a catalog only. A location becomes usable only after importing a valid WireGuard configuration issued by a VPN provider or generated on a server you own. No public server credentials, private keys, or imaginary endpoints are included. Free public VPN endpoints can be unstable and may log or inspect traffic; use only providers you trust.

This starter currently keeps imported Config objects in memory; they must be re-imported after the app process is restarted. The favorite markers are also session-only. Add encrypted persistent storage before production release.

## Build locally
1. Install Android Studio, JDK 17, and Android SDK Platform 36.
2. Open this folder in Android Studio and allow Gradle Sync.
3. Select Build > Build APK(s).
4. Debug APK output: `app/build/outputs/apk/debug/app-debug.apk`.

## Build on GitHub
Push the repository to GitHub. The workflow `.github/workflows/android.yml` builds a debug APK on each push and lets you download it from the Actions run artifacts.

## AdMob
The project uses Google's test banner ad unit while developing. After your app is registered and approved/configured in AdMob, replace the test unit ID in `MainActivity.kt` with your banner unit:
`ca-app-pub-5459256280686692/7850100582`
The AdMob App ID in the manifest is the one supplied by the app owner:
`ca-app-pub-5459256280686692~6163990531`
Before public release, verify the app is registered in AdMob, configure consent (UMP) where required, and follow Google's privacy and ad policies. For development, use Google test ads or disable live ad requests until the app is approved.

## Before publishing
- Add a privacy policy and complete Google Play Data safety disclosures.
- Provide a support contact and accurate app description.
- Test connection, DNS handling, IPv4/IPv6 leak behavior, reconnect behavior, and battery usage on real devices.
- Implement secure encrypted storage for server configurations and favorites.
- Ensure you own or are authorized to use every VPN server.
- Create a signed release AAB with a protected upload key. Never commit keys or private WireGuard configurations to GitHub.

## Technical references
- WireGuard Android tunnel library: https://www.wireguard.com/embedding/
- AdMob banner guidance: https://developers.google.com/admob/android/banner/


## Current completion status
- The Android source project and GitHub Actions debug-APK workflow are included.
- The repository URL supplied by the owner currently contains only `README.md`; upload this project folder to that repository to trigger the build.
- This package is source code, not a tested APK. A build on GitHub Actions or Android Studio is still required.
- No VPN server fleet or free global WireGuard credentials are included. The 20 country entries are selectable labels only; each needs a real, authorized WireGuard `.conf` file. Do not advertise a country as connected until its tunnel is configured and verified.
- Imported WireGuard configurations and favorites currently remain in memory for the app session; persistent encrypted storage is still required before production release.
- Add a privacy policy, test on physical Android devices, and create a signed release AAB before publishing.
