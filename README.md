# Tamam (تمام) v2.0 — Site Engineer Field App (iOS & Android)

**Tamam (تمام)** is a Saudi-first construction field accounting app for **site engineers (`مهندس الموقع`)**: petty cash custody (`العهدة`), ZATCA receipt scanning with duplicate blocking, signed cash labor vouchers, and site video reports. It works offline and installs on iPhone and Android for $0.

**v2.0** is a full redesign of the field UI: clearer screens for outdoor use, a new **Me** tab with a large English / العربية switch, and automatic offline mode.

---

## 🌐 Live App & Install Links

- **Web app (GitHub Pages)**: [https://modysaggaf.github.io/tamam-demo-2/](https://modysaggaf.github.io/tamam-demo-2/)
- **Full-screen iOS mode**: [https://modysaggaf.github.io/tamam-demo-2/?ios=1](https://modysaggaf.github.io/tamam-demo-2/?ios=1)
- **iPhone profile (`Tamam.mobileconfig`)**: [Pages link](https://modysaggaf.github.io/tamam-demo-2/Tamam.mobileconfig) · [Release link](https://github.com/ModySaggaf/tamam-demo-2/releases/latest/download/Tamam.mobileconfig)
- **iPhone app (`Tamam-unsigned.ipa`)**: [Download](https://github.com/ModySaggaf/tamam-demo-2/releases/latest/download/Tamam-unsigned.ipa)
- **Android app (`Tamam.apk`)**: [Download](https://github.com/ModySaggaf/tamam-demo-2/releases/latest/download/Tamam.apk)

---

## 🍎 Install on iPhone

### Method A — Settings profile (recommended, no computer needed)
1. Open [https://modysaggaf.github.io/tamam-demo-2/](https://modysaggaf.github.io/tamam-demo-2/) in **Safari**, go to the **Me** tab → **Install Tamam**, and tap **Download Tamam.mobileconfig** (or open the profile link above directly).
2. Tap **Allow (السماح)** when Safari asks to download a configuration profile.
3. Open **Settings (الإعدادات)** → **Profile Downloaded (تم تنزيل ملف التعريف)**.
4. Tap **Install (تثبيت)**, enter your passcode, and confirm.
5. **Tamam** appears on your Home Screen and opens full-screen.

### Method B — Native `.ipa` via Sideloadly / AltStore
1. Download **`Tamam-unsigned.ipa`** from the link above.
2. Open **Sideloadly** or **AltStore** on a Mac or PC and sign in with a free Apple ID.
3. Drag the `.ipa` in and click **Start**.
4. On the iPhone: **Settings → General → VPN & Device Management → Developer App → Trust**.
   Free Apple ID signing expires after 7 days; re-sideload to renew.

---

## 🤖 Install on Android

1. On the phone, download **`Tamam.apk`** from the link above (or from **Me → Install Tamam** in the app).
2. Open the downloaded file.
3. Allow **Install from this source (تثبيت التطبيقات غير المعروفة)** and tap **Install**.

---

## ✨ What's in v2.0

1. **Home**: Online / Offline indicator, one-tap language button (ع / EN), project row, custody balance with *spent today* and *awaiting approval*, big shortcuts for Scan receipt, Pay a worker and Site video.
2. **Scan receipt**: camera + photo capture, automatic ZATCA QR reading (Tags 1–5), Saudi Tax ID check (`^3\d{13}3$`, VAT forced to 0.00 if invalid), stage and cash/card selection, refund (`رجيع`) switch, **SHA-256 + composite-key duplicate blocking** with a clear "No duplicate found" check, and `> 500 SAR` manager approval vs `≤ 500 SAR` auto-approval.
3. **Pay a worker**: worker search with pay rates, add a new worker, large keypad with live Arabic & English amount in words (تفقيط), finger signature, and a shareable `1200×900` PNG voucher (`CHA-2611-XXXX`).
4. **Site video**: record or upload a walk-through and get an AI site report (stage, progress, materials, safety). Optional Gemini API key.
5. **Activity**: search, filters (All, Pending, Receipts, Labor, Videos), entries grouped by day with daily totals, queued items shown while offline.
6. **Wallet (العهدة)**: quick top-up amounts (1,000 / 2,500 / 5,000 / Other), reason, pending request status, and a money in / out ledger.
7. **Me**: large **English / العربية** switch (full RTL), work offline, send saved items, install links, and an *Advanced & testing* section (testing tools for sample receipts and the QR decoder, Gemini key, reset demo data).
8. **Offline-first**: detects signal loss automatically, saves entries on the phone, and sends them when the signal returns. Service worker cache `tamam-field-v2`.

---

## 🛠 Build

The GitHub Actions workflow (`.github/workflows/build-mobile.yml`) runs on every push to `main` and publishes release **v2.0.0** with `Tamam.apk`, `Tamam-unsigned.ipa`, `Tamam.mobileconfig` and `manifest.plist`.

Local build (Node 20+, JDK 17 and Android SDK for Android; macOS + Xcode for iOS):

```bash
npm install
npm run sync:www && npx cap sync
cd android && ./gradlew assembleDebug
```
