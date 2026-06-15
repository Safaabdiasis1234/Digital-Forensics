# Digital Forensics — Portfolio 1: Analysing Forensic Images 🔍

> Hands-on forensic investigation into a suspected piracy and digital crimes case, using industry-standard tools to recover, analyse, and present digital evidence.

---

## Scenario

As part of an incident response team, I was tasked with investigating a company employee suspected of piracy and serious criminal activity. Two forensic images were seized and submitted through a chain of custody process:

- `E_01_Physical_Image` — physical USB image
- `USB_03.E01` — forensic USB image

The goal was to uncover hidden, deleted, or suspicious data using forensic tools and present findings in a structured report.

---

## Tools Used

- **FTK Imager** — forensic imaging, hash verification, file extraction
- **Autopsy** — file system analysis, metadata, timeline, encryption detection
- **HxD** — hex editor for file signature identification
- **VeraCrypt** — encrypted container mounting and analysis

---

## Tasks Completed

### Task 1 — Recovering Files from a Forensic Image *(15 marks)*

Analysed `E_01_Physical_Image` (Retro USB) using FTK Imager:

- Recovered **21 files** total — 12 regular files and 9 file slack entries
- Documented file names, signatures, extensions, and sizes for each file
- Confirmed device storage capacity: **3.84 GB**
- Verified image integrity via **MD5 and SHA-1 hash matching**

---

### Task 2 — File Signature Investigations *(25 marks)*

Loaded `USB_03.E01` into FTK Imager and used the HEX view to identify 7 files in `/root/Private`:

| File | HEX Signature | Extension |
|------|--------------|-----------|
| file01 | `24 50 44 46` | .pdf |
| file02 | `50 4B 03 04` | .zip |
| file03 | None | .txt |
| file04 | `31 21 44 4F 43 54 59 50 45` | .html |
| file05 | `37 7A BC AF 27 1C` | .7z |
| file06 | `47 49 46 38 39 61` | .gif |
| file07 | `FF FB 90 44` | .mp3 |

---

### Task 3 — Autopsy Case Analysis *(10 marks)*

Created an Autopsy case for `USB_03.E01` and examined the file system:

- Autopsy case file extension: `.aut`
- Device model for `Sword.Art.Online.full.1189342.jpg`: **SEIKO EPSON CORP — EPSON scanner** (EXIF metadata, April 2009)
- Timeline view revealed **3 event types** in 2009: EXIF creation, document created, document last saved
- Identified potentially encrypted file: `supermoon.jpg` — entropy score **7.999999**

---

### Task 4 — VeraCrypt Container Analysis *(25 marks)*

Mounted and examined the encrypted `supermoon.jpg` container:

- Tested SHA256 hashes of 6 recovered documents to find the correct password
- Correct password: SHA256 of `Twofish_encryption.pdf`
```
cbca79cfd838aaae8b21f3df724fde090de17cb276dd82d78adfb48d984a36ae
```
- **3 files** found inside container: `Ajin-4.jpg`, `Blue_Eye_Samurai_DvDCover.jpg`, `Income.xlsx`
- `Income.xlsx` contained **21 collectors** involved in anime sales totalling £11,362
- Recovered deleted file `$RJKF6BP` from `$RECYCLE.BIN` containing **8 movie titles**

**Evidence of suspected criminal activity:** Contact names in the recovered Excel file were coded references — I.L Licit (Illicit), C.R. Iminal (Criminal), S.H. Ady (Shady), C. Rook (Crook) — suggesting deliberate concealment of illegal transactions. The file's presence in the Recycle Bin indicated an attempt to destroy evidence.

---

## Files in this Repository

- `coursework_digital_forensics.pdf` — Full forensic investigation report
- `Chain_of_Custody_Form.pdf` — Evidence chain of custody documentation

---

## Module Info

- **Module:** Digital Forensics — CMP020N210S
- **Assessment:** Coursework Portfolio 1 (25% of module)
- **Institution:** University of Roehampton

---

## Disclaimer

This investigation was conducted in a controlled academic environment. All findings are for educational purposes only.
