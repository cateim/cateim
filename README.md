<p align="center">
  <a href="https://selflabs.org">
    <img src="https://selflabs.org/og.png" width="640" alt="Self-Labs">
  </a>
</p>

<h1 align="center">Gustavo Cateim</h1>

<p align="center">
  <a href="https://selflabs.org"><img src="https://img.shields.io/badge/selflabs.org-0b2a2f?style=flat-square&logo=astro&logoColor=22d3ee" alt="selflabs.org"></a>
  <a href="https://store.selflabs.org"><img src="https://img.shields.io/badge/store-bitcoin_only-0b2a2f?style=flat-square&logo=bitcoin&logoColor=f7931a" alt="store"></a>
  <img src="https://img.shields.io/badge/Vit%C3%B3ria,%20ES-Brazil-0b2a2f?style=flat-square&logo=googlemaps&logoColor=34d399" alt="Vitória, ES, Brazil">
</p>

<p align="center"><em>A one person lab, with uptime.</em></p>

---

I build **firmware for Bitcoin hardware wallets**, **management systems for the
Brazilian public sector**, and **infrastructure that runs on hardware I own**.
All of it under [**Self-Labs**](https://github.com/self-labs), which is a
laboratory, not a company: the "self" is literal. Self-hosted, self-custody,
done by hand.

No managed database without a reason. No deploy that depends on someone logging
into a server. No private key inside a machine that talks to the internet.

> When something broke in production, it is written in the repository that it
> broke, with a date and a file reference. That is traceability, not modesty.

## What is actually running

| System                                     | What it solves                                                    | Notable detail                                                                                                                                             |
| ------------------------------------------ | ----------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Wallet Store**                           | Bitcoin only store, no payment processor in the middle            | Watch only xpub, every address derived locally. Refuses to boot if the configured keys derive an unexpected address. Buyer data erased 72h after delivery. |
| **ALFERES**                                | Personnel, leave and health management for a military police unit | Around 500 people inside, in daily use                                                                                                                     |
| **Jade DIY**                               | Turns off the shelf ESP32 boards into a working Blockstream Jade  | Signed firmware, web flasher, battery and touch logic for four different boards                                                                            |
| **Radar de Promo**                         | Price tracking that pings when a deal is real                     | TypeScript, self-hosted, no affiliate noise                                                                                                                |
| **[cups](https://github.com/cateim/cups)** | Latest OpenPrinting CUPS for Debian and Ubuntu                    | Built from official source because the distro packages were years behind                                                                                   |
| **[selflabs.org](https://selflabs.org)**   | The lab's landing page                                            | Astro, bilingual, Cloudflare Workers. Numbers on it come from the GitHub API, never typed by hand                                                          |

## Upstream

Pull requests accepted in 8 repositories owned by 7 different people, plus write
access to somebody else's project.

| Project                                                                                                           | What I sent                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| ----------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [Blockstream/Jade](https://github.com/Blockstream/Jade)                                                           | Five pull requests accepted into the official firmware of the Jade hardware wallet: swapped buttons on TTGO and USB JTAG on Waveshare S3 ([#260](https://github.com/Blockstream/Jade/pull/260)), Windows connectivity and USB detection ([#268](https://github.com/Blockstream/Jade/pull/268)), battery stability and power logic across T-Display, T-Display S3 and Waveshare S3 ([#270](https://github.com/Blockstream/Jade/pull/270), [#271](https://github.com/Blockstream/Jade/pull/271)), and releasing the touch handles before deleting the i2c bus ([#307](https://github.com/Blockstream/Jade/pull/307)) |
| [oroderico/origo](https://github.com/oroderico/origo)                                                             | Write access to someone else's repository, where I fix bugs. It generates a BIP39 seed from human thrown dice, built after roughly 88 million dollars left Coldcard wallets through a build flag that lowered entropy unnoticed for five years                                                                                                                                                                                                                                                                                                                                                                     |
| [akitaonrails/ai-memory](https://github.com/akitaonrails/ai-memory)                                               | Native Windows hook command with no shell spawn, hook merging instead of overwriting third party hooks, JSON output to kill debug spam                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| [akitaonrails/FrankMD](https://github.com/akitaonrails/FrankMD)                                                   | Multi arch amd64 and arm64 Docker publishing, tag normalisation, version in the About dialog                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| [RobHofmann/HomeAssistant-GreeClimateComponent](https://github.com/RobHofmann/HomeAssistant-GreeClimateComponent) | Brazilian Portuguese translation                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| [albaintor/homeassistant_electrolux_status](https://github.com/albaintor/homeassistant_electrolux_status)         | Two fixes on appliance status handling                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| [ayghri/i-have-adhd](https://github.com/ayghri/i-have-adhd)                                                       | Raised the SessionStart hook timeout so the always on mode is not silently dropped under load                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

Recurring theme: I run Windows and ARM64, which is exactly where most projects
quietly break.

<sub>The Jade pull requests show as closed rather than merged because the
maintainers land the changes through their own branch. The fixes are in the
shipped firmware.</sub>

## How everything ships

```
push to master
      |
      v
  CI: tests, typecheck, image build on a NATIVE arm64 runner (never QEMU)
      |
      v
  webhook -> Portainer stack pulls the repo
      |
      v
  Orange Pi 5 / Ampere VPS
```

No manual step, no SSH at two in the morning, same path in every project. The
deploy job fails loud on any HTTP status outside 2xx, so a broken redeploy never
looks like a green build.

## Written down because it broke

- **The dev server died on every Vite re optimisation.** `EPERM ... rmdir
node_modules\.vite\deps`, then a libuv assertion. Cause: 345 of 345 directories
  in the checkout carried the Windows ReadOnly attribute, and Node's `rmdir`
  returns EPERM on those. Documented in
  [self-labs/self-labs `CLAUDE.md`](https://github.com/self-labs/self-labs/blob/master/CLAUDE.md).
- **An animated trace where the dot vanished at 79% of the band.** The trace
  scrolled _and_ the head ran, so what you saw was the difference between two
  speeds, and that difference is always a whole multiple of 120 units while a
  browser window is any width at all. Fixed by removing the shape, not by
  patching the symptom.

## Stack

| Layer    |                                                                                                  |
| -------- | ------------------------------------------------------------------------------------------------ |
| Firmware | `C` `ESP-IDF` `ESP32 / S3`                                                                       |
| Web      | `TypeScript` `Node.js` `Astro` `Vanilla JS` `PHP` `Python` `C#`                                  |
| Data     | `PostgreSQL` `SQLite`                                                                            |
| Infra    | `Docker` `Portainer` `Cloudflare Workers` `Cloudflare Tunnel` `Caddy` `GitHub Actions` `Forgejo` |
| Hardware | `Orange Pi 5` `Ampere VPS` `OpenWrt` `Home Assistant`                                            |

## Elsewhere

[selflabs.org](https://selflabs.org) · [store.selflabs.org](https://store.selflabs.org) · [@self-labs](https://github.com/self-labs) · [@gucateim](https://instagram.com/gucateim) · contato@selflabs.org
