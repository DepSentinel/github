# 👁️ DepSentinel

**Dependency Integrity Scanner & Wallet Safety Tools**  
_Stop supply-chain attacks, typosquats, and hidden wallet drainers before they reach users._

---

## 🚀 Projects
- **DepSentinel CLI** – Offline-first dependency scanner (npm/Node).  
  → https://github.com/dep-sentinel/dep-sentinel-cli
- **DepSentinel Action** – GitHub Action to scan every PR.  
  → https://github.com/dep-sentinel/dep-sentinel-action
- **NoRugX Bot** – Telegram bot to check mint tools & repos for drainers.  
  → https://github.com/dep-sentinel/norugx-bot
- **Website** – Marketing landers (DepSentinel + NoRugX).  
  → https://github.com/dep-sentinel/website

---

## 🛡️ What we catch
- Typosquat / look-alike packages
- Malicious or obfuscated **postinstall** scripts
- Suspicious tarball changes (size/file spikes)
- Shady outbound domains (pastebins, IPFS links, exfil endpoints)
- Newly modified packages & maintainer churn

---

## 📦 Try it in 60 seconds
```yaml
# .github/workflows/dep-sentinel.yml
name: dep-sentinel
on: [pull_request]
jobs:
  scan:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
      - run: npm ci
      - name: Dependency Integrity Scan
        uses: dep-sentinel/dep-sentinel-action@v1
