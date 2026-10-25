# BaroDrop iPhone app — build it yourself

**English** · [한국어](#바로드롭-아이폰-앱--직접-빌드하기)

The iPhone app is not on the App Store. `BaroDrop-iOS.zip` holds its Xcode project: build it on your Mac and install it on your iPhone.

What the app does: browse your computers, preview and save files to the iPhone, play videos while they arrive, send photos and files to a computer, open the iPhone (its BaroDrop folder and photos) from a computer, and (optionally) approve access from outside as the authenticator.

## You need

- A Mac with **Xcode** (App Store, free). Open it once after installing.
- An iPhone with **iOS 16** or later, and a USB cable.
- An **Apple ID**. A free one works, with limits (below). A paid Apple Developer Program membership ($99/year) removes them.
- **BaroDrop on your NAS, version 1.3 or later** (see [INSTALL-NAS.md](INSTALL-NAS.md)), and the PC agent on your computers.

| | Free Apple ID | Paid developer account |
|---|---|---|
| Browse, receive, send, open the iPhone from a computer | ✅ | ✅ |
| App keeps working | 7 days, then build and install again | 1 year |
| Authenticator push notifications | ❌ | ✅ (with your own push key on the NAS) |

## Build and install

1. Unzip `BaroDrop-iOS.zip` and open `ios/BaroDropAuth.xcodeproj` in Xcode.
2. Xcode → **Settings → Accounts**: add your Apple ID.
3. In the left column click **BaroDropAuth** (blue icon) → target **BaroDropAuth** → tab **Signing & Capabilities**:
   - **Team**: choose your team (your name, "Personal Team" for a free account).
   - **Bundle Identifier**: change `com.barodrop.auth` to your own unique ID, for example `com.yourname.barodrop`. (The original ID belongs to the author's account and cannot be used.)
   - **Free Apple ID only**: delete the **Push Notifications** capability (the trash/✕ next to it). Free accounts cannot sign apps with it.
4. Connect the iPhone with the cable and unlock it. Tap **Trust** if asked. Choose the iPhone at the top of the Xcode window.
5. On the iPhone, turn on **Settings → Privacy & Security → Developer Mode** (it appears after the iPhone is connected to Xcode once) and restart when asked.
6. Press **▶ (Run)** in Xcode. The first build takes a few minutes.
7. If the iPhone says "Untrusted Developer": **Settings → General → VPN & Device Management** → your Apple ID → **Trust**. Then open the app.

With a free Apple ID, repeat step 6 every 7 days (when the app stops opening).

## First use

1. Tab **Browse**: enter your BaroDrop address (the same address you open in the browser on your computers).
2. **＋ Add computer** → on the computer: agent settings (tray / menu bar icon) → **Make a pairing code** → enter the 8-character code on the iPhone → approve on the computer.
3. Tap **Connect** next to the computer. Allow **Local Network** when asked (direct link on the same Wi-Fi).
4. Send to a computer: open the folder on the computer, then **＋ Send from iPhone**. Open the iPhone from a computer: keep the app open; it appears in **My devices** on the computer as "iPhone · app open".

## Authenticator (optional, paid account)

The authenticator approves new devices and access from outside, with a push notification. It needs your own Apple push key:
Apple Developer → **Keys** → new key with **Apple Push Notifications service (APNs)** → put `AuthKey.p8` in the NAS's `apns` folder and set `APNS_KEY_ID`, `APNS_TEAM_ID` and `APNS_TOPIC` (= your Bundle Identifier) in `.env`, then rebuild the NAS. In the app: **Settings → Advanced → Use this iPhone as the authenticator**, and scan the QR from the NAS admin page.
Never share your push key or signing certificate.

---

## 바로드롭 아이폰 앱 — 직접 빌드하기

[English](#barodrop-iphone-app--build-it-yourself) · **한국어**

아이폰 앱은 앱 스토어에 없습니다. `BaroDrop-iOS.zip`에 Xcode 프로젝트가 들어 있으니 각자 Mac에서 빌드해 아이폰에 설치하세요.

앱으로 하는 일: 내 컴퓨터 탐색, 미리보기·아이폰에 받기, 영상 받으면서 재생, 사진·파일을 컴퓨터로 보내기, 컴퓨터에서 아이폰(바로드롭 폴더·사진) 열기, (선택) 인증기로 밖에서 접속 승인.

## 준비물

- **Xcode**가 설치된 Mac(앱 스토어, 무료). 설치 후 한 번 실행하세요.
- **iOS 16** 이상 아이폰과 USB 케이블
- **Apple ID**. 무료 계정도 되지만 제한이 있습니다(아래). 유료 Apple Developer Program(연 $99)이면 제한이 없습니다.
- **내 NAS의 바로드롭 1.3 이상**([INSTALL-NAS.md](INSTALL-NAS.md))과 컴퓨터의 PC 에이전트

| | 무료 Apple ID | 유료 개발자 계정 |
|---|---|---|
| 탐색, 받기, 보내기, 컴퓨터에서 아이폰 열기 | ✅ | ✅ |
| 앱 사용 기간 | 7일 (지나면 다시 빌드·설치) | 1년 |
| 인증기 푸시 알림 | ❌ | ✅ (NAS에 내 푸시 키 필요) |

## 빌드와 설치

1. `BaroDrop-iOS.zip`을 풀고 `ios/BaroDropAuth.xcodeproj`를 Xcode로 엽니다.
2. Xcode → **Settings → Accounts**에서 Apple ID 추가
3. 왼쪽 맨 위 **BaroDropAuth**(파란 아이콘) → 타깃 **BaroDropAuth** → **Signing & Capabilities** 탭:
   - **Team**: 내 팀 선택(무료 계정은 "Personal Team")
   - **Bundle Identifier**: `com.barodrop.auth`를 나만의 ID로 바꾸기. 예) `com.내이름.barodrop` (원래 ID는 만든 사람 계정 것이라 쓸 수 없습니다.)
   - **무료 Apple ID만**: **Push Notifications** 항목을 삭제(옆의 휴지통/✕). 무료 계정은 이 항목이 있으면 서명되지 않습니다.
4. 아이폰을 케이블로 연결하고 잠금 해제, "이 컴퓨터를 신뢰" → Xcode 위쪽에서 내 아이폰 선택
5. 아이폰 **설정 → 개인정보 보호 및 보안 → 개발자 모드** 켜기(Xcode에 한 번 연결하면 나타남) → 재시동
6. Xcode에서 **▶ (Run)**. 첫 빌드는 몇 분 걸립니다.
7. 아이폰에 "신뢰하지 않는 개발자"가 나오면: **설정 → 일반 → VPN 및 기기 관리** → 내 Apple ID → **신뢰**. 그다음 앱을 엽니다.

무료 Apple ID는 7일마다(앱이 안 열리면) 6번을 다시 하면 됩니다.

## 처음 쓰기

1. **탐색** 탭: 바로드롭 주소 입력(컴퓨터 브라우저로 여는 주소와 같음)
2. **＋ 컴퓨터 추가** → 컴퓨터의 에이전트 설정(트레이/메뉴 막대 아이콘) → **연결 코드 만들기** → 8자리 코드를 아이폰에 입력 → 컴퓨터에서 승인
3. 컴퓨터 옆 **연결**. "로컬 네트워크" 허용 창이 뜨면 허용(같은 와이파이 직접 연결)
4. 컴퓨터로 보내기: 컴퓨터의 폴더를 연 뒤 **＋ 아이폰에서 보내기**. 컴퓨터에서 아이폰 열기: 앱을 켜 두면 컴퓨터의 **내 기기**에 "아이폰 · 앱 열림"으로 보입니다.

## 인증기 (선택, 유료 계정)

인증기는 새 기기 등록과 밖에서의 접속을 푸시 알림으로 승인합니다. 내 Apple 푸시 키가 필요합니다:
Apple Developer → **Keys** → **Apple Push Notifications service (APNs)** 키 만들기 → `AuthKey.p8`를 NAS의 `apns` 폴더에 넣고, `.env`에 `APNS_KEY_ID`, `APNS_TEAM_ID`, `APNS_TOPIC`(= 내 Bundle Identifier)을 적은 뒤 NAS 다시 빌드. 앱에서 **설정 → 고급 → 이 아이폰을 인증기로 등록** → NAS 관리자 화면의 QR을 비추기.
푸시 키와 서명 인증서는 절대 남과 공유하지 마세요.

Made by Hanidayo · Built with Claude
