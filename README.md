# BaroDrop

**English** · [한국어](#바로드롭-한국어)

BaroDrop lets you open the folders of your other computers and copy files and folders between them, straight from one disk to another, like using a two-pane file explorer.

- Windows and Mac (Apple silicon) app with a two-pane explorer, list or large icons with picture thumbnails
- Your own Synology NAS is the meeting point. Files go directly between computers when possible, or through your NAS relay. **Files are never stored on the NAS or anywhere else.**
- Pair your own computers once, then connect with one click (and open the other one back from the bar that appears)
- iPhone app: browse your computers, preview photos, videos and documents, save files to the iPhone, send photos and files to a computer, and open the iPhone (its BaroDrop folder and photos) from a computer (it also approves access from outside)
- Android app: the same, except the authenticator and video streaming, with two panes like a computer (long-press a file and drag it across to copy)
- Automatic, signed updates from this page
- Korean and English (🌐 button at the top)

This repository holds the **release files** (the programs and update information). The NAS part and the iPhone app come as files you install or build yourself.

## Download

Get the latest version from **[Releases](https://github.com/hanidayo/barodrop-releases/releases/latest)**:

| Computer | File |
|---|---|
| Windows 10 / 11 (64-bit) | [BaroDropAgent-Windows.exe](https://github.com/hanidayo/barodrop-releases/releases/latest/download/BaroDropAgent-Windows.exe) |
| Mac (Apple silicon: M1/M2/M3/M4) | [BaroDropAgent-Mac.zip](https://github.com/hanidayo/barodrop-releases/releases/latest/download/BaroDropAgent-Mac.zip) |
| NAS (Synology, Container Manager) | [BaroDrop-NAS.zip](https://github.com/hanidayo/barodrop-releases/releases/latest/download/BaroDrop-NAS.zip) — setup: [INSTALL-NAS.md](INSTALL-NAS.md) |
| iPhone (iOS 16+, build it yourself with Xcode) | [BaroDrop-iOS.zip](https://github.com/hanidayo/barodrop-releases/releases/latest/download/BaroDrop-iOS.zip) — how: [INSTALL-IOS.md](INSTALL-IOS.md) |
| Android (10+) | [BaroDrop-Android.apk](https://github.com/hanidayo/barodrop-releases/releases/latest/download/BaroDrop-Android.apk) — how: [INSTALL-ANDROID.md](INSTALL-ANDROID.md) |

`latest.json` is the signed update information the app reads. You don't need to download it.

## Your NAS (once)

BaroDrop runs on your own NAS. Download `BaroDrop-NAS.zip`, follow [INSTALL-NAS.md](INSTALL-NAS.md) (also inside the zip): upload the files, copy `nas.env.example` to `.env` and set **three lines** (your address, a secret, the NAS's home address), then build it in Container Manager and set the reverse proxy and router ports. Nothing else to edit.

## Install

**Windows**
1. Run `BaroDropAgent-Windows.exe`. If Windows SmartScreen appears, choose **More info → Run anyway** (the app is not signed with a paid certificate).
2. In the window, press **Install on this computer**. BaroDrop is added to the Start menu and the desktop.
3. Microsoft Edge WebView2 is needed for the app window (built into Windows 11 and up-to-date Windows 10).

**Mac**
1. Unzip `BaroDropAgent-Mac.zip` and open **BaroDrop Agent**.
2. If macOS says it cannot verify the developer: **System Settings → Privacy & Security → Open Anyway** (or right-click the app → Open).
3. If there is no **Open Anyway**, or macOS says the app **"is damaged and can't be opened"**, open **Terminal** (Applications → Utilities) and run this once:
   ```
   xattr -dr com.apple.quarantine ~/Downloads/"BaroDrop Agent.app"
   ```
   If the app is already in Applications: `xattr -dr com.apple.quarantine "/Applications/BaroDrop Agent.app"`.
   (Or type `xattr -dr com.apple.quarantine ` with a space at the end, drag the app onto the Terminal window, and press Return.)
   This removes the "downloaded from the internet" mark that macOS puts on apps without a paid Apple certificate.
4. In the window, press **Install on this computer** to move it into Applications.

**First setup**
1. On the first start the agent asks for your BaroDrop address (the same address you open in the browser).
2. Choose which drives to share, and whether others may write to them.
3. Pair your computers: **Make a pairing code** on one, enter it on the other.

**iPhone / Android**
The Android app is not on Google Play: download `BaroDrop-Android.apk` and open it on the phone ([INSTALL-ANDROID.md](INSTALL-ANDROID.md)).
The iPhone app is not on the App Store: build it on a Mac with Xcode and a free or paid Apple ID, following [INSTALL-IOS.md](INSTALL-IOS.md). The authenticator (push approvals) needs a paid Apple developer account and your own push key.

## Updates

The app checks this page about every 6 hours (or **Agent settings → Updates → Check for updates**). When a new version is out it tells you what changed and asks: **Update now** or **Later**.
Every release is signed. The app installs only updates whose signature matches the key built into it, so a changed or fake file is refused.

Versions 1.0 and 1.0.1 cannot update from here: install the latest version once by hand. From 1.0.2 on, updates come automatically.

## Credits

Made by **Hanidayo**. Built with [Claude](https://claude.ai) (Anthropic).

---

## 바로드롭 (한국어)

[English](#barodrop) · **한국어**

바로드롭은 내 다른 컴퓨터의 폴더를 열고, 파일과 폴더를 디스크에서 디스크로 바로 복사하는 프로그램입니다. 좌우 두 칸 파일 탐색기처럼 씁니다.

- Windows, Mac(Apple 칩) 앱, 두 칸 탐색기 (목록 또는 사진 썸네일이 보이는 큰 아이콘)
- 내 시놀로지 NAS가 연결을 이어 줍니다. 가능하면 컴퓨터끼리 직접, 아니면 내 NAS 중계로 보냅니다. **파일은 NAS나 다른 곳에 저장되지 않습니다.**
- 내 컴퓨터끼리 한 번 등록하면 다음부터 한 번에 연결(연결해 온 컴퓨터도 나타나는 [열기]로 거꾸로 열기)
- 아이폰 앱: 내 컴퓨터 탐색, 사진·영상·문서 미리보기, 아이폰에 받기, 사진·파일을 컴퓨터로 보내기, 컴퓨터에서 아이폰(바로드롭 폴더·사진) 열기 (밖에서 접속 승인도 이 앱에서)
- 안드로이드 앱: 인증기와 영상 바로 재생을 뺀 같은 기능, 컴퓨터처럼 두 칸 화면(파일을 길게 눌러 끌어 놓으면 복사)
- 이 페이지에서 서명된 자동 업데이트
- 한국어와 영어 지원(맨 위 🌐 버튼)

이 저장소에는 **배포 파일**(프로그램과 업데이트 정보)이 있습니다. NAS용과 아이폰 앱은 각자 설치·빌드하는 파일로 제공합니다.

## 내려받기

**[Releases](https://github.com/hanidayo/barodrop-releases/releases/latest)** 에서 최신 버전을 받으세요.

| 컴퓨터 | 파일 |
|---|---|
| Windows 10 / 11 (64비트) | [BaroDropAgent-Windows.exe](https://github.com/hanidayo/barodrop-releases/releases/latest/download/BaroDropAgent-Windows.exe) |
| Mac (Apple 칩: M1/M2/M3/M4) | [BaroDropAgent-Mac.zip](https://github.com/hanidayo/barodrop-releases/releases/latest/download/BaroDropAgent-Mac.zip) |
| NAS (시놀로지, Container Manager) | [BaroDrop-NAS.zip](https://github.com/hanidayo/barodrop-releases/releases/latest/download/BaroDrop-NAS.zip) — 설치: [INSTALL-NAS.md](INSTALL-NAS.md) |
| 아이폰 (iOS 16 이상, Xcode로 직접 빌드) | [BaroDrop-iOS.zip](https://github.com/hanidayo/barodrop-releases/releases/latest/download/BaroDrop-iOS.zip) — 방법: [INSTALL-IOS.md](INSTALL-IOS.md) |
| 안드로이드 (10 이상) | [BaroDrop-Android.apk](https://github.com/hanidayo/barodrop-releases/releases/latest/download/BaroDrop-Android.apk) — 방법: [INSTALL-ANDROID.md](INSTALL-ANDROID.md) |

`latest.json` 은 앱이 읽는 서명된 업데이트 정보입니다. 받을 필요 없습니다.

## 내 NAS (처음 한 번)

바로드롭은 내 NAS에서 돌아갑니다. `BaroDrop-NAS.zip`을 받아 [INSTALL-NAS.md](INSTALL-NAS.md)(zip 안에도 있음)대로: 파일을 올리고, `nas.env.example`을 `.env`로 복사해 **세 줄**(내 주소, 비밀값, NAS 내부 IP)만 고친 뒤, Container Manager에서 빌드하고 역방향 프록시와 공유기 포트를 설정합니다. 다른 파일은 고칠 필요가 없습니다.

## 설치

**Windows**
1. `BaroDropAgent-Windows.exe` 를 실행합니다. Windows SmartScreen 창이 뜨면 **추가 정보 → 실행** 을 누르세요(유료 인증서로 서명하지 않은 앱이라 나옵니다).
2. 창에서 **이 컴퓨터에 설치하기** 를 누르면 시작 메뉴와 바탕 화면에 바로드롭이 생깁니다.
3. 앱 창에는 Microsoft Edge WebView2가 필요합니다(Windows 11과 최신 Windows 10에는 들어 있음).

**Mac**
1. `BaroDropAgent-Mac.zip` 을 풀고 **BaroDrop Agent** 를 엽니다.
2. "개발자를 확인할 수 없습니다"가 나오면 **시스템 설정 → 개인정보 보호 및 보안 → 그래도 열기** (또는 앱을 우클릭 → 열기).
3. **그래도 열기**가 없거나 **"손상되었기 때문에 열 수 없습니다"** 가 나오면, **터미널**(응용 프로그램 → 유틸리티)을 열고 한 번 실행하세요:
   ```
   xattr -dr com.apple.quarantine ~/Downloads/"BaroDrop Agent.app"
   ```
   이미 응용 프로그램 폴더에 있으면: `xattr -dr com.apple.quarantine "/Applications/BaroDrop Agent.app"`
   (또는 `xattr -dr com.apple.quarantine ` 까지 입력(끝에 한 칸 띄우기)하고 앱을 터미널 창에 끌어다 놓은 뒤 Return)
   유료 Apple 인증서가 없는 앱에 macOS가 붙이는 "인터넷에서 받음" 표시를 지우는 명령입니다.
4. 창에서 **이 컴퓨터에 설치하기** 를 누르면 응용 프로그램 폴더로 옮겨집니다.

**처음 설정**
1. 에이전트를 처음 실행하면 내 바로드롭 주소를 묻습니다(브라우저로 여는 주소와 같음).
2. 공유할 드라이브와 쓰기 허용 여부를 고릅니다.
3. 컴퓨터끼리 등록: 한쪽에서 **연결 코드 만들기**, 다른 쪽에서 그 코드를 입력합니다.

**아이폰 / 안드로이드**
안드로이드 앱은 Google Play에 없습니다. `BaroDrop-Android.apk`를 받아 휴대폰에서 열면 설치됩니다([INSTALL-ANDROID.md](INSTALL-ANDROID.md)).
아이폰 앱은 앱 스토어에 없습니다. [INSTALL-IOS.md](INSTALL-IOS.md)대로 Mac의 Xcode와 Apple ID(무료 또는 유료)로 빌드해 설치하세요. 인증기(푸시 승인)는 유료 Apple 개발자 계정과 각자의 푸시 키가 필요합니다.

## 업데이트

앱이 약 6시간마다 이 페이지를 확인하고(바로 하려면 **에이전트 설정 → 업데이트 → 업데이트 확인**), 새 버전이 있으면 바뀐 내용을 보여 주고 **지금 업데이트** / **나중에** 를 묻습니다.
모든 배포 파일은 서명되어 있습니다. 앱은 안에 든 키와 서명이 맞는 업데이트만 설치하므로, 바뀌거나 가짜인 파일은 설치되지 않습니다.

1.0과 1.0.1은 여기서 업데이트를 받지 못합니다. 최신 버전을 한 번 직접 설치해 주세요. 1.0.2부터는 자동으로 업데이트됩니다.

## 만든 사람

제작 **Hanidayo**. [Claude](https://claude.ai)(Anthropic)를 이용해 만들었습니다.
