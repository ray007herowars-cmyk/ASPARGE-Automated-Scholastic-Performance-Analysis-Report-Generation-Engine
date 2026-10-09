# Automated Student Performance Analysis and Mark Sheet Generation System

A browser-based tool that lets faculty enter cycle test marks and instantly get the converted marks, a class performance summary, a mark-distribution chart, and a **fully filled Excel mark statement** in the institution's official template.

**Live demo:** `https://asparge.vercel.app/index.html`

> **License:** All rights reserved. This project may not be copied, reused, modified or redistributed. See [LICENSE](LICENSE).

---

## What it does

- Faculty picks the department, year and section from dropdowns and types the subject code, subject name and faculty name.
- The class roster is loaded from a CSV file (or pasted in).
- Faculty enters marks (a number, `AB` for absent, `MP` for malpractice).
- The app converts marks (for example 25 to 7.5) and calculates the summary live.
- One click downloads the filled `.xlsx`, built on the original mark statement template with its formatting, red fail highlighting and built-in chart preserved.

## Features

| Feature | Details |
|---|---|
| Dropdown setup | Department (CSE, CSE-ETECH, MECH, ECE), Year (I-IV), Section (A-C) |
| Flexible scales | Marks entered out of 60 / 40 / 25 / 20 / 15 / 10 / 5, converted to 15 / 7.5 / 5 |
| Roster import | CSV upload or paste, up to 64 students |
| Roster Builder page | Reads faculty Excel/CSV sheets, keeps only valid `RA` + 13-digit register numbers, outputs clean roster CSVs |
| Special entries | `AB` (absent) and `MP` (malpractice) handled automatically |
| Live summary | Total, attended, absentees, malpractice, passed, failed, class average, pass % |
| Distribution chart | 10 performance bands, shown in the app and inside the generated Excel file |
| Excel output | Fills the official template; red highlighting adjusts to the chosen marks scale |
| Privacy | Everything runs in the browser. No student data is uploaded anywhere |

## How it works

The app is a single static HTML file. The official `.xlsx` template is embedded inside it. When you click **Generate**, the app opens the template in the browser using [JSZip](https://stuk.github.io/jszip/), writes the values into the template's cells, and downloads the result. Because only cell values are changed, the template's styling, merged cells, conditional formatting and chart stay intact.

No backend, database or server-side code is required.

## Quick start

1. Open the hosted link (or open `index.html` in a browser).
2. Upload your class roster CSV (see format below).
3. Fill in the test details.
4. Enter the marks.
5. Check the summary and chart.
6. Click **Generate filled mark statement (.xlsx)**.

For the full step-by-step guide, see [USER_GUIDE.md](USER_GUIDE.md).

## CSV formats

**Students (required)**
```
RegisterNumber
RA2411003040005
RA2411003040006
```

**Optional overrides** for the dropdown lists: `departments.csv` (`Department,Abbreviation`), `years.csv` (`Year`), `sections.csv` (`Section`).

## Project files

```
index.html               Main page: mark sheet generator (template embedded)
roster.html              Roster Builder: extracts register numbers from faculty Excel sheets
students_template.csv    Sample class roster
departments_template.csv Sample department list
years_template.csv       Sample year list
sections_template.csv    Sample section list
USER_GUIDE.md            Detailed usage instructions
LICENSE                  Proprietary license (all rights reserved)
```

## Limitations

- Supports a single mark statement layout (up to 64 students on one sheet).
- Data is saved in the browser of the device being used; it is not shared across devices or users.
- The app does not check that a mark is within the allowed range, so faculty should verify entries.
- The JSZip library is loaded from the internet, so the first load needs a connection.

## Future enhancements

- Central database and faculty login
- Multiple subjects and sections managed together
- Student-wise and semester-wise performance analytics
- Exporting PDF copies of the mark statement

## Author

G P Revanth Raj, CSE, SRMIST Vadapalani
Project mentor: Dr. P. Durgadevi
