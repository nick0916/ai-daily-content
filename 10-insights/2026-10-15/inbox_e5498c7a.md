---
id: inbox_e5498c7a
date: 2026-10-15
source_ref: "[[00-inbox/2026-10-15/0102-lobsters-vibecoding-sslx-a-fast-modern-alternative-to-openss-f5e2]]"
title: "sslx: A fast, modern alternative to OpenSSL&#39;s CLI"
url: https://github.com/glincker/sslx
source: lobsters-vibecoding
published_at: 2026-10-15T05:02:33-05:00
fetched_at: 2026-10-25T01:29:34.904372+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "用一個 Rust 執行檔取代多數 openssl 指令，處理憑證、TLS 連線與格式轉換。 **Why** 原文指出，常見的憑證工作需要記憶多個 openssl 指令與旗標，操作成本高。 **How** 以 Rust 與 rustls 實作，不需要系統 OpenSSL。 **What** 提供 grade、expiry、inspect、connect、generate、csr、convert、match、extract、decode、verify 等子命令；grade 會給出 A+ 到 F 等級，expiry 在憑證 7 天內到期時回傳 exit code 1；所有指令支援 --json，並可用 cargo install 或 brew install glincker/tap/sslx 安裝。專案以 MIT 授權。"
key_points:
  - "單一執行檔（Rust 與 rustls），不需系統 OpenSSL；可用 cargo install sslx 或 Homebrew 安裝"
  - "sslx grade 檢查 TLS 版本、cipher、憑證有效期、金鑰、hostname、chain 完整性與 ALPN，並給出 A+ 到 F 等級"
  - "sslx expiry 在憑證 7 天內到期時 exit code 為 1，適合用於 cron 或 CI；所有指令都支援 --json 輸出"
tags: [rust, tls, openssl, cli, certificates]
topics: [security]
importance: 2
novelty: 2
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## sslx: A fast, modern alternative to OpenSSL's CLI

用一個 Rust 執行檔取代多數 openssl 指令，處理憑證、TLS 連線與格式轉換。 **Why** 原文指出，常見的憑證工作需要記憶多個 openssl 指令與旗標，操作成本高。 **How** 以 Rust 與 rustls 實作，不需要系統 OpenSSL。 **What** 提供 grade、expiry、inspect、connect、generate、csr、convert、match、extract、decode、verify 等子命令；grade 會給出 A+ 到 F 等級，expiry 在憑證 7 天內到期時回傳 exit code 1；所有指令支援 --json，並可用 cargo install 或 brew install glincker/tap/sslx 安裝。專案以 MIT 授權。

### 重點
- 單一執行檔（Rust 與 rustls），不需系統 OpenSSL；可用 cargo install sslx 或 Homebrew 安裝
- sslx grade 檢查 TLS 版本、cipher、憑證有效期、金鑰、hostname、chain 完整性與 ALPN，並給出 A+ 到 F 等級
- sslx expiry 在憑證 7 天內到期時 exit code 為 1，適合用於 cron 或 CI；所有指令都支援 --json 輸出

**原文：** [lobsters-vibecoding](https://github.com/glincker/sslx)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

sslx

Install

TLS grade

Expiry check

Inspect certificates

Connect to a host

Generate certs

Generate a CSR

Convert between formats

Check cert+key match

Extract from PKCS12

Decode anything

Verify a chain

openssl vs sslx

JSON output

Exit codes

Benchmarks

Shell completions

Community

Contributing

License

openssl, but you don't have to google the flags.

A single binary that handles certs, TLS connections, and all the stuff you normally need three different openssl invocations for. Built with Rust and rustls , no system OpenSSL required.

 

Prebuilt binaries on the releases page .

Homebrew:

Or download directly:

Rate the TLS setup of any host, like SSL Labs but from your terminal:

Checks protocol version, cipher strength, cert validity, key type, hostname matching, chain completeness, and ALPN. Gives you a letter grade from A+ to F.

Check cert expiry on a bunch of hosts at once:

Exit code 1 if anything expires within 7 days. Useful in cron jobs or CI pipelines.

Read a PEM or DER cert file with colored output:

Handles multi-cert bundles too. Auto-detects PEM vs DER.

See the full TLS handshake details and cert chain for any host:

Self-signed cert for local dev in one command:

Creates cert.pem and key.pem with EC P-256 by default. Also supports ec384 and ed25519 .

Creates csr.pem and key.pem . Submit the CSR to your CA.

Auto-detects input format.

No more comparing modulus hashes manually.

Pulls out the leaf cert, intermediates, and key into separate PEM files.

Throw a file or a JWT token at it and sslx figures out what it is:

Also detects PEM certs, DER files, private keys, public keys, and CSRs.

Tells you exactly what's wrong if it fails, with hints on how to fix it.

Every command supports --json for scripting and CI:

Median of 10 runs on macOS M2:

Join the GLINR Discord to ask questions, share feedback, or talk to other users. This project has its own forum channel, #sslx.

See CONTRIBUTING.md . Bugs and feature requests go in issues .

MIT

cargo install sslx

brew install glincker/tap/sslx

# macOS (Apple Silicon) curl -fsSL https://github.com/glincker/sslx/releases/latest/download/sslx-macos-aarch64 -o sslx && chmod +x sslx # Linux curl -fsSL https://github.com/glincker/sslx/releases/latest/download/sslx-linux-x86_64 -o sslx && chmod +x sslx

$ sslx grade github.com

 ╭──────────────────────────────────────────╮
 │ github.com:443 Grade: A+ │
 ╰──────────────────────────────────────────╯

 ✓ Protocol TLS 1.3
 ✓ Cipher TLS13_AES_128_GCM_SHA256 (AEAD)
 ✓ Certificate Valid, 49 days remaining
 ✓ Key ECDSA P-256 (256 bit)
 ✓ Hostname github.com in SANs
 ✓ Chain Complete (3 certs)
 ✓ ALPN HTTP/2 supported

$ sslx expiry google.com github.com cloudflare.com stripe.com

 Host Expires Days Status
 ────────────────────────────────────────────────────────────────
 ✓ google.com:443 2026-06-15 61 OK
 ✓ github.com:443 2026-06-03 49 OK
 ✓ cloudflare.com:443 2026-06-10 56 OK
 ✓ stripe.com:443 2026-09-01 139 OK

$ sslx inspect cert.pem

╭─ Certificate 1 of 1 ──────────────────────────────────╮
│ Subject: CN=*.example.com │
│ Issuer: CN=Let's Encrypt Authority X3 │
│ Serial: 0A:1B:2C:3D... │
│ │
│ Valid: 2026-01-15 → 2026-04-15 │
│ Expires: ██░░░░░░░░ 12 days remaining [!] │
│ │
│ Key: ECDSA P-256 (256 bit) │
│ SANs: *.example.com, example.com │
│ SHA-256: AB:CD:EF:12:34... │
╰──────────────────────────────────────────────────────────╯

$ sslx connect example.com

Connection to example.com:443

 TLS 1.3 · TLS13_AES_256_GCM_SHA384
 ALPN: h2

 Chain:
 ╭─ Certificate 1 of 3 ─────────────────────────╮
 │ Subject: CN=*.example.com │
 │ Valid: 61 days remaining ✓ │
 │ Key: ECDSA P-256 (256 bit) │
 ╰────────────────────────────────────────────────╯
 ↓ signed by
 ╭─ Certificate 2 of 3 (CA) ────────────────────╮
 │ ... │
 ╰────────────────────────────────────────────────╯

sslx generate --cn localhost --san " *.local,127.0.0.1 "

sslx csr --cn example.com --san " *.example.com,api.example.com "

sslx convert cert.pem --to der # PEM to DER sslx convert cert.der --to pem # DER to PEM sslx convert bundle.p12 --to pem # PKCS12 to PEM

$ sslx match cert.pem key.pem

 ✓ Certificate and key match (ECDSA P-256 (256 bit))

sslx extract bundle.p12 --password mypass --out ./certs

$ sslx decode eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...

 ✓ Detected: JSON Web Token (JWT)

 Header: {"alg":"HS256","typ":"JWT"}
 Payload: {"sub":"1234567890","name":"John","iat":1516239022}
 Expires: in 3 hours

sslx verify cert.pem --ca ca-bundle.pem

✓ Certificate is valid
 Chain: complete (3 certs)
 Expiry: 328 days remaining

# check days until expiry sslx connect example.com --json | jq ' .chain.certificates[0].days_remaining ' # get the grade sslx grade example.com --json | jq ' .grade ' # list all SANs sslx inspect cert.pem --json | jq ' .certificates[0].sans '

sslx completions bash > /etc/bash_completion.d/sslx
sslx completions zsh > ~ /.zsh/completions/_sslx
sslx completions fish > ~ /.config/fish/completions/sslx.fish

</details>