# USBArmyKnife Web Installer

A web-based firmware installer for [USBArmyKnife](https://github.com/i-am-shodan/USBArmyKnife) —
a powerful ESP32-based USB attack/research tool.

The installer is powered by [ESP Web Tools](https://esphome.github.io/esp-web-tools/) and
published as a [GitHub Pages](https://pages.github.com/) site, so users can flash their
devices directly from a browser with no additional software required.

## Live Installer

👉 **[Open the installer](https://julesdg6.github.io/t-dongle-army-knife-installer/)**

## Supported Devices

| Device | Chip |
|--------|------|
| LILYGO T-Dongle S3 | ESP32-S3 |
| Waveshare ESP32-S3 LCD 1.47" | ESP32-S3 |
| Waveshare ESP32-S3 GEEK | ESP32-S3 |
| Generic ESP32-S3 | ESP32-S3 |
| Generic ESP32-S2 | ESP32-S2 |
| Evil Crow Cable Wind | ESP32-S3 |
| LILYGO T-Watch S3 | ESP32-S3 |
| M5Stack Atom S3U | ESP32-S3 |

## Requirements

- **Google Chrome** or **Microsoft Edge** (v89+) — the Web Serial API is required
- A **USB data cable** (not a charge-only cable)
- The device plugged in via USB before clicking Install

## How It Works

1. A GitHub Actions workflow runs daily (and on every push to `main`)
2. It downloads the [latest USBArmyKnife release](https://github.com/i-am-shodan/USBArmyKnife/releases) binaries
3. It generates an [ESP Web Tools `manifest.json`](https://esphome.github.io/esp-web-tools/) for each supported device
4. The complete site is deployed to GitHub Pages

## Enable GitHub Pages (first-time setup)

1. Go to **Settings → Pages** in this repository
2. Under **Source**, select **GitHub Actions**
3. Trigger the workflow manually via **Actions → Update Firmware & Deploy → Run workflow**

## Development

The installer is a single static `index.html` file. Firmware binaries and manifests
are generated at CI time and are **not** committed to the repository.

### Workflow

`.github/workflows/update-firmware.yml` — Downloads USBArmyKnife firmware zips,
extracts the `.bin` files, generates `manifest.json` for each device, and deploys
the whole site to GitHub Pages.

## Credits

- [USBArmyKnife](https://github.com/i-am-shodan/USBArmyKnife) by [@i-am-shodan](https://github.com/i-am-shodan)
- [ESP Web Tools](https://esphome.github.io/esp-web-tools/) by the ESPHome project
- Inspired by [squeezelite-esp32-install](https://github.com/balloob/squeezelite-esp32-install)
