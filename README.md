# 🛂 BiometricScanner

**BiometricScanner** is a native iOS app that scans biometric passports using the camera and NFC. It reads the Machine Readable Zone (MRZ), derives the required access key, and then reads personal and biometric data (including the face photo) from the chip. Built with Apple’s native frameworks for speed, privacy, and flexibility.

---

## ✨ Features

- 📷 Scan MRZ (Machine Readable Zone) using Apple's Vision framework
- 🔐 Generate BAC (Basic Access Control) keys from MRZ
- 📡 Read NFC chip via Core NFC
- 👤 Extract identity info (DG1)
- 🖼 Extract and render biometric face photo (DG2 - JPEG2000)
- 🧱 Modular, clean SwiftUI architecture
- 🧩 Built to support IDs and other documents in the future

---

## 📸 Screens Overview

1. **MRZ Scan** – Live camera feed with overlay to scan passport
2. **NFC Read** – Connects to chip, authenticates, and reads DG1 & DG2
3. **Result** – Displays parsed text data + biometric photo

---

## 🧱 Tech Stack

- Swift 5
- SwiftUI
- VisionKit / Vision Framework (OCR)
- Core NFC (NFC chip read)
- JPEG2000 support (via native iOS image decoding)
- iOS 17+

---

## 📂 Project Structure

BiometricScanner/
1. MRZ-Scan.swift // Camera-based MRZ scanner view
2. NFC-Scan.swift // NFC session and chip communication
3. MRZ-Parse.swift // Extracts document number, DOB, expiry
4. NFC-Read.swift // Reads DG1 and DG2 from chip
5. Doc-Data.swift // Holds parsed personal info and image
6. Result.swift // Displays data and face photo
7. BiometricScanner.swift // Main app entry point


## 🔐 Required Permissions (`Info.plist`)

<key>NSCameraUsageDescription</key>
<string>Camera access is required to scan document MRZ zones.</string>

<key>NFCReaderUsageDescription</key>
<string>NFC access is needed to read biometric data from documents.</string>

<!-- Optional / future support -->
<key>NSPhotoLibraryAddUsageDescription</key>
<string>Photo library access is needed to save scanned images.</string>

<key>NSPhotoLibraryUsageDescription</key>
<string>Access is required to choose images for comparison or identity verification.</string>

<key>NSFaceIDUsageDescription</key>
<string>Face ID may be used in future to compare your photo with document data.</string>

## 🚧 MVP Limitations
Only works with ICAO-compliant biometric passports

No support for older devices without NFC

Doesn’t store or export scanned data (yet)

No selfie capture or face matching in MVP

## 🛠 Roadmap
 Add support for national eID cards

 Local secure storage of scan history

 Face match: DG2 photo vs. selfie

 Export scanned data securely

 UI/UX polish + theming

## 🧪 Developer Notes
Testing requires a real biometric passport

NFC only works on physical devices (iPhone 7+)

MRZ can be mocked using test images or fake strings

DG2 decoding depends on JPEG2000 support (built-in on iOS)

## 📄 License
MIT — free to use and modify, but handle biometric data responsibly. Don’t be shady.

## 👨‍💻 Author
Built by Bojanstven — indie dev focused on fast MVPs, privacy-first tools, and clean Swift code.
