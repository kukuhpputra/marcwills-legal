# Privacy Policy — MARCWILLS HRVA

**Last updated:** May 27, 2026
**Developer:** Kukuh Pambuka Putra
**Contact:** kukuh.pambuka@outlook.com

---

## 1. Overview

MARCWILLS HRVA ("the App") is a heart rate variability (HRV) analyzer for sport
science research. This Privacy Policy explains what data the App collects, how it
is used, and how it is stored.

**Summary:** All data collected by this App is stored exclusively on your device.
No data is transmitted to external servers, third parties, or the developer.

---

## 2. Data We Collect

### 2.1 Subject Information
When you register a research subject, the App collects:
- Name or anonymized subject code
- Age
- Biological sex (Male / Female)
- Resting heart rate (measured within the App)

This information is stored in a local SQLite database on your device.

### 2.2 Physiological Data
During a recording session, the App collects the following data from a Polar H10
chest belt sensor via Bluetooth:
- Heart rate (bpm)
- RR intervals (ms) — beat-to-beat intervals used for HRV analysis
- ECG waveform (raw electrical signal at 130 Hz) — displayed only, not exported
- Accelerometer data (X, Y, Z axes in mg) — for motion artifact detection

This data is stored as local files in the App's private document folder on your device.

### 2.3 Derived Metrics
The App calculates and stores HRV metrics derived from the above data:
- RMSSD, SDNN, pNN50, Mean RR
- SD1, SD2, SD1/SD2 ratio (Poincaré plot parameters)

---

## 3. How We Use Your Data

All collected data is used solely for the following purposes:
- Displaying real-time physiological metrics during a recording session
- Storing session records for later review and export
- Generating HRV analysis reports compatible with third-party HRV analysis software software

The App does not use your data for advertising, profiling, or any purpose other
than the research workflow described above.

---

## 4. Data Storage

All data is stored **locally on your device** in:
- A SQLite database file (`sdms.db`) in the App's private storage
- Session folders (`sdms_sessions/`) in the App's document directory

The developer does not have access to this data. The data is not backed up to
any cloud service by the App itself. If you use Android's built-in backup features,
your device settings govern whether app data is backed up to Google Drive.

---

## 5. Data Sharing and Export

The App does not automatically share any data with third parties.

You may choose to export session data using the built-in export feature, which
uses Android's Share Sheet to send files to apps of your choice (e.g., email,
Google Drive, cloud storage). This export is entirely user-initiated and
the developer has no involvement in or access to exported files.

Exported file formats:
- **CSV files** (hr.csv, acc.csv, hrv_rolling.csv): comma-separated physiological data
- **plain-text RR interval format (.txt)** (rr.txt): RR intervals in plain text for import into third-party HRV analysis software

---

## 6. Permissions

The App requests the following Android permissions:

### Bluetooth (BLUETOOTH_SCAN, BLUETOOTH_CONNECT)
**Purpose:** Required to scan for and connect to the Polar H10 chest belt sensor via
Bluetooth Low Energy (BLE).
**Data use:** Only used to establish a connection with the sensor. No Bluetooth
data is transmitted to external servers.

### Location (ACCESS_COARSE_LOCATION)
**Purpose:** Android requires this permission to perform Bluetooth Low Energy (BLE)
scanning on Android 6.0 and above. This is a technical Android requirement.
**Data use:** The App does not collect, use, or store your geographic location.
Location services are not used for any purpose other than satisfying the Android
BLE scanning requirement.

---

## 7. Data Retention and Deletion

You are in full control of your data:
- **Delete a session:** Use the delete button in the Session screen. The session
  record and all associated files are permanently removed from your device.
- **Delete a subject:** Use the delete button in the Subject Registry. All sessions
  and files associated with that subject are permanently removed.
- **Uninstall the App:** Uninstalling the App removes all App data from your device,
  including the database and all session files.

---

## 8. Children's Privacy

This App is intended for use by researchers and professionals aged 18 and above.
The App does not knowingly collect data from children under 18. The subjects whose
physiological data is recorded may include minors when used in research settings;
in such cases, the researcher using the App is responsible for obtaining appropriate
informed consent in accordance with applicable laws and institutional ethics guidelines.

---

## 9. Security

All data is stored in the App's private storage directory, which is not accessible
to other apps on your device (standard Android sandboxing). The developer implements
no additional encryption beyond what Android provides natively, as no data leaves
the device.

---

## 10. Changes to This Privacy Policy

This Privacy Policy may be updated from time to time. Any changes will be reflected
in the "Last updated" date at the top of this document. Continued use of the App
after changes constitutes acceptance of the updated policy.

---

## 11. Contact

For questions or concerns about this Privacy Policy, contact:

**Kukuh Pambuka Putra**
Developer, MARCWILLS
Email: kukuh.pambuka@outlook.com

---

*MARCWILLS HRVA is part of the MARCWILLS physiological monitoring platform.*
