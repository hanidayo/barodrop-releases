# BaroDrop on your NAS (Synology)

**English** · [한국어](#내-nas에-바로드롭-설치-시놀로지)

BaroDrop's NAS part shows the BaroDrop page, connects your devices and relays when they cannot reach each other directly. **It never stores your files.** Tested with Synology DSM 7 + Container Manager.

## What you need

- A Synology NAS with **Container Manager** (Package Center)
- An address for your NAS from outside, e.g. Synology DDNS `mynas.synology.me` (DSM Control Panel → External Access → DDNS) and its certificate (Let's Encrypt, Control Panel → Security → Certificate)
- Access to your router's port forwarding

## 1. Files

1. Download `BaroDrop-NAS-vX.Y.zip` from [Releases](https://github.com/hanidayo/barodrop-releases/releases/latest) and unzip it.
2. In File Station, create the folder `docker/barodrop` and upload everything inside the `BaroDrop` folder into it.
3. Copy `nas.env.example` to **`.env`** in the same folder and edit **three lines** (that is the only file you change):

| Line | Example | What it is |
|---|---|---|
| `PUBLIC_URL` | `https://mynas.synology.me:8443` | Your BaroDrop address (what you open in the browser) |
| `TURN_SECRET` | 32+ random characters | Shared by BaroDrop and its TURN server |
| `NAS_LAN_IP` | `192.168.0.10` | The NAS's home-network address (Control Panel → Network → Network Interface). Reserve it in your router. |

## 2. Run

Container Manager → **Project → Create** → name `barodrop`, path `docker/barodrop`, use the existing `compose.yaml` → build and start. Two containers start: `barodrop` and `coturn`.

## 3. Reverse proxy (DSM)

Control Panel → Login Portal → Advanced → **Reverse Proxy → Create**:

| | Source | Destination |
|---|---|---|
| Protocol | HTTPS | HTTP |
| Host name | `mynas.synology.me` (your name) | `127.0.0.1` |
| Port | `8443` (the port in PUBLIC_URL) | `8787` |

Then **Custom Header → Create → WebSocket** (adds Upgrade and Connection) → Save. Required for PC agents.
Pick the certificate for this name in Control Panel → Security → Certificate → Settings.

## 4. Router ports (to the NAS's address)

- TCP **8443** (the BaroDrop port in PUBLIC_URL)
- TCP and UDP **3478**, UDP **49160–49200** (TURN relay)

Do **not** forward 8787 or 8790. If DSM's firewall is on, allow the same ports.

## 5. Admin page and first use

- Admin page (home network only): `http://<NAS_LAN_IP>:8790`. The first-time code is in Container Manager → barodrop container → **Log** (`BaroDrop 관리자 최초 설정 코드`).
- Install the PC agent on each computer (BaroDrop page → Settings → Get the PC agent, or from Releases), and enter your BaroDrop address when it asks.
- Pair your computers: **Make a pairing code** on one agent, enter it on the other.

## Updating

Download the new NAS zip, upload it over the old files (keep `.env`), then Container Manager → project → Stop → Build → Start. Your devices are kept (`device_data` volume). The admin page tells you when a newer version is on GitHub. PC agents update themselves from GitHub.

---

## 내 NAS에 바로드롭 설치 (시놀로지)

[English](#barodrop-on-your-nas-synology) · **한국어**

바로드롭의 NAS 부분은 바로드롭 화면을 보여 주고, 기기들을 연결해 주고, 직접 연결이 안 될 때 중계합니다. **파일은 NAS에 저장하지 않습니다.** 시놀로지 DSM 7 + Container Manager 기준입니다.

## 준비물

- **Container Manager**(패키지 센터)가 설치된 시놀로지 NAS
- 밖에서 들어오는 NAS 주소. 예: 시놀로지 DDNS `mynas.synology.me`(제어판 → 외부 액세스 → DDNS)와 인증서(제어판 → 보안 → 인증서, Let's Encrypt)
- 공유기 포트 전달 설정

## 1. 파일

1. [Releases](https://github.com/hanidayo/barodrop-releases/releases/latest)에서 `BaroDrop-NAS-vX.Y.zip`을 받아 풉니다.
2. File Station에서 `docker/barodrop` 폴더를 만들고, `BaroDrop` 폴더 안의 파일을 전부 올립니다.
3. 같은 폴더에서 `nas.env.example`을 **`.env`** 로 복사하고 **세 줄만** 고칩니다(고치는 파일은 이것 하나뿐):

| 줄 | 예 | 뜻 |
|---|---|---|
| `PUBLIC_URL` | `https://mynas.synology.me:8443` | 내 바로드롭 주소(브라우저로 여는 주소) |
| `TURN_SECRET` | 32자 이상 아무 문자 | 바로드롭과 TURN이 같이 쓰는 비밀값 |
| `NAS_LAN_IP` | `192.168.0.10` | NAS 내부 IP(제어판 → 네트워크 → 네트워크 인터페이스). 공유기에서 고정해 두세요. |

## 2. 실행

Container Manager → **프로젝트 → 생성** → 이름 `barodrop`, 경로 `docker/barodrop`, 기존 `compose.yaml` 사용 → 빌드·시작. `barodrop`, `coturn` 두 컨테이너가 실행됩니다.

## 3. 역방향 프록시 (DSM)

제어판 → 로그인 포털 → 고급 → **역방향 프록시 → 생성**:

| | 소스 | 대상 |
|---|---|---|
| 프로토콜 | HTTPS | HTTP |
| 호스트 이름 | `mynas.synology.me`(내 주소) | `127.0.0.1` |
| 포트 | `8443`(PUBLIC_URL의 포트) | `8787` |

이어서 **사용자 지정 머리글 → 생성 ▾ → WebSocket**(Upgrade, Connection 두 줄) → 저장. PC 에이전트에 꼭 필요합니다.
제어판 → 보안 → 인증서 → 설정에서 이 주소의 인증서를 고릅니다.

## 4. 공유기 포트 전달 (대상 = NAS 내부 IP)

- TCP **8443** (PUBLIC_URL의 바로드롭 포트)
- TCP·UDP **3478**, UDP **49160–49200** (TURN 중계)

8787, 8790은 **열지 마세요**. DSM 방화벽을 쓰면 같은 포트를 허용합니다.

## 5. 관리자 화면과 처음 쓰기

- 관리자 화면(집 네트워크에서만): `http://<NAS_LAN_IP>:8790`. 처음 설정 코드는 Container Manager → barodrop 컨테이너 → **로그**의 `BaroDrop 관리자 최초 설정 코드` 줄.
- 각 컴퓨터에 PC 에이전트 설치(바로드롭 화면 → 설정 → PC 에이전트 받기, 또는 Releases). 처음 실행하면 내 바로드롭 주소를 묻습니다.
- 컴퓨터끼리 등록: 한 에이전트에서 **연결 코드 만들기** → 다른 에이전트에 입력.

## 업데이트

새 NAS ZIP을 받아 기존 파일 위에 올리고(`.env`는 그대로), Container Manager → 프로젝트 → 중지 → 빌드 → 시작. 등록한 기기는 유지됩니다(`device_data` 볼륨). GitHub에 새 버전이 있으면 관리자 화면에 표시됩니다. PC 에이전트는 GitHub에서 스스로 업데이트됩니다.

Made by Hanidayo · Built with Claude
