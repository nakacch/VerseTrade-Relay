# Third-party notices

Third-party components retain their own copyright and license terms.
The application itself is not offered under an open-source license.

Full notices are included in `VerseTrade-Relay.exe` and saved when it starts:

```text
%LOCALAPPDATA%\VerseTrade-Relay\cache\bundled\<payload-hash>\THIRD-PARTY-NOTICES.txt
```

The hash-named folder identifies the installed support files. Several folders
can exist after updates; use the one written by the version you are running.

| Component | License / upstream |
| --- | --- |
| egui / eframe | MIT OR Apache-2.0 — https://github.com/emilk/egui |
| ort | MIT OR Apache-2.0 — https://github.com/pykeio/ort |
| ONNX Runtime 1.30.0 | MIT and accompanying third-party notices — https://github.com/microsoft/onnxruntime |
| rapidocr-core | Apache-2.0 — https://github.com/White-NX/rapidocr-rs |
| Default interface fonts | Ubuntu Font Licence, SIL Open Font License, MIT; individual notices included |
| Other dependencies and compiler support | Full notices are included in the file above |

OCR models are downloaded separately and are not included in the EXE. Their
upstream terms apply. See [model license information](https://rapidai.github.io/RapidOCRDocs/main/en/model_licenses/)
and the selected model's source.

Japanese interface fonts are loaded from fonts already installed on the user's
PC. Windows fonts, game screenshots and game localization files are not distributed.
Product names identify integrations and do not imply endorsement.
