# 바로드롭 안드로이드 앱

**한국어** · [English](#barodrop-android-app)

안드로이드 앱은 Google Play에 없습니다. [최신 릴리스](https://github.com/hanidayo/barodrop-releases/releases/latest)에서 **`BaroDrop-Android.apk`**를 받아 휴대폰에 설치하세요. 계정은 필요 없습니다.

앱으로 하는 일: 컴퓨터처럼 두 칸(휴대폰 · 컴퓨터, 파일을 길게 눌러 다른 칸으로 끌어 놓으면 복사), 내 컴퓨터 탐색(썸네일), 미리보기·휴대폰에 받기(`Download/BaroDrop`), 사진·파일을 컴퓨터로 보내기(다른 앱의 공유 버튼으로도), 컴퓨터에서 휴대폰 열기(받은 파일 폴더·내장 저장공간).

## 준비물

- **Android 10** 이상 휴대폰이나 태블릿
- **내 NAS의 바로드롭 1.7 이상**([INSTALL-NAS.md](INSTALL-NAS.md))과 컴퓨터의 PC 에이전트

## 설치

1. 휴대폰에서 [최신 릴리스](https://github.com/hanidayo/barodrop-releases/releases/latest)를 열고 **BaroDrop-Android.apk**를 누릅니다(컴퓨터에서 받아 휴대폰으로 옮겨도 됩니다).
2. 받은 파일을 엽니다. "출처를 알 수 없는 앱 설치" 허용을 물으면 허용하고 **설치**를 누릅니다.
3. Google Play 프로텍트가 "알 수 없는 개발자"라고 하면 **세부정보 더보기 → 무시하고 설치**(Google Play에 없는 앱이라 나옵니다).

업데이트: 새 `BaroDrop-Android.apk`를 받아 그대로 덮어 설치합니다. 모든 릴리스가 같은 키로 서명되어 설정이 그대로 남습니다.

## 처음 쓰기

1. 바로드롭 주소 입력(컴퓨터 브라우저로 여는 주소와 같음)
2. **모든 파일 접근** 허용(받은 파일을 `Download/BaroDrop`에 저장하고, 컴퓨터에서 내장 저장공간을 열기 위해). 나중에 화면의 ⚙ → **파일 접근 허용**에서도 됩니다.
3. **＋**(컴퓨터 추가) → 컴퓨터의 에이전트 설정 → **연결 코드 만들기** → 8자리 코드를 휴대폰에 입력 → 컴퓨터에서 승인
4. 컴퓨터 옆 **연결**

## 알아 두기

- 인증기(밖에서 접속 승인)는 아이폰 앱에만 있습니다.
- 영상은 다 받은 뒤 휴대폰 플레이어로 열립니다(받으면서 바로 재생은 지금은 아이폰만).
- 휴대폰과 컴퓨터에 Tailscale을 켜 두면 어디서든 직접 연결됩니다. 직접 연결이 막히면 NAS 중계로 연결됩니다.
- 직접 빌드(선택): `BaroDrop-Android.zip`에 Android Studio 프로젝트가 있습니다. `android` 폴더를 Android Studio로 열고 **Build → Build APK(s)**. 직접 빌드한 APK는 그 컴퓨터의 키로 서명되므로, 받은 앱을 지운 뒤 설치하세요.

---

## BaroDrop Android app

[한국어](#바로드롭-안드로이드-앱) · **English**

The Android app is not on Google Play. Download **`BaroDrop-Android.apk`** from the [latest release](https://github.com/hanidayo/barodrop-releases/releases/latest) and install it on your phone. No account is needed.

What the app does: two panes like on a computer (the phone and the computer; long-press a file and drag it to the other pane to copy it), browse your computers (with thumbnails), preview files and save them to the phone (`Download/BaroDrop`), send photos and files to a computer (also from other apps' Share button), and let a computer open the phone (its BaroDrop folder and the internal storage).

## You need

- An Android phone or tablet with **Android 10** or later.
- **BaroDrop on your NAS, version 1.7 or later** (see [INSTALL-NAS.md](INSTALL-NAS.md)), and the PC agent on your computers.

## Install

1. On the phone, open the [latest release](https://github.com/hanidayo/barodrop-releases/releases/latest) and tap **BaroDrop-Android.apk** (or download it on a computer and copy it to the phone).
2. Open the downloaded file. When asked, allow your browser / file app to **install unknown apps**, then tap **Install**.
3. If Google Play Protect warns about an unknown developer, tap **More details → Install anyway** (the app is not on Google Play).

Updates: install the newer `BaroDrop-Android.apk` over the old one. All releases are signed with the same key, so your settings stay.

## First use

1. Enter your BaroDrop address (the same address you open in the browser on your computers).
2. Allow **All files access** when asked (to save to `Download/BaroDrop` and to let your computers open the internal storage). You can do it later in the page's ⚙ → **Allow file access**.
3. **＋** (add computer) → on the computer: agent settings → **Make a pairing code** → enter the 8-character code on the phone → approve on the computer.
4. Tap **Connect** next to the computer.

## Good to know

- The authenticator (approving access from outside) is in the iPhone app only.
- Videos are downloaded first and then open in the phone's player (streaming while they arrive is iPhone-only for now).
- With Tailscale on the phone and the computer, they connect directly from anywhere. When a direct connection is blocked, BaroDrop uses your NAS relay.
- Build it yourself (optional): `BaroDrop-Android.zip` holds the Android Studio project. Open its `android` folder in Android Studio and use **Build → Build APK(s)**. An APK you build is signed with your computer's key, so uninstall the downloaded app before installing it.

Made by Hanidayo · Built with Claude
