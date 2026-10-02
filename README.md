# Minty PDF

A Windows PDF reader and editor with document tabs, in-place editing, forms, local OCR and certificate signing.

**[Download the latest release](https://github.com/dobromirdikov/minty-pdf-releases/releases/latest)**

This repository provides signed Windows releases and release notes. Application source and CI builds are maintained in a separate private repository.

## Download and install

Open the latest release and choose a package:

| File | Use |
| --- | --- |
| `MintyPDF-Setup-<version>.exe` | Signed installer with Start menu shortcuts and PDF app registration. |
| `MintyPdf-<version>-win-x64.zip` | Portable package. Extract the entire archive, then run `MintyPdf.exe` inside the extracted application folder. |
| `SHA256SUMS.txt` | SHA-256 checksums for the installer and portable archive. |

Requires **Windows 10 or later, x64**. Both packages include the .NET desktop runtime. Local OCR also requires the [Microsoft Visual C++ v14 Redistributable for x64](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170), which is not bundled. USB certificate tokens need their manufacturer's installed driver.

Setup installs for your Windows account without an administrator prompt. Save your work and close Minty PDF before upgrading. The upgrade keeps your documents, settings and recovery files.

To compare a downloaded file with `SHA256SUMS.txt`, run this in PowerShell, replacing the filename with your download:

```powershell
Get-FileHash -Algorithm SHA256 -LiteralPath '.\MintyPDF-Setup-<version>.exe'
```

## What you can do

- Read with continuous scrolling, search, selectable text and copying. Open multiple PDFs in draggable tabs and reopen up to ten recent files.
- Switch to Edit to change text in place, fill standard PDF forms, load compatible fonts, move supported objects and add text, images, shapes or highlights.
- Create PDFs, add blank pages, rotate, rearrange, delete or extract pages, print documents and export pages as PNG.
- Import selected PDF pages from thumbnail previews, or add pages from DOCX, TXT, PNG, JPEG, BMP and TIFF files. Imported pages appear after the current page.
- Run English or Bulgarian OCR on the current page or entire document. Recognized text becomes editable objects; remaining artwork becomes images. OCR runs only when requested.
- Save password-protected or unlocked copies, apply permanent redactions, and sign or check PDF certificate signatures.
- Use light or dark mode and collapse the navigation and properties panels.

## First steps

1. Open a PDF or drop PDF files into the window. Existing documents start in **Read** mode, where you can select and copy text.
2. Use the top-center **Read/Edit** switch to enable editing and form filling. New PDFs start ready for editing.
3. Use **Pages > Import pages from files** to add content. PDF imports show thumbnails and page-selection options.
4. For scans, switch to Edit and choose **Scan > Convert this page** or **Convert entire document**. Review recognized text and fonts before saving.
5. Use **Save** or **Save as** to write your changes. `Ctrl+O` opens, `Ctrl+S` saves, `Ctrl+P` prints and `Ctrl+W` closes the current tab.

## Signing and verification

In Edit mode, choose **Security > Sign with certificate**, draw the signature box on a page, choose your certificate, enter a reason and name the signed copy. Complete any local PIN prompt. Minty PDF saves and opens the signed copy; signed documents are protected from editing.

**Security > Check signatures** reports signed-byte integrity, whether the signature covers the current revision and Windows certificate-chain trust separately. Integrity can be checked using the public certificate embedded in someone else's PDF without their private key. Verification is offline; revocation and trusted timestamps are not checked.

## Defaults and updates

Choose **Help > Make Minty PDF the default**, then select Minty PDF for `.pdf` files in Windows Settings. If Settings was open during installation and the app is missing from the list, close Settings completely and reopen it from Minty PDF.

Minty PDF checks this release repository at startup. You can also use **Help > Check for updates**. Updates open a download link for you to install; they are not silently installed. PDF editing and OCR run locally, and document contents are not uploaded for update checks.

## Current limits

- DOCX import uses basic formatting and Arial. Complex Word layouts and legacy DOC files are not supported. PDF-to-Word/Excel export is not available.
- Paragraph reflow across pages, nested graphic-group editing and XFA scripting/dynamic layout are not supported. Some embedded fonts need a compatible replacement for new characters.
- Redaction marks do not remove content until applied. Applying redactions creates a new, unencrypted PDF made from page images. Original selectable text, interactive forms, links, bookmarks, attachments and signatures are removed from that copy.
- OCR accuracy and font matching depend on the scan. Additional PDF signatures, trusted timestamps and long-term signature validation are not implemented.

## Feedback and license

[Report a problem](https://github.com/dobromirdikov/minty-pdf-releases/issues/new) with your Minty PDF version, Windows version, steps to reproduce, and expected and actual results.

Minty PDF is distributed under the MIT license. Packages include `LICENSE`, `THIRD-PARTY-NOTICES.txt` and dependency license texts. This public repository contains release information; application source is currently private.
