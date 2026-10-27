# Quick start

[README](../README.md) · [日本語](QUICKSTART.ja.md)

## 1. Install and set up

Download `VerseTrade-Relay.exe` from [Releases](https://github.com/nakacch/VerseTrade-Relay/releases)
and double-click it. Required support files and license notices are prepared
automatically in your user data folder. Microsoft Visual C++ x64 runtime must already be installed.

In welcome setup, choose the environment you play in (**LIVE** or **PTU**).
Use **Find standard game installations** or **Browse game folder** to find your
installed game's translation files. Set **LIVE global.ini** or **PTU global.ini**
to the `global.ini` for the language you use in that installation. For example,
a localization file is under `<game installation>/data/Localization/<language>/global.ini`.
Leave the other environment empty if you do not use it.

The app uses entries in this translation file to match localized place and item
names to UEX, and automatically follows changes to the file while running.
The app interface language and game/OCR language are separate settings.
ONNX is the recommended OCR option. Select models suitable for your game language,
then use **download and verify** in the app's welcome setup or **Settings → OCR**.
ONNX support is included in the EXE, and the app downloads your selected models
for you. You can reopen first-run setup from Settings.

In Settings, refresh the UEX commodity and terminal catalog. Your **UEX user secret**
is required to submit reports to UEX. Enter it in **Settings → UEX connection**
when you plan to submit reports. It is not needed to download the public
commodity and terminal catalog. Set the **watch folder**
to the folder where the game saves screenshots, confirm the environment and
optional game version, then save settings. Saving does not
download models. Model downloads and catalog refreshes are separate operations.

## 2. Read and review

1. Check that the app is watching your screenshot folder and that LIVE/PTU matches
   the environment you are playing in.
2. On the **in-game trading terminal**, set the **location field on the left** to
   the station name.
3. Take screenshots while scrolling through the **commodity list on the right of
   that same terminal**. With **Automatically read captures** enabled, the app
   reads these screenshots continuously as they appear in the watched folder.
   Normally, no terminal selection in the app or manual image import is needed.
4. Select a table cell to inspect its source image, crop, OCR observations and
   candidate values. Correct the commodity, UEX direction, price per SCU, stock SCU,
   inventory status and cargo sizes as necessary. Status runs from 1 (empty) to 7 (full).
5. Review uncertain readings, pending items and UEX differences. The review filter
   only changes displayed rows; it does not remove hidden rows from submission.
6. Use image enlargement for unreadable details. Changing the viewed image does
   not automatically change the image attached to a report. Check attachments explicitly.

A pencil marker identifies a value changed by the reporter, including adopting a
different OCR candidate or observation. Hover over the marker to inspect the reason
and the recorded before/after values. Confirming an unchanged value does not create
a reporter-change marker. Reverting to the original value removes that change's marker.

Reports automatically include English explanations of applicable reporter changes
and recorded dictionary conversions. Quoted OCR/dictionary text keeps its original
language. These explanations are added alongside your own notes. An annotated item
may be sent as an individual report, so more annotated items can mean more requests.

OCR confidence text colors and UEX difference borders represent different checks.
Low OCR confidence changes the value's text color; UEX price/stock differences
are shown with colored borders and difference values.
Manual corrections do not make the original OCR observation more confident.
Re-recognition can update machine readings while preserving manual edits; verify
the resulting draft. Reset/clear operations can remove the current work.

You can also use **Select images** or drag and drop existing screenshots onto the
app. Folder watching detects new files, so use these options for older screenshots.
If a new image needs its destination confirmed, follow the on-screen prompt.

## 3. Test and submit

Check the terminal, environment, direction, game version, report values and supporting
image. **A screenshot is required for every report, including test submissions;
attachment cannot be disabled.** The app attaches the original capture converted
to JPEG, not the image corrected for OCR. Missing or changed evidence blocks submission.
Use input validation to resolve blocking errors. Check the selected
submission mode: the default test-first mode requires a successful test of the
same contents before production. Changes to tested values or generated report
explanations require another test.
Other modes follow the controls and confirmation shown in the app.

UEX requests follow the saved game language, independently of the app interface
language. Automatically generated explanations remain in English.

Test submission contacts UEX when run from the app; it is separate from production
reporting. Confirm production only after reviewing the summary. Keep the app open
until the result is known. PTU drafts are not submitted as LIVE reports.

If a production request has an **unknown** result, do not submit the same report
again immediately. In **History**, filter unknown entries, refresh status and use
reconciliation. Supply all report IDs for the group or confirm that the entire
group was not accepted before recovery. A partial result is not proof of rejection.

## 4. Settings and history

Settings has seven groups of tabs: appearance/images, UEX comparison, submission,
OCR, monitoring/language, app updates and UEX connection. Resetting a page affects
that page's unsaved edits; all-settings reset is broader. Undo reset, Save and the
unsaved-changes prompt let you choose what to keep. Themes preview immediately.

History is a separate page with all/test/production/unknown filters and report
status tools. Preserve history during updates, especially unresolved submissions.

## 5. Update, backup and uninstall

Close the app before updating. Back up `%APPDATA%\VerseTrade-Relay\`, download the
new EXE, verify its checksum and save it into a new folder. Launch the
new EXE. Existing user data is separate from the executable. The current preview
does not configure an automatic update feed; check Releases manually.

To verify the executable in PowerShell:

```powershell
Get-FileHash .\VerseTrade-Relay.exe -Algorithm SHA256
```

Compare it with the matching `.exe.sha256` asset from the same release.
Checksums detect differing bytes; the app is unsigned.

Your UEX user secret is protected by **Windows data protection**.
Backups contain private history, paths and protected credentials: keep them private.

To uninstall:

1. Close VerseTrade Relay.
2. Delete **`VerseTrade-Relay.exe`** from the folder where you saved it.
3. In File Explorer, delete **`%APPDATA%\VerseTrade-Relay\`** to remove settings,
   submission history and downloaded models. Back up any data you want to keep first.
4. To also remove cached image copies and support files, delete
   **`%LOCALAPPDATA%\VerseTrade-Relay\`**.

## Troubleshooting

| Symptom | Action |
| --- | --- |
| Missing OCR models | Choose your engine/language/model and download/verify in welcome setup or OCR settings. |
| Required support files fail to load | Install Microsoft's x64 Visual C++ runtime; clear an obsolete explicit DLL setting, close and restart. Check cache write access. |
| Missing Japanese text | Check that Japanese-capable Windows UI fonts are installed. Fonts are not bundled. |
| Incorrect names/locations | Check the selected localization, environment, catalog and terminal; inspect observations and candidates. |
| Submit is disabled | Resolve validation errors, pending items, missing credentials or a missing/stale successful test; inspect the shown reason. |
| Unknown production result | Reconcile in History before attempting a resend. |
| App closes unexpectedly | Check `%APPDATA%\VerseTrade-Relay\logs\versetrade-relay.log` and report the version and reproduction steps. |

Report issues in [VerseTrade-Relay Issues](https://github.com/nakacch/VerseTrade-Relay/issues).
Redact secrets and personal information from any logs or screenshots you share.
