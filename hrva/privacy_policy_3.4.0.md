<!--
DRAFT for HRVA v3.4.0 — updated 2026-10-19 (local only; NOT published, NOT
committed). Source: the 2026-10-13 draft (D-P1 … D-P12) plus the 3.4.0
changes (sdms_app/milestones/update340/legal_review_340.md §8–§9; Notes 195,
212–224, 232–244). Before publishing: legal review; fill in the effective
date; "Last updated" must equal kLegalConsentVersion in the app
('2026-10-19'); then carry the text into the .html page.
-->

# Privacy Policy — MARCWILLS HRVA

**Last updated:** October 19, 2026
**Developer:** Kukuh Pambuka Putra · MARCWILLS HRVA v3.4.0 · **Effective:** October 19, 2026
**Contact:** kukuh.pambuka@outlook.com

> **Summary:** All data collected by this App is stored on your device. The App
> has no internet access: no data is transmitted to external servers, third
> parties, or the developer. Data leaves the App only when you export it
> yourself (see Section 6).

---

## 1. Overview

MARCWILLS HRVA ("the App") is a heart rate variability (HRV) analyzer for sport
science research and wellness monitoring. This Privacy Policy explains what data
the App collects, how it is used, and how it is stored.

---

## 2. Data We Collect

### 2.1 Subject Information

When you register a research subject, the App collects:

- Subject code (mandatory)
- Name (optional)
- Age
- Biological sex (Male / Female)
- Training status (Athlete / Sedentary; optional, metadata only — it enters no
  calculation)
- Resting heart rate (measured within the App or entered manually)

The subject code is a mandatory anonymization identifier. It is designed to let
you refer to a research subject without recording their name, supporting research
protocols that require de-identified or pseudonymized data. If your research
protocol requires full anonymization, we recommend using the subject code as the
primary identifier and leaving the name field blank.

This information is stored in a local SQLite database on your device.

### 2.2 Physiological Data

During a recording session, the App collects the following data from a Polar H10
chest belt sensor via Bluetooth:

- Heart rate (bpm)
- RR intervals (ms) — beat-to-beat intervals used for HRV analysis
- ECG waveform (raw electrical signal at 130 Hz) — displayed during a recording
  and, when the per-session "Save ECG" switch is on (the default), saved to
  `ecg.csv` in the session folder and included in exports
- Accelerometer data (X, Y, Z axes in mg) — for motion detection and activity
  monitoring
- The sensor's own timestamps for ECG and accelerometer samples
- Sensor skin-contact status as reported by the sensor, and Bluetooth connection
  events (disconnections and reconnections) with their times
- Bluetooth signal strength (RSSI) of the sensor, about once per second while
  recording
- The sensor's battery level, each time it changes during a recording
- Polar H10 device ID — a hardware identifier for the sensor itself, used to
  record which physical device was used for a session
- Sensor device information as reported by the sensor at connection: model,
  manufacturer, serial number, and firmware, hardware and software revisions —
  recorded per session for traceability, together with the App's version and
  build identifier

Device identifiers (sensor serial number, firmware) identify the sensor, not the
person, but may link sessions recorded with the same sensor.

This data is stored on your device, in the App's private storage: partly as files
in the session folder and partly in the App's local SQLite database.

### 2.3 Session Configuration Data

In Activity Mode, the App additionally records:

- Target intensity settings (Karvonen % HRR, tolerance, intensity standard)
- Heart rate zone adherence data (time in range, underload, overload)
- Notification preferences for the session

This configuration is recorded with the session and written to the Karvonen
section of the session's `session_methods.md` file.

### 2.4 Derived Metrics

The App calculates and stores HRV metrics derived from the above data:

- RMSSD, SDNN, pNN50, Mean RR
- SD1, SD2, SD1/SD2 ratio (Poincaré plot parameters)
- ln(RMSSD), lnRMSSD/mRR (log-transformed HRV indices)
- LF Power, HF Power, LF/HF ratio, Total Power (frequency-domain, Stationary Mode
  only)
- ECG R-peak times detected by the App in the saved ECG, and a signal-quality
  index (bSQI) per 10-second segment that compares the App's R-peak detection
  with the sensor's RR intervals (`ecg_rpeaks.csv`, `ecg_quality.csv`); during a
  recording the same index is shown on screen but not stored
- Recording-integrity counts (what was confirmed written, gaps, late or duplicate
  samples), summarised in `session_methods.md`

### 2.5 Session Notes

The App allows you to attach a free-text note to a recording session (e.g., to
record contextual observations about that session). This field is not validated,
filtered, or restricted by the App in any way — any text you enter is stored
exactly as typed.

Because the App does not inspect or restrict the content of this field, **you are
responsible for what you write in a session note**. If your research protocol
requires full anonymization of subject data, do not enter the subject's name or
other directly identifying information in a session note.

### 2.6 Session Markers

During a recording you can place markers: numbered events (with an optional
free-text description), body-position changes, and analysis-window start/stop. The
App also records its own markers (automatic stability transitions, intensity-alert
firings, sensor disconnections and reconnections, and changes of the skin-contact
status reported by the sensor). The same responsibility as for session notes
applies to what you type into an event description: event descriptions are
included in exports, including the encrypted `.hrva` file (Section 5), so do not
write participant names in them.

---

## 3. How We Use Your Data

All collected data is used solely for the following purposes:

- Displaying real-time physiological metrics during a recording session
- Storing session records for later review and export
- Generating HRV analysis reports and session summaries
- Providing intensity guidance feedback in Activity Mode

The App does not use your data for advertising, profiling, or any purpose other
than the research or wellness workflow described above.

---

## 4. Data Storage

All data is stored **locally on your device**. The developer does not have access
to it.

### Where your data is stored

| Where | What | Notes |
|---|---|---|
| **App database** (`sdms.db`, in the App's private storage on this phone) | Participants: code, optional name, age, gender, training status. Sessions: date and time, mode, settings (Karvonen target, body position, "Save ECG", disconnect alert), resting/maximum heart rate and how the resting value was obtained, sensor ID, session ID, optional session name and notes. For each session: every RR interval with its status, every heart-rate packet, per-minute HRV values and their validity, markers (including any text you type in a marker description), the activity log, sensor disconnections, signal strength, recording-health counts, sensor battery level, the sensor settings used, sensor details (model, serial number, firmware), the ECG R-peaks and signal-quality index, and the session's methods text. App settings: device tag, export folder, consent date. | The single source for everything except raw ECG and accelerometer data. |
| **Session files** (one folder per session in the App's private storage; the folder name contains the participant's name if one was entered, otherwise the participant code, plus the date and the mode) | `acc.csv` (raw accelerometer data) and, when "Save ECG" is on, `ecg.csv` (raw ECG). | Since v3.4.0 nothing else is kept as a file. Sessions recorded with earlier versions keep their older files. |
| **Files created only when you export** | The files listed in Section 5, the summary PDF, and the `.hrva` file. | Built at the moment of export in a temporary folder that the App deletes afterwards. They leave the App only where you send them (Section 6). Exported copies are named with the session's identifier (SID), not the folder name. |
| **Database backup** ("Export database backup", only when you tap it) | A copy of the whole App database: every participant and every session. | **Does not contain the raw ECG and accelerometer data** (`ecg.csv`, `acc.csv`). Keep the session exports too if you need complete sessions. The temporary copy made for the backup is deleted by the App. |
| **Android / Google backup** | Nothing. | Since v3.4.0 the App does not take part in Android/Google backup or in device-to-device transfer. |

**Backups made by earlier versions.** Up to v3.3.x, Android's automatic backup was
on by default for the App. If Google backup was switched on for your phone,
Android may already have stored a copy of the App's data in your Google account.
Updating to v3.4.0 does not delete that copy, and the App cannot reach it. You can
delete it yourself in your phone's Google backup settings (the menu differs
between phone makers and Android versions).

---

## 5. Session Output Files

While recording, the App keeps only `acc.csv` and, when "Save ECG" is on,
`ecg.csv` as files (Section 4). When you export a session, the App creates these
files from its database:

### Stationary Mode

- `rr.txt` — raw RR intervals
- `hr.csv` — timestamped heart rate log
- `acc.csv` — accelerometer data log
- `hrv_rolling.csv` — per-minute HRV snapshot
- `session_markers.csv` — the session markers of Section 2.6
- `session_methods.md` — analysis method documentation for this session,
  including the App version and build identifier, the sensor's device information
  (including its serial number) and a summary of the recording's integrity
- `beats.csv` — every received RR interval with its status
- `disconnect_gaps.csv` — Bluetooth disconnection gaps
- `rssi.csv` — Bluetooth signal strength of the sensor
- `battery.csv` — sensor battery level changes
- `ecg.csv`, `ecg_rpeaks.csv`, `ecg_quality.csv` — when "Save ECG" is on

### Activity Mode

All files above, plus:

- `activity_log.csv` — per-second intensity status log

A PDF session summary can also be generated. Exported copies are named with the
session's identifier (SID), for example `SID-hr.csv`.

### The `.hrva` file

"Export .hrva" writes a whole session into one file, `SID.hrva`, together with a
checksum file `SID.hrva.sha256`. The `.hrva` file is encrypted (Section 10) and
pseudonymised: it does not contain the participant's name, the session folder
name, session notes, the session name or the App's settings. It does contain the
participant code, age, gender and training status, the real date and time of the
session, the sensor's identifiers (including its serial number) and event-marker
descriptions. Raw accelerometer data is included only if you choose "Include raw
ACC"; otherwise a per-second summary is included. The App creates a `.hrva` file
only when you export one.

---

## 6. Data Sharing and Export

The App does not automatically share any data with third parties. Every export is
started by you, and the developer has no involvement in or access to exported
files. There are three ways data can leave the App:

- **Share Sheet:** session files, the `.hrva` file and the PDF summary are handed
  to an app you choose (e-mail, cloud storage, messaging).
- **Export folder:** if you choose a folder in Settings, every session export is
  also copied into it, in a sub-folder named with the session's SID. Re-exporting
  keeps the previous copy under a time-stamped name.
- **Database backup:** Settings → "Export database backup" writes a complete copy
  of the App's database — including every participant's name, code and details —
  into the export folder. The backup also contains the technical records of every
  session (for example signal strength, sensor battery, sensor device information
  including serial numbers, and disconnection gaps). Backups made before a
  deletion still contain that session (see Section 8).

**Exported files are outside the App's protection.** Other apps with access to
your device storage can read them, and they remain on the device until you delete
them yourself.

---

## 7. Permissions

### Bluetooth (BLUETOOTH_SCAN, BLUETOOTH_CONNECT)

Required to scan for and connect to the Polar H10 sensor via Bluetooth Low Energy.
No Bluetooth data is transmitted to external servers.

### Location (ACCESS_FINE_LOCATION)

Android requires location permission for Bluetooth Low Energy scanning on
Android 6.0 and above. The App declares only the precise-location permission
(ACCESS_FINE_LOCATION); the permission list on your phone may also show the
approximate-location permission (ACCESS_COARSE_LOCATION) as granted to the App.
The App does not collect, use, or store your geographic location.

### No storage or internet permission

The App requests no storage permission. The export folder is chosen through
Android's own folder picker, which gives the App access to that one folder only;
you can choose a different folder at any time in the App's Settings. The App also
has no internet permission; the links to these documents open in your browser.

### Vibration (VIBRATE)

Used to provide intensity feedback notifications during Activity Mode sessions
(underload and overload alerts) and, in both modes, to signal that the sensor has
disconnected during a recording (can be switched off per session). This is a
normal Android permission and does not require user confirmation at runtime.

---

## 8. Data Retention and Deletion

You are in full control of your data. Deletion inside the App is **permanent**.

### What is deleted

| You do | Deleted from this phone | NOT deleted (the App cannot reach these) |
|---|---|---|
| **Delete a session** (Records or the participant's session list; one or several) | The session's record and everything stored for it in the App database; its session folder (`ecg.csv`, `acc.csv`, and older files); the temporary copies the App made for sharing; its copy in the export folder **only if you tick that option**. Deleted content is overwritten in the database file. | Files already shared to other apps or people (including `.hrva` files); database backups made before the deletion; the export-folder copy if you did not tick the option; backups Android made from earlier versions (Section 4). |
| **Discard** a recording right after Stop | The same as "Delete a session" for that recording. Nothing of it has been exported yet. | Database backups made during or before the recording; backups Android made from earlier versions. |
| **Delete a participant** (Registry) | The participant's registration (code, name, age, gender, training status) and **all of their sessions**, as in "Delete a session", in one step; their sessions' copies in the export folder **only if you tick that option**. | Files already shared; database backups made before the deletion (they contain the participant); export-folder copies if not ticked; backups Android made from earlier versions. |
| **Uninstall the App** | All App data in the App's private storage. | The same items as above. |

A deleted session leaves a gap in the device's session numbering (shown as
"attempts discarded or deleted" in a participant's session list), so it is
visible that something was removed, but no content remains.

**Deletion inside the App does not reach exported copies.** If a participant
withdraws from your study, removing exported copies, database backups and any
older Android backups is part of your research protocol. Database backups saved in
the export folder are never deleted by the App, even when you tick the option to
delete a session's export-folder copy: that option removes only the session's own
SID sub-folder. Export-folder copies of sessions that you deleted with an earlier
version of the App (versions before 3.4.0 did not offer to delete them) also remain
until you delete them yourself.

---

## 9. Children's Privacy

This App is built for research, and it is therefore normally operated by users
aged 18 and above: researchers, educators, coaches and trained professionals.

The App may also be used by students under 18 who want to learn how heart rate is
recorded, preferably with a teacher, parent or guardian present. The App itself
has no account or sign-up, shows no advertising, has no internet access, and sends
nothing to the developer or to any third party, so it does not collect a student's
personal information anywhere outside the device it runs on. What is recorded
stays in the App's private storage unless a person chooses to export it
(Section 6).

When subjects or users include minors, the researcher or teacher running the
session is responsible for obtaining appropriate informed consent, including from
a parent or guardian where required, in accordance with applicable laws and
institutional ethics guidelines. Do not enter a minor's real name if a participant
code is enough.

---

## 10. Security

Data inside the App is stored in its private storage directory, which is not
accessible to other apps on your device (standard Android sandboxing). Exported
copies (Section 6) are not covered by this protection.

### Encryption of .hrva files

HRVA can export a session as a single `.hrva` file. This file is encrypted with
industry-standard encryption (AES-256-GCM) using a key built into the HRVA family
of applications (HRVA Record, HRVA Workbench). The purpose is to deter casual,
unauthorised viewing while the file is shared or stored. It is not designed to
prevent access by parties who use HRVA applications, nor by technically skilled
parties; it is not a substitute for the researcher's own data-protection
measures. `.hrva` files are pseudonymised: participant names and free-text
session notes are not included. Event-marker descriptions are included;
researchers should not write participant names in them. Per-stream exports (e.g.
`rr.txt`, CSV files) are not encrypted. MARCWILLS does not receive or store
research data; the researcher who records and shares the data is responsible for
its lawful handling, participant consent, and responding to lawful requests from
authorities or reviewers. File integrity is verified with SHA-256 checksums.

The SHA-256 checksum (`SID.hrva.sha256`) only shows whether a file has changed;
it does not hide its content.

---

## 11. Changes to This Privacy Policy

This Privacy Policy may be updated from time to time. Any changes will be
reflected in the "Last updated" date at the top of this document. When a change is
material, the App asks you to read and agree again before it can be used.

---

## Contact

For questions or concerns about this Privacy Policy, contact:

**Kukuh Pambuka Putra**
Developer, MARCWILLS
Email: kukuh.pambuka@outlook.com

---

© 2026 Kukuh Pambuka Putra. All rights reserved.
MARCWILLS HRVA v3.4.0 · Developed with AI coding assistance (Claude, Anthropic)
[Terms & Conditions](terms_and_conditions) · [Medical Disclaimer](disclaimer)
