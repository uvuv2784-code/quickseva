# QuickSeva Flutter starter

This is a runnable Flutter UI starter for the QuickSeva local-services marketplace.

## Included in this starter
- Home screen and service catalogue (12 categories including car washer)
- Customer booking flow: direct booking or quotation request
- Home-service or shop-visit selection
- Your Services booking list
- Worker registration form and worker/customer mode selector
- Amritsar sample professionals
- 5% worker-side commission policy documented in the profile screen

## Important limitations
This is NOT a production-ready marketplace and does not include a compiled APK.
Data is currently held in app memory and resets when the app restarts.
The following integrations still need implementation and configuration:
- Firebase Authentication / OTP, Firestore or a production API/database
- Real GPS permission, geocoding, Google Maps keys, distance/radius search
- Worker document upload, verification workflow and admin dashboard
- Push notifications and booking state transitions
- Razorpay payment gateway and server-side payment verification
- Secure server-side commission ledger and payouts
- Review moderation, abuse prevention, privacy policy and terms
- Production testing, signing key and Play Store release

## Run locally
Install Flutter SDK and Android Studio / Android SDK, then:
```bash
flutter pub get
flutter run
```

Build a debug APK after the integrations and testing:
```bash
flutter build apk --debug
```
For a release APK:
```bash
flutter build apk --release
```
The APK is normally written to `build/app/outputs/flutter-apk/app-release.apk`.

## Commission rule
QuickSeva platform fee = 5% of the final service amount, charged to the worker only after verified job completion. Do not expose the fee in customer-facing screens, invoices or quotations. Calculate and store the fee server-side, not in the client app. Cancelled or refunded jobs must not earn commission; refunds and disputes need an explicit ledger reversal policy.

## Suggested production architecture
Flutter Android/iOS clients + authenticated API + PostgreSQL + object storage + Firebase Cloud Messaging + Google Maps Platform + Razorpay.
Never put payment secrets or privileged database credentials inside the mobile app.

## Build a test APK with GitHub Actions
1. Create a GitHub repository and upload the contents of this folder.
2. Push the files to the `main` branch.
3. Open the repository's **Actions** tab.
4. Run **Build QuickSeva Android APK** (or wait for the push build).
5. Open the successful workflow run and download the `quickseva-debug-apk` artifact.
6. Extract the artifact and install `app-debug.apk` on an Android test phone. You may need to allow installation from your browser/file manager.

This creates a debug/testing APK, not a signed Play Store release.
