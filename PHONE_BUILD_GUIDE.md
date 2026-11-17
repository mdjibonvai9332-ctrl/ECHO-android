# ECHO Android — Phone-only Cloud Build Pack

This package is designed so the project can be built on GitHub Actions from an Android phone browser. It does NOT include a precompiled APK.

## A. Upload the source from your Android phone
1. Download and extract `ECHO_Android_Phone_Build.zip` using your phone's Files app.
2. Open https://github.com and sign in or create an account.
3. Create a new repository named `echo-android`.
4. For the easiest no-cost cloud build, set repository visibility to **Public**. GitHub says standard hosted Actions runners are free for public repositories. This makes source code visible to everyone, so do not upload secrets, private user data, production keys, or credentials.
5. Open the new repository, choose **Add file → Upload files**.
6. Upload the CONTENTS of this extracted folder, including the hidden `.github` folder and its workflow file. If the mobile browser does not show hidden folders, enable “show hidden files” in the file manager or use GitHub's web editor to create `.github/workflows/build-android.yml` and paste the workflow from this package.
7. Commit the files to the `main` branch.

## B. Run the cloud APK build
1. In the repository, open the **Actions** tab.
2. If prompted, enable GitHub Actions for the repository.
3. Select **Build ECHO Android APK** in the left workflow list.
4. Tap **Run workflow**.
5. Enter your deployed ECHO API HTTPS URL. Example format: `https://your-service-name.onrender.com`. If the API is not deployed yet, the APK can still be built with a placeholder URL, but login/chat will not connect until a real API is deployed.
6. Tap **Run workflow** and wait for the run to finish with a green check.
7. Open the successful workflow run, scroll to **Artifacts**, and download `ECHO-Android-APK`.
8. Extract the artifact ZIP, tap `app-release.apk`, allow “Install unknown apps” for the browser/files app if Android asks, then install.

## C. Free backend hosting — test only
The existing backend starter currently uses SQLite on local disk. Do NOT deploy it as-is to Render Free for real user data: Render free web services have ephemeral filesystems, so SQLite data can disappear on restart/redeploy/spin-down. Render free services also spin down after 15 minutes idle. Free Render Postgres expires after 30 days. See https://render.com/docs/free.
Before deploying for real users, migrate the backend to a persistent managed database and verify its backup/retention terms. Supabase currently offers a free tier for prototyping, but free projects can pause after inactivity and have quotas; see https://supabase.com/pricing.
The API must be deployed over HTTPS. Configure a real SMS OTP provider and secrets in the host dashboard. Never expose JWT_SECRET, OTP_SECRET, SMS credentials, or API admin keys in Flutter source, GitHub files, or APK.

## D. Important production gaps
This Flutter starter is an early client. Real calls/video, push notifications, contact sync, file sharing, group management, end-to-end encryption, account recovery/deletion, abuse reporting, and admin tools still need implementation and security review. It is not ready for public users or sensitive conversations.

## E. Flutter build reference
Official Flutter Android release guide: https://docs.flutter.dev/deployment/android
