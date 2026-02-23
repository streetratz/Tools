# Time Zone Helper

**Time Zone Helper** is a lightweight Windows desktop utility that lets you track and compare multiple time zones simultaneously. Whether you're scheduling meetings across continents, coordinating with remote teams, or just curious what time it is in Tokyo, Time Zone Helper keeps the answer one glance away — without a web browser, without sign-in, without ads.

> **Offline-only.** The app makes no network calls and collects no telemetry.

---

## What It Does

| Capability | Detail |
|---|---|
| **Always-on Local & UTC display** | Your system's local time and UTC are always visible as the first two rows. |
| **Up to 5 additional time zones** | Add any zone from the full IANA timezone database (e.g. `America/New_York`, `Asia/Tokyo`). |
| **±48-hour time slider** | Shift the displayed moment up to 48 hours forward or backward in 15-minute steps to plan ahead or look back. |
| **Live / Shifted modes** | When the slider is at 0 the display tracks the system clock in real time (Live). Moving the slider freezes a base time and shifts from it (Shifted). |
| **Copy All** | One click copies every visible row to the clipboard, one zone per line, ready to paste into an email or chat message. |
| **Reset** | Returns the slider to 0 and snaps the display back to the current time. |
| **System tray presence** | Runs quietly in the Windows system tray. Close the window to hide it; the app keeps running until you choose Quit from the tray. |
| **Persistent preferences** | Your chosen zones, their order, custom labels, time format, and window position are saved automatically and restored on every launch. |

---

## Installation

### Option 1 — NSIS Installer (recommended)

1. Download `Time-Zone-Helper_<version>_x64-setup.exe` from this folder.
2. Double-click the installer and follow the on-screen prompts.
3. Launch **Time Zone Helper** from the Start menu or desktop shortcut.

### Option 2 — MSI Installer

1. Download `Time-Zone-Helper_<version>_x64_en-US.msi` from this folder.
2. Double-click the `.msi` file and complete the wizard.
3. Launch **Time Zone Helper** from the Start menu.

**System requirement:** Windows 10 (1803) or later, x64.

No internet connection is required. The installer does not contact any remote server.

---

## Getting Started

When the app opens you will see two permanent rows at the top:

```
🏠 Local     2026-02-24  14:35
   UTC       2026-02-24  19:35
```

Both update every minute while in **Live** mode.

---

## Using the Time Zone List

### Viewing zones

All zones — Local, UTC, and any you have added — are displayed as a vertical list. Each row shows the zone name (or your custom label) and the current effective time in your chosen format.

### Entering edit mode

Click the **pencil / edit icon** in the toolbar to enter **Edit mode**. In this mode the following controls become available:

| Control | Action |
|---|---|
| **+ Add** | Opens a searchable dropdown of all IANA zone names. Type to filter, then select to add. |
| **✕ Remove** | Appears next to each additional zone row. Click to remove that zone. |
| **▲ / ▼ Move buttons** | Move an additional zone one position up or down in the list. Local and UTC always stay at positions 1 and 2 and cannot be moved. |
| **Label field** | Click the zone name to type a custom display label (e.g. rename `America/Chicago` to `Chicago Office`, or rename `Local` to `Home`). Leave empty to show the default name. Available for all zones **except UTC**. |

Click the **checkmark / done icon** to exit edit mode. All changes are saved automatically.

**Limits:**
- Maximum of **5 additional zones** (on top of Local and UTC).
- Duplicate zones are blocked with a brief "Already added" message.
- **Local** cannot be removed. Its label can be customised.
- **UTC** cannot be removed or renamed.
- Additional zones can be removed and labelled freely.

---

## Shifting Time with the Slider

The horizontal slider at the bottom of the window controls the time offset.

| Slider position | Mode | Behaviour |
|---|---|---|
| Dead center (0) | **Live** | All rows track the current system clock in real time. |
| Moved left or right | **Shifted** | The moment the slider first moves off 0, the current time-of-day is captured as the base. All rows show that base time ± the slider offset. |

- **Range:** −48 hours to +48 hours.
- **Step:** 15 minutes per notch.
- The window title shows the current mode: `Time Zone Helper (Live)` or `Time Zone Helper (Shifted)`.

### Resetting

Click the **Reset button** (circular arrow icon) to:
- Move the slider back to 0.
- Discard the captured base time.
- Return to **Live** mode.

---

## Copying Times

Click the **Copy All button** (clipboard icon) to copy every visible row to the clipboard:

```
Local: 2026-02-24 14:35
UTC: 2026-02-24 19:35
America/New_York: 2026-02-24 09:35
Europe/London: 2026-02-24 19:35
Asia/Tokyo: 2026-02-25 04:35
```

Output respects the active 12-hour or 24-hour format setting and the current zone order. If clipboard access fails the app displays a notification and does not crash.

---

## Settings

### Time Format — 12-hour / 24-hour

A toggle button sits in the **top header bar**, next to the Settings icon. Click it to switch between:

| Format | Example |
|---|---|
| **24-hour** (default) | `2026-02-24 14:35` |
| **12-hour** | `2026-02-24 2:35 PM` |

The selected format applies to all zone rows and to the Copy All output. The setting is persisted and restored on the next launch.

### Display sub-rows

Inside the **Settings panel** (gear icon, top-right) two sub-row visibility options are available:

| Setting | Default | Effect |
|---|---|---|
| **Show day / date** | On | Displays an extra sub-row under each zone showing the day of the week and calendar date. |
| **Show UTC offset** | On | Displays an extra sub-row showing the current UTC offset (e.g. `UTC+9`) for each zone. |

Turning these off gives a more compact view.

### Theme

Inside the Settings panel a **Dark / Light** theme toggle lets you switch between dark mode (default) and light mode. The choice is stored locally and persists across launches.

---

## System Tray

Time Zone Helper runs from the Windows system tray so it is always within reach.

| Action | Result |
|---|---|
| **Left-click** tray icon | Opens (or brings to front) the app window. |
| **Right-click** tray icon → **Open** | Opens the app window. |
| **Right-click** tray icon → **Reset** | Resets the slider to 0 (returns to Live mode) without opening the window. |
| **Right-click** tray icon → **Quit** | Fully exits the application. |
| **Window Close button (✕)** | *Hides* the window only — the app continues running in the tray. |

---

## Preferences & Data Storage

All preferences are stored **locally on your machine** in a JSON file inside your Windows user application data directory:

```
%APPDATA%\com.chronoslider.app\preferences.json
```

The file is written atomically (temp file → rename) to prevent corruption. No data is synced, uploaded, or shared.

**Stored preferences:**

| Key | Description |
|---|---|
| `timeFormat` | `"24h"` or `"12h"` |
| `additionalTimezones` | Ordered list of IANA zone IDs + optional custom labels |
| `windowBounds` | Last window position and size |

---

## Keyboard Shortcuts

| Key | Action |
|---|---|
| **Tab / Shift+Tab** | Move focus between controls |
| **Space / Enter** | Activate focused button |
| Any toolbar element focused | Auto-shows the toolbar if it is hidden |

---

## Frequently Asked Questions

**Does the app need an internet connection?**
No. All timezone data (IANA database) is bundled inside the application. The app never makes any network request.

**Does it collect any usage data or telemetry?**
No. There is no analytics or telemetry of any kind.

**The window is gone — how do I reopen it?**
Click the Time Zone Helper icon in the Windows system tray, or right-click the tray icon and choose **Open**.

**Can I reorder Local and UTC?**
No. Local is always row 1 and UTC is always row 2. Only the additional zones (rows 3+) can be reordered.

**I added a zone with a weird name — can I rename it?**
Yes. Enter edit mode (pencil icon), click the zone name, and type any label you like. Leave the field empty to revert to the default name. You can also rename the **Local** row. The **UTC** row label is fixed and cannot be changed.

**Can I make the app launch at Windows startup?**
Auto-launch is not available in this release. It is planned for a future version.

---

## Version History

See `CHANGELOG.md` in this folder for the full version history of this release.

---

## License

Time Zone Helper is developed and maintained by the project owner. See the main code repository for licensing details.
