<p align="center">
  <a href="https://selflabs.org">
    <img src="https://selflabs.org/og.png" width="640" alt="Self-Labs">
  </a>
</p>

<h1 align="center">Gustavo Cateim</h1>

<p align="center">
  <a href="https://selflabs.org"><img src="https://img.shields.io/badge/selflabs.org-0b2a2f?style=flat-square&logo=astro&logoColor=22d3ee" alt="selflabs.org"></a>
  <a href="https://store.selflabs.org"><img src="https://img.shields.io/badge/store-hardware_wallets-0b2a2f?style=flat-square&logo=bitcoin&logoColor=f7931a" alt="store"></a>
  <img src="https://img.shields.io/badge/Vit%C3%B3ria,%20ES-Brazil-0b2a2f?style=flat-square&logo=googlemaps&logoColor=34d399" alt="Vitória, ES, Brazil">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fselflabs.org%2Fstats.json&style=flat-square&labelColor=0b2a2f&query=%24.commits&label=commits&color=22d3ee" alt="commits">
  <img src="https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fselflabs.org%2Fstats.json&style=flat-square&labelColor=0b2a2f&query=%24.repositorios&label=repositories&color=22d3ee" alt="repositories">
  <img src="https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fselflabs.org%2Fstats.json&style=flat-square&labelColor=0b2a2f&query=%24.prsExternos&label=upstream%20PRs&color=34d399" alt="upstream pull requests">
</p>

<p align="center"><em>A one person lab, with uptime.</em></p>

<p align="center">
  <sub>The counters are read live from <a href="https://selflabs.org/stats.json">selflabs.org/stats.json</a>, regenerated from the GitHub API every Monday, private repositories included.</sub>
</p>

---

I build **firmware for Bitcoin hardware wallets**, **management systems for the
Brazilian public sector**, **home automation on boards I flash myself**, and
**infrastructure that runs on hardware I own**. All of it under
[**Self-Labs**](https://github.com/self-labs), which is a laboratory, not a
company: the "self" is literal. Self-hosted, self-custody, done by hand.

No managed database without a reason. No deploy that depends on someone logging
into a server. No private key inside a machine that talks to the internet.

> When something broke in production, it is written in the repository that it
> broke, with a date and a file reference. That is traceability, not modesty.

## What is actually running

| System                                                                | What it solves                                                                    | Notable detail                                                                                                                                                                                         |
| --------------------------------------------------------------------- | --------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Wallet Store**                                                      | Sells hand assembled DIY hardware wallets, no account, Pix or Bitcoin             | Watch only xpub, every address derived locally. Refuses to boot if the configured keys derive an unexpected address. Buyer data erased 72h after delivery.                                             |
| **ALFERES**                                                           | Personnel, leave, headcount and health for the Military Police of Espírito Santo  | Live at a unit of around 500 officers, about 20 concurrent users at peak. The unit registry already covers the whole state.                                                                             |
| **Jade DIY**                                                          | Turns off the shelf ESP32 boards into a working Blockstream Jade                  | Secure Boot signed firmware, a browser flasher, battery and touch logic for four different boards                                                                                                      |
| **Radar de Promo**                                                    | Deal hunting with nobody in the loop                                              | Rewrites each deal with an LLM, swaps in the affiliate link and posts to WhatsApp groups and a Telegram channel. When a group fills up, the next one is created and the invite already out points there |
| **[Tasmota IR](https://github.com/self-labs/tasmota-ir)**             | Learn and send IR from Home Assistant through any Tasmota board                   | Climate, media player, fan, light and cover entities built from learned keys. The emitter belongs to the appliance, set once, never typed per call                                                     |
| **[Tasmota for KinCony](https://github.com/self-labs/tasmota-kincony)** | Browser flasher for Tasmota builds that actually fit KinCony boards               | The official binaries either lose the W5500 Ethernet or leave the 16 relays unreachable. Plug in by USB-C and click Install, no Python, no esptool                                                      |
| **[cups](https://github.com/cateim/cups)**                            | An old USB printer turned into an AirPrint network printer                        | Multi arch image rebuilt every Sunday, published only when a package actually moved. ![pulls](https://img.shields.io/docker/pulls/cateim/cups?style=flat-square&labelColor=0b2a2f&color=22d3ee&label=pulls) |
| **[selflabs.org](https://selflabs.org)**                              | The lab's landing page                                                            | Astro, bilingual, Cloudflare Workers. Numbers on it come from the GitHub API, never typed by hand                                                                                                      |

Also public and maintained:
[ha-custom-branding](https://github.com/self-labs/ha-custom-branding) (white label
Home Assistant: tab, login screen, loading logo and PWA icon, surviving every image
update), [ai-usagebar-win](https://github.com/cateim/ai-usagebar-win) (Claude and
Codex quotas in the Windows tray, one `.exe`, no Rust toolchain),
[stirling-pdf](https://github.com/cateim/stirling-pdf) (a weekly MIT build of
Stirling-PDF without the 5 user cap) and [DIY](https://github.com/cateim/DIY)
(27 Portuguese guides on self-hosting and home automation, each with the
Portainer stack ready to paste).

## Upstream

Twenty pull requests accepted in nine repositories owned by eight different
people, plus write access to somebody else's project.

| Project                                                                                                           | What I sent                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| ----------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [Blockstream/Jade](https://github.com/Blockstream/Jade)                                                           | Six pull requests accepted and nine commits of mine in the official firmware of the Jade hardware wallet: swapped buttons on TTGO and USB JTAG on Waveshare S3 ([#260](https://github.com/Blockstream/Jade/pull/260)), Windows connectivity and USB detection ([#268](https://github.com/Blockstream/Jade/pull/268)), battery stability and power logic across T-Display, T-Display S3 and Waveshare S3 ([#270](https://github.com/Blockstream/Jade/pull/270), [#271](https://github.com/Blockstream/Jade/pull/271)), releasing the touch handles before deleting the i2c bus ([#307](https://github.com/Blockstream/Jade/pull/307)), and a user option to rotate the camera image 180 degrees ([#335](https://github.com/Blockstream/Jade/pull/335)), because two units of the same board with the same OV5640 module came out opposite ways up |
| [arendst/Tasmota](https://github.com/arendst/Tasmota)                                                             | Two pull requests merged in September 2026: the UART0 console on ESP32-S3, C3 and C6 is released when a template uses its pins ([#25047](https://github.com/arendst/Tasmota/pull/25047)), which kept the W5500 Ethernet of KinCony boards down unless a USB cable was plugged in, and raw IR frames can now choose their emitter ([#25062](https://github.com/arendst/Tasmota/pull/25062)), because on a board with several transmitters every learned raw code left through the first one while the command still answered `Done`                                                                                                                                                                                                                  |
| [oroderico/origo](https://github.com/oroderico/origo)                                                             | Write access to someone else's repository, where I fix bugs. It generates a BIP39 seed from human thrown dice, built after roughly 88 million dollars left Coldcard wallets through a build flag that lowered entropy unnoticed for five years. Plus a touch input fix merged into Oderico's Jade fork                                                                                                                                                                                                                                                                                                                                                                                                                              |
| [akitaonrails/ai-memory](https://github.com/akitaonrails/ai-memory)                                               | Native Windows hook command with no shell spawn, from around 735 ms to around 175 ms per tool call, hook merging instead of overwriting third party hooks, JSON output to kill debug spam                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| [akitaonrails/FrankMD](https://github.com/akitaonrails/FrankMD)                                                   | Multi arch amd64 and arm64 Docker publishing, tag normalisation, version in the About dialog                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| [albaintor/homeassistant_electrolux_status](https://github.com/albaintor/homeassistant_electrolux_status)         | Two fixes on appliance status handling                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| [RobHofmann/HomeAssistant-GreeClimateComponent](https://github.com/RobHofmann/HomeAssistant-GreeClimateComponent) | Brazilian Portuguese translation                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| [ayghri/i-have-adhd](https://github.com/ayghri/i-have-adhd)                                                       | Raised the SessionStart hook timeout so the always on mode is not silently dropped under load                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| [sucateirocripto/appsucateiro](https://github.com/sucateirocripto/appsucateiro)                                   | Calculator redesign with an interactive particle background                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |

Under review right now: Tasmota IR into the HACS default store
([hacs/default#11235](https://github.com/hacs/default/pull/11235)), the large link
preview card in [evolution-go#207](https://github.com/evolution-foundation/evolution-go/pull/207)
(the WhatsApp API behind Radar de Promo), two more Electrolux fixes
([#222](https://github.com/albaintor/homeassistant_electrolux_status/pull/222),
[#224](https://github.com/albaintor/homeassistant_electrolux_status/pull/224)) and
the HACS one click install for the Intelbras alarm integration
([#7](https://github.com/bobaoapae/guardian-api-intelbras/pull/7),
[#8](https://github.com/bobaoapae/guardian-api-intelbras/pull/8)).

Recurring theme: I run Windows and ARM64, which is exactly where most projects
quietly break.

<sub>Five of the six Jade pull requests show as closed rather than merged because
the maintainers land the changes through their own branch. The commits are in
the official `master` and in the shipped firmware.</sub>

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

- **Ethernet that only came up with a USB cable plugged in.** On a KinCony AG8
  the W5500 was detected, `ETH_START` fired, and the link never followed. Cause:
  with no USB host at boot, Tasmota falls back to a console on UART0, and on the
  ESP32-S3 that is GPIO43 and GPIO44, exactly the board's SPI MOSI and MISO.
  Fixed upstream by releasing the console instead of the pins
  ([arendst/Tasmota#25047](https://github.com/arendst/Tasmota/pull/25047)).
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

| Layer           |                                                                                                  |
| --------------- | ------------------------------------------------------------------------------------------------ |
| Firmware        | `C` `C++` `ESP-IDF` `Tasmota` `ESP32 / S3`                                                       |
| Web             | `TypeScript` `Node.js` `Fastify` `Astro` `Vanilla JS` `Python` `Django` `PHP` `C# / WPF` `Rust`  |
| Home automation | `Home Assistant` `custom integrations in Python` `ESPHome` `MQTT` `Node-RED`                     |
| Data            | `PostgreSQL` `SQLite` `Redis`                                                                    |
| Infra           | `Docker` `Portainer` `Cloudflare Workers` `Cloudflare Tunnel` `Caddy` `GitHub Actions` `Forgejo` |
| Hardware        | `Orange Pi 5` `Ampere VPS` `OpenWrt` `KinCony AG8` `KinCony KC868-A16v3`                         |

## Elsewhere

[selflabs.org](https://selflabs.org) · [store.selflabs.org](https://store.selflabs.org) · [@self-labs](https://github.com/self-labs) · [@gucateim](https://instagram.com/gucateim) · contato@selflabs.org
