## Gustavo Cateim

I run [**Self-Labs**](https://github.com/self-labs), a one person engineering lab
in Vitória, Espírito Santo, Brazil. Firmware, web systems and infrastructure that
run on my own hardware, deployed by webhook, with the private key kept outside
the server.

I like problems where the cheap solution is also the correct one, and I write
down what broke in production instead of quietly fixing it.

### What I build

- **Bitcoin hardware wallets.** [jade-diy](https://github.com/cateim/jade-diy)
  turns off the shelf ESP32 boards into a working Blockstream Jade. Upstream
  contributions merged into [Blockstream/Jade](https://github.com/Blockstream/Jade)
  (#268, #270, #271).
- **Systems for the public sector.** Personnel, leave and health management for a
  military police unit, around 500 people inside, running in production.
- **Self-hosted infrastructure.** Docker on an Orange Pi 5 and an Ampere VPS,
  Portainer stacks pulled straight from git, Cloudflare Tunnel, native ARM64 CI.
- **Low cost fixes for real problems.** [DIY](https://github.com/cateim/DIY) and
  [cups](https://github.com/cateim/cups): the latest OpenPrinting CUPS built for
  Debian and Ubuntu, because the distro packages were years behind.

### Stack

`C / ESP-IDF` `TypeScript` `Node.js` `Astro` `Python` `PHP` `C#` `PostgreSQL`
`Docker` `Portainer` `Cloudflare Workers` `GitHub Actions`

### How everything ships

Push to `master`, CI runs the tests, a webhook redeploys the stack. No manual
step, no SSH at two in the morning. Same path in every project.

### Elsewhere

[selflabs.org](https://selflabs.org) · [store.selflabs.org](https://store.selflabs.org) · [@gucateim](https://instagram.com/gucateim)
