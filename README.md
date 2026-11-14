


<img width="1103" height="639" alt="h316_panel" src="https://github.com/user-attachments/assets/2d6a6645-6dee-450f-b432-f5f50fb88ff6" />
# h316-front-panel-simh
• Interactive Honeywell H316 front panel GUI for SIMH BASIC-16 with live register lamps and PTR/PTP paper tape support.

# Honeywell H316 Front Panel for SIMH (v6)

An interactive graphical front panel for the **SIMH Honeywell H316** emulator, designed for running **BASIC-16** with live register lamps, sense switches, and an 8-channel perforated paper tape (PTR/PTP) monitor.

Linux release is compiled into a standalone native binary.

---

## Download

1. Go to the **[Releases](../../releases/latest)** section on the right-hand side of this page.
2. Under **Assets**, download these four files into the **same folder** (you can ignore GitHub's auto-generated *Source code* archives):
   * **`h316_panel_simhv6`** (standalone Linux executable)
   * **`basic.ini`** (SIMH configuration file)
   * **`basic_16_slst.ptp`** (Honeywell BASIC-16 paper tape image)
   * **`cf1.bas`** (sample BASIC program C/F CONVERTER)
   * **`memtest.ptp`** (sample BASIC program on ptp memtest PRESS other REGISTER to watch a light show.)
3.Please install SIMH. Will work with v3 and above. (sudo apt install simh)
    
---

## Requirements

* **OS:** Linux (`x86_64`) with an X11 desktop environment
* **Emulator:** SIMH Honeywell H316 (`h316` binary installed in your system `PATH`)

---

## Installation & Quick Start

1. Open a terminal in the folder where you saved the downloaded files.
2. Make the binary executable:
   ```bash
   chmod +x h316_panel_simhv6
   ```

3. Launch the front panel:
   ```bash
   ./h316_panel_simhv6
   ```

4. Click **LAUNCH** to boot SIMH, goto the terminal window and type RUN 1000. Always use CAPS LOCK. Then click **LOAD .BAS** to try `cf.bas` or **MOUNT PTR** for `memtest.ptp`.


5. Please download all files and put them in one folder.

---

## Front Panel Controls

| Control | Function |
| :--- | :--- |
| **LAUNCH** | Boots SIMH using the INI file specified in the `INI:` field (default: `basic.ini`). |
| **LOAD .BAS** | Streams an ASCII `.bas` or `.txt` program line-by-line into BASIC-16. |
| **MOUNT PTR** | Attaches a paper tape image (`.ptp`, `.ptap`, `.bin`, or `.txt`) to the reader and feeds it into BASIC. |
| **BOOT PTR** | Executes `boot ptr` in SIMH to bootstrap from the attached paper tape. |
| **PUNCH PTP / STOP PTP** | Captures `LIST` output from BASIC-16 and saves it as a `.ptp` file with blank tape leaders. |
| **SENSE 1–4 & SENSE** | Toggles the 4 front-panel sense switches and syncs their octal value (`SSW`) to SIMH. |
| **POLL: OFF / ON** | Toggles real-time polling of the `A`, `B`, `P/Y`, and `M` registers on the front-panel lamps. |
| **REGISTER (A, B, OP, P/Y, M)** | Selects which register is displayed on the 16-bit indicator lamps and octal readout. |
| **MSTR / FETCH / P+1** | Sends `Ctrl+C` (Break), `LIST`, or `RUN` commands to BASIC-16. |
| **POWER (ON)** | Cleanly terminates the background `h316` SIMH process and exits the application. |
