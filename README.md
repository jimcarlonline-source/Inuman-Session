# Inuman Session

A pixel-art Filipino inuman game. Make your own character, join the barkada (Tito Ven, Tita Thea, Ate Nini, Ate Bonsai and Bantay), and survive 10 nights without passing out or killing the vibe. Ate Pearl and Ate Analeh drop by on special nights.

The game is one HTML file in `www/`. Capacitor wraps it as an Android app, and GitHub Actions builds the APK, so you don't need Android Studio.

## Get the APK

1. Create a new repository on GitHub (public or private).
2. Upload everything in this folder, including the hidden `.github` folder. The easiest way is from a terminal:
   ```
   git init
   git add .
   git commit -m "Inuman Session"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/inuman-session.git
   git push -u origin main
   ```
   If you upload with the GitHub website instead, make sure `.github/workflows/build-apk.yml` is included. Some file pickers hide folders that start with a dot.
3. Open the **Actions** tab. The "Build Android APK" run starts on its own and takes about 5 to 8 minutes.
4. When it shows a green check, open the run and download **InumanSession-APK** under Artifacts. It's a zip with the `.apk` inside.
5. Copy the APK to your Android phone and open it. Allow "Install unknown apps" for your file manager or browser when Android asks.

You can also start a build anytime from **Actions > Build Android APK > Run workflow**.

## Make a release with a download link

Push a version tag and the APK gets attached to a GitHub Release that anyone with access can download:

```
git tag v1.0.0
git push origin v1.0.0
```

## Change the game

Edit `www/index.html`, commit and push. A new APK builds automatically. The version number goes up by one each build (1.0.1, 1.0.2, ...), so phones install it as an update.

The app icon and splash screen come from the images in `assets/`. Replace them with your own (same file names and sizes) to change them.

## Good to know

- The APK is a **debug build**. It installs and plays normally, and it's fine for sharing with friends and testers. The Google Play Store needs a signed release build (AAB) instead. Set that up when you're ready to publish.
- The app works offline. The fonts are bundled in `www/fonts` (SIL Open Font License, see the license files there).
- Progress and your character are saved on the phone. Uninstalling the app clears them.
- App ID: `com.ven.inumansession`. Change it in `capacitor.config.json` before your first public release if you want a different one. It can't change after you publish to the Play Store.

## Build on your own computer (optional)

Needs Node 20, Java 17 and Android Studio.

```
npm install
npx cap add android
npm run android:icons
npx cap sync android
npx cap open android
```

Then press Run in Android Studio.
