# Storytellers Dice

One web app (`www/index.html`) packaged two ways by GitHub Actions:

- **Windows**: Electron, producing an installer and a portable `.exe`
- **Android**: Capacitor, producing an installable `.apk`

## Build it (no software needed on your computer)

1. Create a free account at github.com and press **New repository** (any name, public or private). Do not tick "Add a README".
2. Unzip `storytellers-dice-app.zip` on your computer.
3. In your new repository press **uploading an existing file**, then drag in everything inside the unzipped folder (the `.github`, `www` and `electron` folders and the loose files). Press **Commit changes**.
   - If the `.github` folder did not upload (it can be hidden on Mac: press Cmd+Shift+. in Finder), press **Add file > Create new file**, type `.github/workflows/build.yml` as the name, paste in the contents of that file and commit.
4. Open the **Actions** tab. Choose **Build apps** on the left and press **Run workflow**. (Committing to `main` also starts it automatically. If GitHub asks you to enable workflows, accept.)
5. Wait 5 to 10 minutes until both jobs show a green tick.
6. Open the finished run and scroll to **Artifacts** at the bottom. Download:
   - `StorytellersDice-Android-APK` (a zip containing `app-debug.apk`)
   - `StorytellersDice-Windows` (a zip containing the installer and the portable exe)

## Install

**Windows:** unzip, then either run `StorytellersDice-Setup-1.0.0.exe` to install, or run `StorytellersDice-Portable-1.0.0.exe` with no install. The app is unsigned, so Windows SmartScreen may warn you: press **More info > Run anyway**.

**Android:** unzip the artifact, copy `app-debug.apk` to your phone (USB, cloud drive or email), open it and allow "Install unknown apps" for the app you opened it from. Play Protect may ask to scan it: that is normal for apps outside the Play Store.

## Updating the app later

Edit or replace `www/index.html` in your repository (Add file > Upload files, same name), commit, and the build runs again.

## Notes

- Saved seeds, maps and tokens live on each device (browser storage) and do not sync between Windows and Android.
- On Android, **Export** opens the share sheet so you can save the map image or send it to another app. The back button closes open pages before leaving the app.
- The Android build is a debug-signed APK, which installs fine for personal use. Publishing on Google Play would need a release-signed bundle.
- To use your own icon: Windows, add `build/icon.ico` (256x256) to the repo. Android, replace the icons under `android/app/src/main/res` after generating the project locally.
