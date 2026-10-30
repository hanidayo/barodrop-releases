# 리눅스 서버에 바로드롭 설치 (Cloudflare Tunnel)

**한국어** · [English](#barodrop-on-a-linux-server-cloudflare-tunnel)

시놀로지 NAS 대신 집에 있는 리눅스 미니 PC(우분투 + 도커)에서 바로드롭 서버를 돌리는 방법입니다. 공유기 포트를 열지 않고 Cloudflare Tunnel로 바깥에 연결합니다.

## 준비물

- 도커가 설치된 리눅스 서버(우분투 등)
- Cloudflare에 연결된 도메인과, 이 서버에서 동작 중인 Cloudflare Tunnel(cloudflared)
- 바로드롭 1.7.7 이상의 `BaroDrop-NAS.zip`

## 1. 파일

1. `BaroDrop-NAS.zip`을 서버에 풀어 `BaroDrop` 폴더를 만듭니다(예: `~/barodrop`).
2. `server.env.example`을 복사해 `.env`로 저장하고 두 줄을 고칩니다.
   - `PUBLIC_URL=https://barodrop.example.com` (터널에 붙일 주소)
   - `SERVER_LAN_IP=192.168.0.20` (이 서버의 집 내부 IP)
   - (선택) `INVITE_CODE=원하는코드` — 새 기기가 처음 한 번 넣는 초대 코드. 비워 두면 주소만 알면 누구나 기기를 등록할 수 있습니다.
3. 실행: `docker compose -f compose.server.yaml up -d --build`
4. 처음 한 번 `docker compose -f compose.server.yaml logs barodrop`에서 **관리자 최초 설정 코드**를 확인합니다.

## 2. Cloudflare Tunnel

Cloudflare Zero Trust → Networks → Tunnels → (이 서버의 터널) → **Public Hostname 추가**

- 호스트 이름: `barodrop.example.com`
- 서비스: `HTTP` · `localhost:8787`

관리자 화면 포트(8790)는 터널에 붙이지 마세요. 관리자 화면은 집 네트워크(또는 Tailscale)에서 `http://서버내부IP:8790`으로 엽니다.

## 3. NAS에서 옮겨 오기 (선택)

예전 NAS에 등록한 컴퓨터·짝·인증기를 그대로 쓰려면:

1. NAS를 1.7.7 이상으로 올린 뒤, NAS 관리자 화면 → **설정 → 백업 내려받기**
2. 새 서버의 관리자 화면에서 설정 코드로 임시 비밀번호를 정하고 로그인 → **설정 → 백업 파일로 복원** → 서버가 다시 시작됩니다. 이후 관리자 비밀번호는 NAS에서 쓰던 것입니다.
3. 각 PC 에이전트: 설정 → 바로드롭 서버 주소를 새 주소로 바꾸고 저장. 등록과 내 기기 짝이 그대로 이어집니다.
4. 휴대폰 앱: ⚙ → 바로드롭 주소 바꾸기 → 새 주소. 주소가 바뀌면 휴대폰은 새 기기가 되므로 컴퓨터 추가(연결 코드)를 한 번 다시 합니다. 아이폰 인증기는 새 서버 관리자 화면 → 인증기에서 **폐기**한 뒤 같은 화면의 QR로 다시 등록합니다(앱이 예전 주소를 기억하고 있기 때문).
5. 다 옮겼으면 NAS의 바로드롭 컨테이너를 멈춥니다.

## 알아 두기

- 내려받기 화면: `https://(바로드롭 주소)/download` (`/d`로도 열림) — 다른 사람에게 이 주소만 알려 주면 됩니다.

- TURN 서버 없이 동작합니다. 회사망 등에서 직접 연결이 막히면 바로드롭 서버를 거치는 중계로 자동 전환합니다.
- 집에서 쓰는 기기는 서버와 같은 공인 IP로 들어오므로 집 네트워크로 인정됩니다(`HOME_PUBLIC_IP=auto`).
- 업데이트: 새 `BaroDrop-NAS.zip`의 파일로 덮어쓰고(`.env`는 그대로) `docker compose -f compose.server.yaml up -d --build`.

---

## BaroDrop on a Linux server (Cloudflare Tunnel)

[한국어](#리눅스-서버에-바로드롭-설치-cloudflare-tunnel) · **English**

Run the BaroDrop server on a Linux mini PC at home (Ubuntu + Docker) instead of a Synology NAS, reachable from outside through Cloudflare Tunnel — no router ports to open.

## You need

- A Linux server with Docker
- A domain on Cloudflare and a Cloudflare Tunnel (cloudflared) running on this server
- `BaroDrop-NAS.zip` from BaroDrop 1.7.7 or later

## 1. Files

1. Unzip `BaroDrop-NAS.zip` on the server (e.g. `~/barodrop`).
2. Copy `server.env.example` to `.env` and set `PUBLIC_URL` (the tunnel's address) and `SERVER_LAN_IP` (the server's home address). Optional: `INVITE_CODE=…` — new devices enter it once; empty lets anyone with the address register a device.
3. Start: `docker compose -f compose.server.yaml up -d --build`
4. Find the **admin setup code** once in `docker compose -f compose.server.yaml logs barodrop`.

## 2. Cloudflare Tunnel

Cloudflare Zero Trust → Networks → Tunnels → (this server's tunnel) → **Add a public hostname**: `barodrop.example.com` → `HTTP` · `localhost:8787`.
Do not put the admin port (8790) on the tunnel; open the admin page at home (or over Tailscale) at `http://server-address:8790`.

## 3. Moving from the NAS (optional)

1. Update the NAS to 1.7.7+, then NAS admin page → **Settings → Download backup**.
2. On the new server's admin page, set a temporary password with the setup code, sign in → **Settings → Restore from backup**. The server restarts; the admin password is the NAS's again.
3. Each PC agent: Settings → change the BaroDrop server address and save. Its registration and paired devices carry over.
4. Phone apps: ⚙ → change the BaroDrop address. A phone is a new device at a new address: add your computers once more (pairing code), and re-register the iPhone authenticator: new server's admin page → Authenticator → **Revoke**, then scan the QR again (the app remembers the old address).
5. Stop BaroDrop on the NAS.

## Good to know

- Download page: `https://(your address)/download` (also `/d`) — share just this address.

- No TURN server: when a direct link is blocked, BaroDrop relays through this server.
- Devices at home arrive with the server's own public address and count as home (`HOME_PUBLIC_IP=auto`).
- Updating: copy the new `BaroDrop-NAS.zip` files over (keep `.env`) and run `docker compose -f compose.server.yaml up -d --build`.

Made by Hanidayo · Built with Claude
