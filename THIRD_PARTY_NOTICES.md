# Third-Party Notices

This document records the third-party components actually shipped in the Hardware Debug Copilot v0.1.0 Beta Windows x64 release. It is an inventory and release-readiness record; the complete license and attribution files are included in the binary archive under `licenses/`.

Hardware Debug Copilot's original application code, diagnostic rules, and analysis logic remain proprietary and closed source. The third-party licenses listed here apply only to their respective components.

## Reviewed release

- Archive: `Hardware-Debug-Copilot-v0.1-gui-win64.zip`
- Size: 45,083,257 bytes (42.99 MiB)
- SHA-256: `2991EE129C7D06FA6BA294D4CD02FDF961A3ECDA9309636514672ED76FC92EC6`
- Review date: 2026-09-18

## Shipped components

| Component | Version / scope | Distribution basis | License material in the archive |
|---|---|---|---|
| CPython | 3.13.14 interpreter from python-build-standalone 20260728 and selected standard-library modules | Python Software Foundation license family and incorporated notices | `licenses/CPython/LICENSE.txt` |
| CPython runtime dependencies | bzip2 1.0.8, Expat 2.8.1, libffi 3.4.6 (`libffi-8.dll`), liblzma/XZ Utils 6.0.0, libmpdec 4.0.0, and Unicode Character Database 15.1.0 data | Component-specific permissive upstream licenses | `licenses/CPython-Dependencies/` |
| NumPy | 2.5.3 | NumPy wheel license bundle | `licenses/NumPy/` |
| OpenBLAS and LAPACK | OpenBLAS 0.3.34.106.0 plus LAPACK as identified by the NumPy wheel | Bundled through NumPy's Windows binary distribution | Included verbatim in `licenses/NumPy/LICENSE.txt` and the retained NumPy license tree |
| charset-normalizer | 3.5.1 compiled character-detection modules | MIT License | `licenses/charset-normalizer/LICENSE.txt` |
| PySide6 | 6.11.2; QtCore, QtGui, and QtWidgets Python bindings | LGPL-3.0-only distribution option | `licenses/PySide6-Shiboken6/` |
| Shiboken6 | 6.11.2 runtime | LGPL-3.0-only distribution option | `licenses/PySide6-Shiboken6/` |
| Qt | 6.11.2; Core, GUI, Widgets, Windows platform plugin, and software OpenGL fallback | LGPL-3.0-only; Qt libraries remain separate replaceable DLL/PYD files | `licenses/Qt/` |
| Qt embedded third-party code | Components actually used by the shipped Qt Core/GUI/Windows runtime, including libpng 1.6.58; Mesa llvmpipe is shipped as `opengl32sw.dll` | Component-specific upstream licenses | Exact `qt_attribution.json` records and verbatim license texts under `licenses/Qt/` |
| PyInstaller | 6.22.3 bootloader/runtime | GPLv2-or-later with the PyInstaller bootloader exception and separately identified runtime-hook terms | `licenses/PyInstaller/COPYING.txt` |
| Noto Sans CJK SC / Noto Sans SC | Version 2.04, build-time font; document-specific subsets only | SIL Open Font License 1.1 | `licenses/Noto-Sans-CJK-SC/OFL.txt` |
| Microsoft Visual C++ Runtime and Universal CRT | App-local VC v14 and UCRT runtime files required by the frozen application | Microsoft runtime redistribution terms | `licenses/Microsoft-Runtime/REDISTRIBUTION-NOTICE.txt` with exact shipped families and official references |

The complete NumPy license tree is retained because the binary wheel contains additional bundled numerical and runtime code. The Qt directory retains the exact upstream attribution metadata and all license texts needed by the selected Qt Core/GUI/Windows components.

## Qt / PySide6 distribution details

The release uses the LGPL-3.0-only option for PySide6, Shiboken6, and the shipped Qt libraries. The final payload contains only:

- `Qt6Core.dll`
- `Qt6Gui.dll`
- `Qt6Widgets.dll`
- `QtCore.pyd`, `QtGui.pyd`, and `QtWidgets.pyd`
- `plugins/platforms/qwindows.dll`
- `opengl32sw.dll` (Mesa llvmpipe software OpenGL fallback)

These files are dynamically loaded, remain separate and replaceable, and are not modified by Hardware Debug Copilot. The archive includes the LGPL 3.0 and incorporated GPL 3.0 texts, exact third-party attribution records, and references to the exact corresponding source archives:

- PySide6 6.11.2 source SHA-256: `C0FDD62B91A1D36D5EE2E1FB71050A32FBC93FCDEEF0FDCB41D29AFAAF00D9B5`
- Qt Base 6.11.2 source SHA-256: `8F8C16703A8170B235361AACDF0EC97D2445AE4E3E3D127EB1576F498269EF79`

Qt Network, Qt SVG, Qt OpenGL module DLLs, optional image-format plugins, TLS plugins, QML/Quick, WebEngine, Multimedia, and Qt PDF are not shipped.

## User-guide font

The Chinese PDF no longer contains Microsoft YaHei. It embeds only document-specific subsets named `HDCNotoSansSC-Regular` and `HDCNotoSansSC-Bold`, generated from Noto Sans SC Version 2.04 under SIL Open Font License 1.1. The archive contains no `.ttf`, `.otf`, `.ttc`, variable-font source, or other standalone font program.

## Confirmed absent from the final payload

- OpenSSL / `libssl` / `libcrypto`
- Qt Network and Qt SVG
- Microsoft YaHei
- ReportLab and fontTools runtimes
- pytest and development tooling
- Python application source files, tests, build scripts, Git metadata, and font source files

This document is not legal advice. The publisher remains responsible for ongoing compliance if the binary composition or distribution method changes.
