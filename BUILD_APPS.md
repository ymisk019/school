# Building DARK SCHOOL as apps

Everything runs on GitHub Actions: `.github/workflows/build-apps.yml`.

## Release
1. Push the project to GitHub (branch `main`).
2. Tag a version and push it:  `git tag v1.0.0 && git push origin v1.0.0`
   (or Actions tab -> "Build apps" -> Run workflow).
3. After ~15-25 min: Releases tab -> draft "Dark School v1.0.0" holds
   Windows (.exe/.msi), macOS (.dmg), Linux (.deb/.AppImage/.rpm) and Android (.apk).
   Publish the draft to share a download link.

To change the version, edit `version` in `src-tauri/tauri.conf.json` and `src-tauri/Cargo.toml`.

## iPhone (needs a paid Apple Developer account, $99/yr)
Add these repository secrets (Settings -> Secrets and variables -> Actions):
- `APPLE_DEVELOPMENT_TEAM`   your 10-character Team ID
- `IOS_CERTIFICATE`          base64 of your Apple Distribution .p12
- `IOS_CERTIFICATE_PASSWORD` the .p12 password
- `IOS_MOBILE_PROVISION`     base64 of an App Store provisioning profile for `com.houssamdev.darkschool`
Then run the workflow manually with "build_ios" ticked. Upload the .ipa with Apple's Transporter to TestFlight.

No Apple account? The GitHub Pages site already works on iPhone:
Safari -> Share -> Add to Home Screen.

## Local dev
    npm install
    npx @tauri-apps/cli@2 dev
