# Tamam (تمام) — Standalone Site Engineer Field Accounting App (iOS & Android)

**Tamam (تمام)** is a Saudi-first construction field accounting mobile application built for **Site Engineers (`مهندس الموقع`)**. It runs as an offline-first progressive mobile web application, an installable iOS WebClip Configuration Profile (`Tamam.mobileconfig`), and native Capacitor 6 iOS (`Tamam-unsigned.ipa`) & Android (`Tamam.apk`) packages.

---

## 🌐 Live App & Direct $0 Installation Links

- **Live Mobile App (GitHub Pages)**: [https://modysaggaf.github.io/tamam-demo-2/](https://modysaggaf.github.io/tamam-demo-2/)
- **Full-Screen iOS Mode**: [https://modysaggaf.github.io/tamam-demo-2/?ios=1](https://modysaggaf.github.io/tamam-demo-2/?ios=1)
- **iOS Settings Configuration Profile (`Tamam.mobileconfig`)**:
  - Direct Pages Link: [https://modysaggaf.github.io/tamam-demo-2/Tamam.mobileconfig](https://modysaggaf.github.io/tamam-demo-2/Tamam.mobileconfig)
  - GitHub Release Link: [https://github.com/ModySaggaf/tamam-demo-2/releases/latest/download/Tamam.mobileconfig](https://github.com/ModySaggaf/tamam-demo-2/releases/latest/download/Tamam.mobileconfig)
- **iOS Native Unsigned Package (`Tamam-unsigned.ipa`)**: [https://github.com/ModySaggaf/tamam-demo-2/releases/latest/download/Tamam-unsigned.ipa](https://github.com/ModySaggaf/tamam-demo-2/releases/latest/download/Tamam-unsigned.ipa)
- **Android Native Package (`Tamam.apk`)**: [https://github.com/ModySaggaf/tamam-demo-2/releases/latest/download/Tamam.apk](https://github.com/ModySaggaf/tamam-demo-2/releases/latest/download/Tamam.apk)

---

## 🍎 Step 1: How to Install on iPhone (iOS) for $0

### Method A — iOS Settings Configuration Profile (`Tamam.mobileconfig`) *(Recommended — No Computer Needed)*
1. Open **[https://modysaggaf.github.io/tamam-demo-2/](https://modysaggaf.github.io/tamam-demo-2/)** in **Safari** on your iPhone and tap **📲 Install on iPhone (iOS) & Android → Download Tamam.mobileconfig** (or open `https://modysaggaf.github.io/tamam-demo-2/Tamam.mobileconfig` directly).
2. Safari will prompt: *"This website is trying to download a configuration profile. Do you want to allow this?"* → Tap **Allow (السماح)**.
3. Open the **iPhone Settings (الإعدادات)** app → tap **Profile Downloaded (تم تنزيل ملف التعريف)** near the top.
4. Tap **Install (تثبيت)** in the top-right corner, enter your iPhone passcode, and confirm **Install** on the *"Unverified Profile / Unknown Source"* prompt.
5. **Tamam (تمام)** is now installed on your iPhone Home Screen and launches **100% full-screen** (`FullScreen: true`) without any Safari browser bars!

### Method B — Native Capacitor iOS `.ipa` via Sideloadly / AltStore
1. Download **`Tamam-unsigned.ipa`** from [GitHub Releases](https://github.com/ModySaggaf/tamam-demo-2/releases/latest/download/Tamam-unsigned.ipa).
2. Open **Sideloadly** or **AltStore** on macOS/Windows and sign in with any free personal Apple ID (`$0`).
3. Drag `Tamam-unsigned.ipa` into Sideloadly and click **Start**.
4. On your iPhone, navigate to **Settings → General → VPN & Device Management → Developer App → Trust** to verify and launch the native iOS binary.

---

## 🤖 Step 2: How to Install on Android (`.apk`) for $0

1. On your Android phone, download **`Tamam.apk`** from [GitHub Releases](https://github.com/ModySaggaf/tamam-demo-2/releases/latest/download/Tamam.apk) (or tap **Download Android APK** inside the app's Installer sheet).
2. Tap **Open** on the downloaded `Tamam.apk` file.
3. When prompted by Android, enable **Allow from this source (تثبيت التطبيقات غير المعروفة)** and tap **Install**.

---

## ✨ Core Features (Site Engineer Edition)

1. **Standalone Mobile Shell**: Full-screen `100vw × 100dvh` layout on mobile devices with native iOS notch & home-indicator safe areas (`env(safe-area-inset-top)` / `env(safe-area-inset-bottom)`), and a centered single-phone frame on desktop screens.
2. **4 Tabs (`Home`, `Activity`, `Wallet / العهدة`, `Me`) + `+` Action Sheet**:
   - **Activity**: Filter chips (`All`, `Receipts`, `Labor`, `Videos`) and tap-to-inspect detail sheet (displaying ZATCA TLV tags, SHA-256 digest, composite key, or Tafqeet).
   - **Wallet (`العهدة`)**: Live custody balance, inflow/outflow/refund ledger, and custom Top-Up Request (`[data-a="topupReq"]`).
3. **Flow 1 — Real Receipt Scanner (`Scan receipt`)**:
   - Rear camera live stream (`getUserMedia`) + `<input type="file" accept="image/*" capture="environment">` + 4 ZATCA sample presets.
   - UTF-8 safe **Saudi ZATCA QR TLV Base64 Decoder** (Tags 1–5: Seller, 15-digit Tax Number `3...3`, Timestamp, Invoice Total, 15% VAT).
   - **SHA-256 + Composite Key Duplicate Shield** persisted in `localStorage`, blocking duplicate receipts with `#dup-shield-alert`.
   - **Live VAT Enforcement Rule**: Validates Tax ID against `/^3\d{13}3$/`; automatically forces VAT to `0.00 SAR` if invalid or missing.
   - Editable Merchant, Tax #, Total, Stage chips (`Excavation`, `Foundation`, `Finishing`, `General`), Payment Method (`Cash`, `Card`), **Refund Toggle (`فاتورة رجيع`)**, and automatic `> 500 SAR` manager approval vs `≤ 500 SAR` auto-approval routing.
4. **Flow 2 — Real Cash Labor Voucher Studio (`Pay a worker`)**:
   - Pick an existing worker or add a **Custom Worker** (Name, Trade, Work Description).
   - 7-digit keypad (`0` to `9,999,999` SAR) with **live Arabic & English Tafqeet** on both the keypad screen and issued voucher.
   - **Finger Signature Canvas** (`#sig`) with stroke validation.
   - Generates a high-resolution **`1200×900` PNG Official Voucher** (`CHA-2611-XXXX`) with 1-tap PNG download and native `navigator.share`, deducting from the engineer's cash wallet.
5. **Flow 3 — Real Site Video Recorder (`Site video`)**:
   - Live camera video capture (`MediaRecorder`) + file upload + simulated site walk-through with live timer (`#vt`), generating a structured **AI Site Report** (Detected Stage, Progress %, Materials seen, Safety/PPE check) and saving to Activity.
6. **Settings (`Me` Tab) & Offline Persistence**:
   - Instant **English (LTR) ↔ العربية (RTL)** toggle (`document.documentElement.dir`).
   - Full `localStorage` persistence (`tamam_engineer_state_v1`) + **Offline Queue Mode** + **Reset Demo Data**.
   - Optional **Gemini API Key** field and in-app **iOS & Android Installer Sheet**.
