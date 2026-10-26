# VerseTrade Relay

![VerseTrade Relay — For Datarunners](assets/branding/versetrade-relay-banner.png)

A Windows desktop app for reading **Star Citizen trading-terminal screenshots**,
reviewing the results, and reporting commodity prices and stock to **UEX**.

[日本語](README.ja.md) · [Download](https://github.com/nakacch/VerseTrade-Relay/releases) ·
[Quick start](docs/QUICKSTART.md) · [Report an issue](https://github.com/nakacch/VerseTrade-Relay/issues)

## Features

- Watch your screenshot folder and automatically read new captures as you take them.
  You can also import screenshots or drag and drop them onto the app.
- Run OCR locally using models selected for your game language.
- Automatically match localized place and item names to UEX using your game's
  translation file, `global.ini`, and follow changes to that file automatically.
- Check source images and field crops while editing commodities, prices, stock,
  inventory status and cargo sizes.
- Spot low OCR confidence through text colors and differences from UEX reference
  prices/stock through colored borders and difference values.
- Test reports before production submission and keep submission history.
- English/Japanese interface; System, Light, Dark and Slate themes.

## Download and requirements

1. Open [Releases](https://github.com/nakacch/VerseTrade-Relay/releases).
2. Download **`VerseTrade-Relay.exe`** from **Assets**.
3. Save it in a folder of your choice and double-click it to start.

GitHub's **Source code** archives contain documentation and artwork only. Use the release
EXE for the app. Releases marked **Pre-release** are preview builds.

Requirements: 64-bit Windows 10/11, an OpenGL-capable graphics driver,
and the [Microsoft Visual C++ x64 Redistributable](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist).
The app is unsigned. Internet access is required for model downloads and UEX services.

## Single executable

Download and run one EXE. Required support files are prepared automatically in
your user data folder. **OCR models are not bundled**:
select and download them for your language in the welcome page or **Settings → OCR**.

The app is designed primarily for **ONNX-based OCR**, with speed and recognition
accuracy in mind. Required ONNX support is included in the EXE; only your selected
models can be downloaded directly inside the app, from welcome setup or **Settings → OCR**.
Tesseract is an optional alternative and requires a
separate installation. Speed and accuracy depend on the model, language and image.

Read the manuals here on GitHub. Third-party license notices are included inside
the EXE and saved in the app cache at startup. An optional `.exe.sha256` download
lets you verify the executable.

## First run

1. In welcome setup, choose LIVE or PTU and select that installation's translation
   file (`global.ini`) for your game language, then check the OCR language.
2. In the app's welcome setup or **Settings → OCR**, select your models and use
   **download and verify**.
3. Refresh the commodity/terminal catalog in **Settings → UEX connection**.
4. Set the watch folder to the folder where your game saves screenshots, confirm
   LIVE/PTU, and save settings. Leave **Automatically read captures** enabled.
5. On the **in-game trading terminal**, set the **location field on the left** to
   the station name. Take screenshots while scrolling through the **commodity list
   on the right**, staying at the same terminal.
6. The app automatically reads the new screenshots from the watched folder.
   Normally, you do not need to select a terminal in the app or import images
   manually. Check the results against the images and correct them as needed.
7. Check the submission mode and attachment setting. In the default test-first
   mode, pass a test before confirming production submission.

See the [quick start](docs/QUICKSTART.md) for editing, recovery and updates.

## Data and privacy

OCR runs locally. Network access is used for model downloads, UEX catalog/reference
queries, requested updates and UEX report/status requests. Screenshot attachments,
when enabled, send the original screenshot to UEX during submission.

| Data | Default location |
| --- | --- |
| Settings, history and logs | `%APPDATA%\VerseTrade-Relay\` |
| Downloaded ONNX models | `%APPDATA%\VerseTrade-Relay\ocr-models\` |
| Image copies and support files | `%LOCALAPPDATA%\VerseTrade-Relay\cache\` |

The UEX user secret is encrypted for your Windows user account.
Working image copies can remain in the cache. Replacing/deleting the EXE does not
remove these folders. See the manual before resetting app data.

## Limitations

- OCR can misread values. Check the terminal, environment, direction and every
  value before sending; ambiguous readings need manual review.
- A production result may be unknown after connection failure. Reconcile it in
  history before retrying. Unknown results are not automatically resent.
- The app does not automate in-game actions.
- The initial release is a packaging preview. Live UEX submission and acceptance
  across all languages and Windows environments are not claimed as verified.

## Issues and feature requests

Use [this repository's Issues](https://github.com/nakacch/VerseTrade-Relay/issues).
English and Japanese are welcome. Include app/Windows version, UI/game language,
OCR engine/model, reproduction steps and expected/actual results. Remove secrets,
personal paths and identifying screenshot details. Do not upload unchanged
settings files or submission-history databases.

## Distribution and acknowledgments

This repository contains user documentation and release metadata. Application
source is maintained separately and is not published here. The application is
not offered under an open-source license. Third-party components retain their
own licenses; see [notices](docs/THIRD_PARTY.md). Full license texts are saved as
`cache\bundled\<payload-hash>\THIRD-PARTY-NOTICES.txt` under the local app data folder.
Windows fonts, game screenshots and localization files are not redistributed.
This is an independent community tool, not an official Star Citizen or UEX product.
