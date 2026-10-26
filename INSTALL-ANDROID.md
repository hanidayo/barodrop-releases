# BaroDrop Android app — build it yourself

**English** · [한국어](#바로드롭-안드로이드-앱--직접-빌드하기)

The Android app is not on Google Play. `BaroDrop-Android.zip` holds its Android Studio project: build it on your computer and install the APK on your phone. No developer account is needed.

What the app does: browse your computers (with thumbnails), preview files and save them to the phone (`Download/BaroDrop`), send photos and files to a computer (also from other apps' Share button), and let a computer open the phone (its BaroDrop folder and the internal storage).

## You need

- A Windows or Mac computer with **Android Studio** (free: https://developer.android.com/studio).
- An Android phone or tablet with **Android 10** or later.
- **BaroDrop on your NAS, version 1.5 or later** (see [INSTALL-NAS.md](INSTALL-NAS.md)), and the PC agent on your computers.

## Build

1. Install Android Studio and open it once (it downloads the Android SDK on the first start).
2. Unzip `BaroDrop-Android.zip`. In Android Studio: **File → Open** → choose the `android` folder.
3. Wait until the bottom bar says the Gradle sync finished (the first time takes a few minutes: it downloads the build tools).
4. **Build → Build App Bundle(s) / APK(s) → Build APK(s)**. When it finishes, click **locate**: the file is `app/build/outputs/apk/debug/app-debug.apk`.

## Install on the phone

- **Easiest:** copy `app-debug.apk` to the phone (USB cable, Google Drive, messenger …) and open it there. Allow "Install unknown apps" for the app you opened it with when asked.
- **Or** turn on USB debugging on the phone (Settings → About phone → tap "Build number" 7 times → Developer options → USB debugging), connect it, choose it at the top of Android Studio and press **▶ Run**.

To update later, build again **on the same computer** and install over the old app (the computer's debug key signs it; your settings stay). An APK built on another computer has a different key: uninstall the old app first (files in `Download/BaroDrop` stay).

## First use

1. Enter your BaroDrop address (the same address you open in the browser on your computers).
2. Allow **All files access** when asked (to save to `Download/BaroDrop` and to let your computers open the internal storage). You can do it later in the page's ⚙ → **Allow file access**.
3. **＋** (add computer) → on the computer: agent settings → **Make a pairing code** → enter the 8-character code on the phone → approve on the computer.
4. Tap **Connect** next to the computer.

## Good to know

- The authenticator (approving access from outside) is in the iPhone app only.
- Videos are downloaded first and then open in the phone's player (streaming while they arrive is iPhone-only for now).
- With Tailscale on the phone and the computer, they connect directly from anywhere.

---

## 바로드롭 안드로이드 앱 — 직접 빌드하기

[English](#barodrop-android-app--build-it-yourself) · **한국어**

안드로이드 앱은 Google Play에 없습니다. `BaroDrop-Android.zip`에 Android Studio 프로젝트가 들어 있으니, 컴퓨터에서 빌드해 나온 APK를 휴대폰에 설치하세요. 개발자 계정은 필요 없습니다.

앱으로 하는 일: 내 컴퓨터 탐색(썸네일), 미리보기·휴대폰에 받기(`Download/BaroDrop`), 사진·파일을 컴퓨터로 보내기(다른 앱의 공유 버튼으로도), 컴퓨터에서 휴대폰 열기(받은 파일 폴더·내장 저장공간).

## 준비물

- **Android Studio**가 설치된 Windows 또는 Mac 컴퓨터(무료: https://developer.android.com/studio)
- **Android 10** 이상 휴대폰이나 태블릿
- **내 NAS의 바로드롭 1.5 이상**([INSTALL-NAS.md](INSTALL-NAS.md))과 컴퓨터의 PC 에이전트

## 빌드

1. Android Studio를 설치하고 한 번 실행합니다(처음 실행 때 Android SDK를 내려받습니다).
2. `BaroDrop-Android.zip`을 풉니다. Android Studio에서 **File → Open** → `android` 폴더 선택
3. 아래 상태 줄에 Gradle sync가 끝났다고 나올 때까지 기다립니다(처음엔 빌드 도구를 내려받느라 몇 분 걸립니다).
4. **Build → Build App Bundle(s) / APK(s) → Build APK(s)**. 끝나면 **locate**를 누르면 `app/build/outputs/apk/debug/app-debug.apk` 파일이 보입니다.

## 휴대폰에 설치

- **가장 쉬운 방법:** `app-debug.apk`를 휴대폰으로 옮겨서(USB 케이블, 구글 드라이브, 메신저 등) 휴대폰에서 엽니다. "출처를 알 수 없는 앱 설치" 허용을 물으면 허용합니다.
- **또는** 휴대폰의 USB 디버깅을 켜고(설정 → 휴대전화 정보 → 소프트웨어 정보 → "빌드번호" 7번 누르기 → 개발자 옵션 → USB 디버깅) 케이블로 연결한 뒤, Android Studio 위쪽에서 휴대폰을 고르고 **▶ Run**

나중에 업데이트할 때는 **같은 컴퓨터에서** 다시 빌드해 덮어 설치합니다(그 컴퓨터의 디버그 키로 서명되어, 설정이 그대로 남습니다). 다른 컴퓨터에서 빌드한 APK는 키가 달라 덮어 설치가 안 되니, 먼저 기존 앱을 지우고 설치하세요(`Download/BaroDrop`의 파일은 남습니다).

## 처음 쓰기

1. 바로드롭 주소 입력(컴퓨터 브라우저로 여는 주소와 같음)
2. **모든 파일 접근** 허용(받은 파일을 `Download/BaroDrop`에 저장하고, 컴퓨터에서 내장 저장공간을 열기 위해). 나중에 화면의 ⚙ → **파일 접근 허용**에서도 됩니다.
3. **＋**(컴퓨터 추가) → 컴퓨터의 에이전트 설정 → **연결 코드 만들기** → 8자리 코드를 휴대폰에 입력 → 컴퓨터에서 승인
4. 컴퓨터 옆 **연결**

## 알아 두기

- 인증기(밖에서 접속 승인)는 아이폰 앱에만 있습니다.
- 영상은 다 받은 뒤 휴대폰 플레이어로 열립니다(받으면서 바로 재생은 지금은 아이폰만).
- 휴대폰과 컴퓨터에 Tailscale을 켜 두면 어디서든 직접 연결됩니다.

Made by Hanidayo · Built with Claude
