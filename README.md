# TTR Calculator

A browser-based Warfarin **Time in Therapeutic Range (TTR)** calculator using the Rosendaal linear interpolation method. All computation happens locally in your browser — no data ever leaves your machine.

**Live demo:** https://xuxiaobogit.github.io/ttr-calculator/
&nbsp;·&nbsp; **One-click sample:** https://xuxiaobogit.github.io/ttr-calculator/?demo=1

![TTR Calculator preview — sample dataset with per-group statistics, per-patient table, and an INR trajectory chart](docs/preview.png)

## Features

- 📄 **Flexible import** — drag & drop a CSV / TXT file, or paste rows straight from Excel. UTF‑8 and GBK encodings, plus comma / tab / semicolon delimiters, are auto‑detected.
- 👥 **Batch by patient and group** — computes many patients and groups at once; a single patient with just two columns (date, INR) also works.
- 📊 **Detailed metrics** — per‑patient TTR, time below range, time above range, and days assessed; per‑group summaries (mean ± SD, median, range).
- 📈 **Interactive INR trajectory chart** — the therapeutic window is shaded, and each measurement is colored by whether it falls in / below / above range.
- ⚙️ **Configurable range** — presets (2.0–3.0 / 2.5–3.5) or custom limits; optionally exclude over‑long testing intervals (default threshold 56 days).
- 💾 **One‑click CSV export** — results open directly in Excel.
- 🌐 **Bilingual UI (English / 中文) and light / dark themes.**
- 🔒 **Zero‑dependency single file** — everything runs client‑side; no data is uploaded to any server.

## Data format

One INR record per line; the layout is detected automatically from the number of columns:

| Columns | Layout |
| --- | --- |
| 4 | `PatientID, Group, DateTime, INR` |
| 3 | `PatientID, DateTime, INR` |
| 2 | `DateTime, INR` (single patient) |

Dates such as `2023-08-19 14:30`, `2023/8/19`, and `8/19/2023 0:05` are accepted (`x/y/year` is read as month/day/year).

Example:

```csv
PatientID,Group,DateTime,INR
P01,A,2025-01-06 09:00,1.85
P01,A,2025-01-20 09:30,2.40
P02,B,2025-01-08 08:15,3.10
```

## URL parameters

The demo link supports a few query parameters for sharing a preconfigured view:

| Parameter | Values | Effect |
| --- | --- | --- |
| `demo` | any | Auto-loads the built-in sample dataset |
| `lang` | `en` / `zh` | Sets the interface language |
| `theme` | `light` / `dark` | Sets the color theme |

Example: `?demo=1&lang=en&theme=light`

## Method

Rosendaal FR, Cannegieter SC, van der Meer FJ, Briët E. **A method to determine the optimal intensity of oral anticoagulant therapy.** *Thromb Haemost.* 1993;69(3):236‑239.

Time between consecutive INR measurements is allocated by linear interpolation. Intervals longer than the optional gap threshold are excluded from both the numerator and the denominator.

## Disclaimer

For research and educational use only; not intended for clinical decision-making.

## License

MIT
