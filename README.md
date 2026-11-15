


<img width="1103" height="639" alt="h316_panel" src="https://github.com/user-attachments/assets/2d6a6645-6dee-450f-b432-f5f50fb88ff6" />
# h316-front-panel-simh
An interactive graphical front panel for the **SIMH Honeywell H316** emulator, designed for running **BASIC-16** with live register lamps, sense switches, and an 8-channel perforated paper tape (PTR/PTP) monitor.


• Interactive Honeywell H316 front panel GUI for SIMH BASIC-16 with live register lamps and PTR/PTP paper tape support.


## History: The Honeywell H316 Rack-Mount System

The **Honeywell H316** was introduced in **1969** as the compact, lower-cost entry in Honeywell's **Series 16** 16-bit minicomputer lineup (alongside the DDP-116, DDP-416, and DDP-516). While its pedestal variant became famous as the $10,600 Neiman Marcus "Kitchen Computer," the standard H316 was engineered primarily as an industrial and laboratory **19-inch rack-mount system**.

### Key Historical Milestones
* **First Sub-$10,000 Major Minicomputer:** Honeywell advertised the base rack-mountable H316 at **$9,700**, making it the first 16-bit minicomputer from a major manufacturer priced under $10,000.
* **ARPANET Backbone Node (IMP):** Beginning in the early 1970s, ruggedized rack-mounted H316s replaced the larger DDP-516 as **Interface Message Processors (IMPs)**—the packet-switching routers that formed the backbone of the early ARPANET (precursor to the modern Internet).
* **Early Semiconductor Memory Milestone:** In 1972, Honeywell demonstrated a prototype H316 fitted with a semiconductor RAM board at a computer show, marking one of the earliest public displays of solid-state memory in a commercial minicomputer (though production units continued using magnetic core memory).
* **The 19-Inch Rack Standard (EIA-310):** The H316 chassis was built to fit the standard **19-inch wide** equipment rack—a format originally created by AT&T and Western Electric in **1922** for telephone central-office relay equipment and standardized as **EIA-310** in **1965** using **1.75-inch (1U)** vertical mounting increments.

### Rack-Mount Hardware Specifications
* **Configurations:** Available as a **standard rack-mountable chassis** (with slides/hardware for customer-supplied 19" × 24" racks), a **full factory rack-mounted cabinet** (24" × 24" × 72"), a **tabletop** enclosure, or a **pedestal** unit.
* **Chassis Dimensions (Rack-Mountable Unit):** 15.47 in (H) × 17.69 in (W, behind 19" front panel) × 26 in (D)
* **Weight:** ~120 lbs (54 kg) for the standard rack-mountable unit (150 lbs for the tabletop version)
* **CPU & Logic:** 16-bit word length built from discrete **DTL (Diode-Transistor Logic)** integrated circuit modules, running at a **2.5 MHz** clock with a **1.6 µs** memory cycle time
* **Memory:** 4,096 words (4K × 16-bit) of magnetic core memory standard, expandable up to 16,384 words (16K)
* **Power & Cooling:** 475 watts AC with internal filtered forced-air cooling (rated for 0°C to 45°C ambient operation)
* **I/O & Peripherals:** 16-bit input/output buses (INB/OTB), single priority interrupt line (expandable), and standard support for 10 cps Teletype (ASR-33) paper tape readers/punches


# Honeywell H316 Front Panel for SIMH (v6)


Linux release is compiled into a standalone native binary.

---

## Download

1. Go to the **[Releases](../../releases/latest)** section on the right-hand side of this page.
2. Under **Assets**, download these five files into the **same folder** (you can ignore GitHub's auto-generated *Source code* archives):
   * **`h316_panel_simhv6.tar.gz`** (standalone Linux executable)
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

1. Open a terminal in the folder where you downloaded the archive and extract it:
   ```bash
   tar -xzvf h316_panelv6_linux.tar.gz
   ```
2. Open a terminal in the folder where you saved the downloaded files.
3. Make the binary executable:
   ```bash
   chmod +x h316_panel_simhv6
   ```

4. Launch the front panel:
   ```bash
   ./h316_panel_simhv6
   ```

5.  Click LAUNCH to boot SIMH, goto the terminal window and type Always use CAPS LOCK. RUN 1000. Answer NO then YES.  Then click LOAD .BAS to try cf1.bas or MOUNT PTR for memtest.ptp. type RUN once loaded. Please dont use POOL till program is fully loaded into BASIC-16


6. Please download all files and put them in one folder.

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


---

## Credits & Resources

* **[Open SIMH Project](https://opensimh.org/)** ([GitHub Repository](https://github.com/open-simh/simh)) — The open-source Computer History Simulation Project (originally created by Robert M. Supnik) that provides the `h316` emulator backend.
* **[SIMH Honeywell H316/H516 Simulator Documentation](https://opensimh.org/simdocs/h316_doc.html)** — Reference guide for emulated CPU registers, sense switches, Paper Tape Reader (`PTR`), and Paper Tape Punch (`PTP`) devices.
* **[Honeywell Series 16 Documentation Archive](http://www.series16.adrianwise.co.uk/documentation/index.html)** — Scanned Honeywell hardware manuals, programmers' reference guides, and BASIC-16 listings (mirrored from Bitsavers).
* **[Computer History Museum — Honeywell H316 Collection](https://www.computerhistory.org/collections/catalog/X579.85)** — Historical artifacts, brochures, and specifications for the 1969 Honeywell Series 16 lineup.
