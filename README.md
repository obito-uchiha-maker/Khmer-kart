# KHMER KART V2 🇰🇭 — 3D Android Edition

An original Khmer-themed 3D kart-racing prototype. It uses Three.js for the 3D scene, Vite for the web build, Capacitor for Android packaging, and an optional Express leaderboard API. It does not include Mario characters, Nintendo branding, or copied Mario Kart assets.

## What's implemented in this V2 starter
- Real-time Three.js 3D scene with a loop track, roadside palms, a Khmer-inspired temple silhouette, Tuk-Tuk-style player vehicle, and three rival vehicles.
- Keyboard and mobile touch controls, acceleration/braking/steering, boost button, lap counter, timer, and local best time.
- Capacitor Android wrapper configuration (`com.khmerkart.game`).
- GitHub Actions cloud workflow to build a debug APK and attach it as an artifact.
- Separate Express API starter for health and in-memory leaderboard endpoints.

## Run in browser
Requires Node.js 20+ recommended (Node 18+ may work depending on dependencies).

```bash
npm ci
npm run dev
```

## Cloud-build APK using only a phone + GitHub
1. Create a GitHub repository and upload/push the contents of this project to the repository root. Include `package-lock.json`.
2. Open the repository's **Actions** tab. If prompted, enable Actions.
3. Choose **Build Android APK** and press **Run workflow**, or push a commit to `main`/`master`.
4. Wait for the workflow to finish. Open the successful run and download the `khmer-kart-v2-debug-apk` artifact.
5. Extract the artifact ZIP on Android and install `app-debug.apk`. Android may ask you to allow installation from that source.

The workflow produces a **debug/test APK**, not a Play Store release. A release APK/AAB requires signing credentials; keep signing keys and passwords in GitHub Actions secrets, never in source files.

## Local Android project (optional)
```bash
npm ci
npm run build
npx cap add android
npx cap sync android
cd android
./gradlew assembleDebug
```

## Backend API
The optional server is in `server/server.js`. Deploy it separately on a Node-compatible host. The current in-memory scores reset whenever the server restarts and are not a production persistent leaderboard. The game prototype currently stores best time locally on the device; API integration and persistent database are future work.

## Important limitations
- This is an early 3D prototype, not a full commercial 3D racing game. Vehicle physics, collision, item combat, track selection, sound, online multiplayer, and persistent online scores still need development.
- The APK workflow has been authored but must be run in GitHub Actions to produce a downloadable APK. No APK is claimed to exist until that cloud workflow succeeds.
- Google Fonts uses a network connection; Khmer text still falls back to system fonts if offline.
