# mylandx v1.3.3

A lightweight, modern desktop productivity app for Linux (built for Fedora GNOME): **task reminders, a study timer, alarms, clock, calendar, notes, a local music player, prayer times with adhan, and a national / international / Hijri calendar** — all in one small GTK4 app. No Electron, no cloud account, no tracking; your data stays on your machine.

> **Platform:** Linux (GTK4 + Python). A Windows build is not available yet.

## Highlights

### Productivity
- **Home** – analog + digital clock, WIB/WITA/WIT/UTC times, today's summary (active tasks, next alarm, focus time, next prayer), upcoming-event notices next to the clock.
- **Tasks** – quick add, due dates, priority, notes, reminders (from on-time up to 1 day before), filters, overdue markers.
- **Focus** – Pomodoro timer (focus / short break / long break), custom durations, link a session to a task, 7-day statistics.
- **Alarms** – multiple alarms, per-weekday repeat, 5-minute snooze, synthesized chime (no bundled audio files).
- **Notes** – plain-text editor with autosave (~0.6 s after you stop typing), search, pinning, word count, delete any note. Layered backups: `data.bak.json`, 14 daily snapshots, and automatic recovery of a corrupted data file.
- **Music (local only)** – add files/folders, queue with shuffle/repeat, favourites, **custom albums** to separate tracks by category, remove tracks from the list (files on disk are never touched), mini player bar with a close (✕) button. Playback uses `mpv`.

### Prayer times & adhan (new in 1.3)
- Five daily prayer times (plus sunrise), computed **offline** for any location.
- **Country → city picker**: 247 countries and ~750 built-in cities (Indonesia: ~260 regencies/cities), each with coordinates and an IANA time zone (DST-aware). Both dropdowns are searchable.
- **Manual coordinates** for any place not in the list (time zone is auto-picked from the nearest city if left blank).
- Calculation method follows the local authority where known (Kemenag RI, JAKIM, MUIS, Umm al-Qura, ISNA, Karachi, Egyptian, …), otherwise Muslim World League. High-latitude fallback included. Asr: standard or Hanafi.
- Desktop notification + **adhan playback** at prayer time (choose your own audio file, optional separate Subuh file; chime or silent modes). Music is paused automatically and resumed afterwards. Optional reminder 5/10/15 min before.
- Times, notifications and adhan use the **local time of the selected city**.
- Per-prayer on/off switches, live countdown to the next prayer, "test adhan" button.

### Calendars (new in 1.3)
- Month view with **Hijri day numbers** under each date and colored markers: red = national holiday, yellow = collective leave (cuti bersama), purple = national / international / Hijri observance.
- **Official Indonesian holidays for 2026 and 2027** (from the SKB 3 Menteri joint decree). Other years: fixed-date, Easter-derived and Hijri holidays are computed and marked "approximate".
- National observance days (Kartini, Sumpah Pemuda, Hari Pahlawan, …) and international days (Earth Day, Human Rights Day, …).
- **Hijri calendar** with events: Islamic New Year, Ashura, Mawlid, Isra Mi'raj, Nisf Sha'ban, Ramadan start, Nuzul al-Qur'an, Eid al-Fitr, Arafah, Eid al-Adha, Tashriq days, Ayyam al-Bidh. Manual ±1 day correction for moon-sighting differences.
- **Home notices** next to the clock for today and the next 7 days ("Tomorrow · Hari Pahlawan"), can be turned off.

### Look & feel
- macOS-style window buttons: round **red (close) / yellow (minimize) / green (maximize)** in a draggable custom title bar.
- Dark / light theme, 6 accent colors, 24-hour or AM/PM clock.
- Runs in the background (optional) so alarms and adhan still ring when the window is closed; optional start at login.

## Install (Fedora)
```bash
tar xzf mylandx.tar.gz && cd mylandx-app
./install.sh          # installs to ~/.local, no root unless packages are missing
mylandx --version     # should print: mylandx 1.3.3
```
Dependencies (installed automatically if missing): `python3-gobject`, `gtk4`, `python3-cairo`, `mpv`, `pipewire-utils`.
Uninstall: `./uninstall.sh` (add `--purge` to also delete data).

Keyboard shortcuts: `Ctrl+1…9` switch pages, `Ctrl+Q` quit, `Esc` closes dialogs.

## Data
Everything is stored locally in `~/.local/share/mylandx/` (`data.json`, backups). Safe to copy to another machine.

## Known limitations
- Prayer times are calculated, not scraped: expect **±1–3 minutes** vs. the official local schedule (verified against Jakarta, Oct 2026 — within 1 minute; other cities are not individually verified). Use the manual coordinates for places not in the list.
- Hijri month starts are tabular, adjusted to the Indonesian government's announced dates for 2026–2027; actual month starts depend on moon sighting (use the ±1 day correction).
- Holiday data is official only for 2026–2027; Nyepi / Waisak outside those years are not included. There is no online sync.
- No adhan recording is bundled — pick your own audio file in Settings.
- The GTK UI has been developed with stub-based tests; please report any visual glitches or crashes with the terminal output of `mylandx`.
