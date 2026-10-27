<p align="center">
  <img src="ui/icon.png" width="104" alt="Console Studio logo">
</p>

<h1 align="center">Console Studio</h1>
<p align="center"><strong>Your console. Your next step.</strong></p>
<p align="center">A desktop companion for exploring console homebrew and preparing supported USB and SD media.</p>
<p align="center">Windows x64 · macOS Apple Silicon & Intel · English / Deutsch</p>

---

Console Studio brings compatibility information, project updates, original sources and media preparation into one minimal desktop app. Explore **27 console families** across Xbox, PlayStation and Nintendo, review the risks, and prepare files using **12 supported console profiles**.

The interface uses black, gray and white with subtle gold accents, including a short animated logo introduction. English is the default; German is available from the language selector.

> **Preview release — v1.1.1.** Console Studio prepares files and explains the remaining steps. It does not provide a universal, plug-and-play jailbreak for every console. Read the exact model and firmware requirements before proceeding.

## Features

- **Console catalog:** model and firmware requirements, risks, hardware alternatives, next steps and original project links.
- **Automatic package downloads:** supported profiles query their configured original release sources when you prepare a package.
- **Wii U automation:** downloads and assembles Aroma, EnvironmentLoader, CustomRPXLoader, PayloadLoaderPayload and the NAND dumper.
- **Project news:** release and commit updates from configured GitHub projects, plus GitLab updates for the Switch 2 research project. Cached results are marked when a live query fails.
- **USB and SD preparation:** optional FAT32/MBR formatting, explicit device selection and confirmation, and full SHA-256 read-back verification.
- **Folder export:** prepare a package for manual transfer without formatting a device.
- **Included instructions:** every prepared package contains an HTML guide with risks, sources and the next steps on the console.
- **English and German:** saved language preference, translated catalog content and application dialogs. Third-party release notes and operating-system diagnostics retain their original language.
- **Minimal startup animation:** approximately two seconds, skippable with **Esc**. Respects reduced-motion preferences and does not replay when changing languages.
- **Local operation:** no account, telemetry or upload of your console information.

## Supported preparation profiles

A profile's output may be an installer, a payload or a set of base files. The additional requirements below still apply.

| Console | Prepared files | Additional requirements |
| --- | --- | --- |
| Xbox 360 | Rock Band Blitz and the current PeerPressure SoftmodInstaller | Supported motherboard, suitable HDD, console backup and on-console installation. Corona and Winchester are blocked in this profile. |
| PlayStation 2 | FreeMcBoot installer | Compatible console and memory card, plus an existing ELF entry point such as a suitable FreeDVDBoot setup. |
| PlayStation 3 | A selected PUP at `PS3/UPDATE/PS3UPDAT.PUP` | Manual firmware selection and an independently published SHA-256. Exact CECH model and HEN/CFW requirements must be checked. |
| PlayStation 4 | GoldHEN payload | This profile requires firmware **11.00**, a compatible PPPwn host/stage2 and the Ethernet entry procedure. |
| PSP | ARK-4 live-CFW files | Firmware **6.61**, existing compatible storage and running ARK Loader on the PSP. PSP storage is not formatted by the app. |
| GameCube | Swiss as `ipl.dol` | An already installed PicoBoot and a compatible SD adapter. |
| Wii | HackMii `boot.elf` | The model-specific BlueBomb host/Bluetooth procedure. |
| Wii mini | HackMii `boot.elf` | The Wii mini BlueBomb procedure and its specific backup/recovery limitations. |
| Wii U | Aroma, base loaders and NAND dumper | Appropriate SD media, browser entry, NAND backup and PayloadLoader/Aroma setup. Existing CBHC/Indexiine installations need special preparation. |
| Nintendo Switch | Atmosphère and Hekate | Confirmed **unpatched V1**, RCM entry, payload sender, backups and manual emuMMC/launch configuration. |
| Nintendo 3DS / 2DS | Luma3DS base files | Model-, region- and firmware-specific first-install steps, additional exploit files and finalization from the guide. |
| Nintendo DSi | TWiLight Menu++ base files | The appropriate Memory Pit variant and camera entry procedure. Unlaunch is a separate decision. |

The catalog also provides information for original Xbox, Xbox One and Series, PS1, PS5, PS Vita/PSTV, Switch 2, DS/DS Lite, NES/Famicom, SNES/Super Famicom, Nintendo 64, Game Boy/Color, Game Boy Advance, Virtual Boy, and NES/SNES Classic Mini.

**An information page does not imply an automated installation profile.** Hardware modifications, raw memory-card images, FATX writes, browser/network exploits and payload injection are not executed by Console Studio.

## Download and install

Choose the matching archive from the project's published release assets:

| Platform | Archive | Start |
| --- | --- | --- |
| Windows x64 | `Console-Studio-Windows.zip` | Fully extract it, then open `ConsoleStudio.exe`. Keep all supplied runtime files together. |
| macOS, Apple Silicon | `Console-Studio-Mac-Apple-Silicon.zip` | Extract it and move `Console Studio.app` into Applications. |
| macOS, Intel | `Console-Studio-Mac-Intel.zip` | Extract it and move `Console Studio.app` into Applications. |

The Mac builds require **macOS 13 or later**. Packaged apps do not require a separate installation of Node.js or Python. An internet connection is needed for package downloads and current project updates.

### Signing status

Mac builds are **ad-hoc signed, not Apple-notarized**. Windows builds do not carry an Authenticode publisher certificate. Operating systems may show a security prompt. Only approve a download you trust; do not disable system-wide protections.

If macOS reports a damaged app, replace the old copy with a freshly downloaded, fully extracted archive. To help diagnose a remaining signature issue, run:

```bash
codesign --verify --deep --strict --verbose=2 "/Applications/Console Studio.app"
```

Include the output in a bug report. Do not modify files inside a signed app bundle.

## Prepare your media

1. Select the console and review **Overview & risks**, compatibility notes and original sources.
2. Open **Prepare media**, select your model and enter the actual firmware version.
3. Confirm that you have checked compatibility, read the risks and made the required backups. Explicitly allow pre-release software where required.
4. Click **Download & verify packages**. This stage prepares files locally; it does not write to your USB or SD device.
5. Review the package versions and checksums. Export a package folder, or use **Find USB / SD** to select a target device.
6. Choose an existing FAT32 volume or explicitly request formatting. Confirm the exact device before writing.
7. Wait for copying and read-back verification to finish, then safely eject through your operating system.
8. Follow the on-console steps in the app or `Console-Studio-Anleitung.html` on the prepared media. Its contents use the selected language.

## Formatting and verification

> Formatting permanently erases every partition and file on the selected device. Check its name, capacity and device identifier before confirming.

Automatic FAT32/MBR formatting is limited to devices up to **32 GiB**. Larger existing FAT32 volumes can be used without formatting. PSP storage is never formatted by the app. Some SD readers may not expose a supported external device; a USB reader may be needed.

The app filters protected devices, checks device identity again before operations, rejects unsafe archive paths and does not overwrite existing target files. It reads copied files back and compares their SHA-256 hashes. These checks reduce mistakes but do not replace backups or confirm that a console installation will succeed.

A locally calculated hash confirms file consistency. It is **not a publisher signature**. Where a source provides a supported independent digest, the download is also checked against it; otherwise the package review states that no separate publisher checksum is available.

## Updates and current limitations

- Package versions are queried when you prepare supported profiles. This does **not** install application updates or silently change compatibility rules.
- Some resources are intentionally fixed packages, including the Xbox 360 demo and Wii/HackMii installer. A profile may stop if a project changes its archive naming or layout.
- PS3 firmware selection and the optional Xbox 360 17559 system-update ZIP remain manual.
- 3DS and DSi profiles provide base files, not every variant-specific first-install exploit.
- A new release or research announcement does not automatically make a firmware version supported. Consult the linked primary source.
- Public API rate limits, unavailable hosts and offline operation may prevent downloads or live news retrieval. The app does not silently substitute an unverified mirror.
- Information-only platforms may provide source links rather than a machine-readable news feed.

The bundled compatibility catalog was reviewed on **October 27, 2026**. Its date is separate from live project-news retrieval dates.

## Privacy and local storage

Console Studio has no telemetry and does not upload selected local files or console identifiers. It connects to configured project hosts for news and downloads; those hosts receive ordinary network requests.

Downloaded archives and prepared packages are stored in the application's local user-data directory under `work`. They can occupy several gigabytes. Close the app before removing old working folders. The selected language and cached project news are stored locally.

## Development

The app uses Electron with a sandboxed renderer, a limited preload bridge and a separate package-preparation worker. Development uses **Node.js 24**; Python 3 is used by the localization and Mac ZIP packaging scripts.

From the repository root:

```bash
npm ci
npm start
```

Run the automated core tests:

```bash
npm test
```

Regenerate the English renderer after changing the German UI source or translation dictionary:

```bash
python3 scripts/build-locales.py
```

Relevant files:

| Path | Purpose |
| --- | --- |
| `main.cjs`, `preload.cjs` | Desktop lifecycle and restricted renderer-to-main communication |
| `ui/` | Interface, styles, localization bootstrap and startup animation |
| `data/catalog.json`, `data/catalog.en.json` | German and English console information |
| `data/translations.en.json` | UI and application-message translations |
| `lib/profiles.cjs` | Compatibility gates, download recipes and target layouts |
| `lib/network.cjs`, `lib/archive.cjs` | Allowed download sources, checksums and archive extraction |
| `lib/disks.cjs`, `lib/media.cjs` | Device checks, formatting and verified copying |
| `tests/` | Core tests and Electron UI smoke scripts |

### Build packages

```bash
node build.mjs
```

The build script targets Windows x64, macOS arm64 and macOS x64, with output in the sibling `builds` directory. It does not perform Developer ID signing or notarization.

For a Mac release, finish all bundle modifications, sign the app, then package it while preserving every signed resource and symlink:

```bash
python3 scripts/package-mac.py \
  "../builds/Console Studio-darwin-arm64/Console Studio.app" \
  "Console-Studio-Mac-Apple-Silicon.zip" \
  --docs .
```

Repeat with the x64 bundle for Intel Macs. The script checks sealed resource hashes and signed symlinks inside the resulting ZIP. This is not a substitute for Apple's native `codesign` verification, Gatekeeper assessment or a real Mac launch test.

### Validation status

The existing core suite contains **41 passing automated tests**. UI checks have run in Electron under Linux, including language selection, the Wii U preparation flow and startup-animation dismissal. Wii U package assembly was checked with the five original release archives; several other profiles were also checked against actual project archives.

**Not hardware-tested in the build environment:** Windows/macOS startup, native privilege dialogs, physical FAT32 formatting, media preparation on those operating systems, or installation on consoles. See [TESTS.txt](TESTS.txt) for the recorded test scope.

## Reporting issues and contributing

For a bug report, include the app version, operating system and architecture, console model, firmware, selected profile, exact error and steps to reproduce. For media issues, include capacity and filesystem. Remove serial numbers, keys and other private data before sharing logs or screenshots. Never attach NAND dumps, EEPROM backups, CPU keys or account credentials.

When proposing a new profile, include original project sources, explicit model/firmware requirements, expected archive contents and target paths. Report package-only testing separately from hardware testing. Translations, documentation corrections and compatibility clarifications are welcome.

## Credits and license

Console Studio brings together information and downloads from independent homebrew projects. Credit for each exploit, installer and payload belongs to its original authors. Original project links are included throughout the app and its generated guides.

Console Studio's own source code is available under the [MIT License](LICENSE). Electron, dependencies and downloaded third-party packages retain their respective licenses. The application's license does not relicense their work.

Console Studio is an independent project and is not affiliated with or endorsed by Microsoft, Sony or Nintendo. Console names and trademarks belong to their respective owners.
