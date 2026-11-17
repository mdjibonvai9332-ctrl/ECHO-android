# ECHO Android — Flutter Starter

## What is included
- ECHO-branded Flutter Android app starter
- Phone number login and OTP verification screens
- JWT token storage using SharedPreferences
- Home navigation: Chats, Calls, Contacts, Groups, Profile
- Profile loading from the ECHO backend
- Conversation list and message history/send API integration
- Responsive Material 3 UI

## Requirements
- Flutter stable SDK (Dart 3.3+)
- Android Studio / Android SDK
- Node.js backend from `ECHO_backend_and_demo.zip`

## Run on Android emulator
1. Install Flutter and Android Studio on a computer.
2. Extract this ZIP.
3. In this folder run:
   `flutter pub get`
4. Start your ECHO backend on the computer at port 4000.
5. Run:
   `flutter run --dart-define=ECHO_API_URL=http://10.0.2.2:4000`

`10.0.2.2` is the Android emulator's special route to the host computer.
For a physical Android phone, use your computer's LAN IP on the same Wi-Fi
(e.g. `http://192.168.x.x:4000`) or a deployed HTTPS API URL.

## Build APK
`flutter build apk --release --dart-define=ECHO_API_URL=https://YOUR_API_DOMAIN`

Output:
`build/app/outputs/flutter-apk/app-release.apk`

## Important limitations
This is an initial Android source-code build, not a compiled/installable APK.
It needs Flutter/Android SDK to compile. Backend API must be running and reachable.
For production, use HTTPS, configure a real SMS OTP provider, secure secrets,
and complete privacy/security testing.

Calls, video calls, push notifications, contact sync, file uploads, groups,
end-to-end encryption, and admin tools are not implemented in this Android build yet.
The current backend also needs further hardening and production database migration
before public use. Do not distribute to real users as a finished messenger.
