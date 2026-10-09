# User Guide

**Automated Student Performance Analysis and Mark Sheet Generation System**

This guide explains how a faculty member uses the system from start to finish, what each field means, how the numbers are calculated, and what to do if something goes wrong.

---

## 1. Purpose

Preparing a cycle test mark statement by hand means converting every mark, counting absentees, working out the pass percentage and drawing a chart. This system does all of that. The faculty only has to choose the class details and enter the marks. The output is the institution's own mark statement template, already filled in.

## 2. What you need

- A computer (or phone) with a modern browser such as Chrome, Edge, Firefox or Safari.
- An internet connection when the page first loads.
- A class roster as a CSV file, or the register numbers ready to paste.
- The marks for each student.
- Microsoft Excel, LibreOffice Calc or similar to open the generated file.

## 3. The workflow at a glance

1. Optionally load custom dropdown lists.
2. Load the class roster.
3. Fill in the test details.
4. Enter the marks.
5. Review the summary and chart.
6. Generate and download the Excel mark statement.

---

## 4. Step-by-step instructions

### Step 1: Reference lists (optional)

The department, year and section dropdowns already contain these values:

- **Department:** CSE, CSE-ETECH, MECH, ECE
- **Year:** I, II, III, IV
- **Section:** A, B, C

You only need this step if you want different options. Upload a CSV with a header row:

| File | Header row |
|---|---|
| Departments | `Department,Abbreviation` |
| Years | `Year` |
| Sections | `Section` |

Templates for these files can be downloaded from the links shown in this section.

### Step 2: Load the class roster

The roster is the list of register numbers for the class.

**Option A: upload a CSV file.** The file must have a header named `RegisterNumber`, then one register number per row:

```
RegisterNumber
RA2411003040005
RA2411003040006
RA2411003040007
```

**Option B: paste the list.** Open "Or paste register numbers, one per line", paste the numbers, and click **Load pasted list**.

After loading, a message shows how many students were loaded. The template holds a maximum of **64 students**. If your file has more, only the first 64 are used, and a message tells you so.

Loading a new roster replaces the old one on the screen.

### Step 3: Fill in the test details

| Field | How to fill it | Where it appears in the Excel file |
|---|---|---|
| Department | Choose from the dropdown | Department line (full name) and the Year & Sec cell |
| Year | Choose I, II, III or IV | Year & Sec cell |
| Section | Choose A, B or C | Year & Sec cell |
| Subject code | Type it, for example `21CSS101J` | Subject line |
| Subject name | Type it | Subject line, after the code |
| Faculty name | Type it | Faculty Name line |
| Marks entered out of | Choose 60, 40, 25, 20, 15, 10 or 5. This is the maximum marks of the question paper | Column headings and all calculations |
| Convert to | Choose 15, 7.5 or 5. This is the scale the marks are converted to | Converted marks column |
| Batch | Type it, for example `2024-2028` | Batch cell |
| Date of exam | Pick the date | Date of Exam cell and the attendance heading |
| Test name | For example `Cycle Test - 01` | Title of the sheet |

**Note:** The Batch box starts with the value `2024-2028`. Change it to your actual batch before generating.

**Your entries are saved automatically** in the browser, so you can close the page and continue later on the same device.

### Step 4: Enter the marks

The marks table lists every student from the roster. For each student there are two boxes:

- **Att %**: the attendance percentage. It starts at 100. Change it if needed.
- **Marks**: the mark obtained.

What you can type in the Marks box:

| Entry | Meaning |
|---|---|
| A number such as `22` or `17.5` | Marks obtained out of the "Marks entered out of" value |
| `AB` (any case) | Absent |
| `MP` (any case) | Malpractice |
| Left empty | Not graded yet |

The **Converted** column fills in immediately as you type. For example, 22 out of 25 converted to 7.5 shows 6.60. `AB` and `MP` entries appear as `AB` and `MP`.

**Faster entry by pasting.** Open "Paste marks", then paste lines in either format (tab or comma separated):

```
RA2411003040005    100    22
RA2411003040006    100    AB
```
or just register number and marks:
```
RA2411003040005    22
RA2411003040006    AB
```

Click **Apply to matching students**. Lines are matched by register number. A message says how many lines matched. Lines whose register number is not in the roster are skipped, so check for typing mistakes if the count is lower than expected.

You can paste straight from Excel by copying the columns.

**Be careful:** The app does not stop you from typing a mark higher than the maximum (for example 30 out of 25). Check your entries.

### Step 5: Review the summary and chart

The summary cards update after every change.

| Card | Meaning |
|---|---|
| Total students | Number of students in the roster |
| Attended | Students who have a mark or malpractice entry, excluding absentees |
| Absentees | Students marked `AB` |
| Malpractice | Students marked `MP` |
| Passed | Attended minus failed minus malpractice |
| Failed | Students with a numeric mark below the pass mark |
| Class average | Average of all numeric marks, shown out of the maximum |
| Pass % | Passed divided by (attended minus malpractice), as a percentage |
| Not yet graded | Students with an empty Marks box |

**Pass mark rule:** The pass mark is **half** of the "Marks entered out of" value. For example 12.5 for a 25-mark test, 30 for a 60-mark test. A mark below that counts as a fail.

**Distribution chart:** The bars show how many students fall into each 10% band of the maximum marks: 0-9, 10-19, up to 90-100. Absentees and malpractice cases are not counted in the bars.

### Step 6: Generate the Excel mark statement

Click **Generate filled mark statement (.xlsx)**.

- If some students have no marks entered, the app asks whether to continue. Choosing **OK** leaves those rows blank in the Excel file.
- The file downloads with a name like `I_CSE_A_CycleTest-01_MarkStatement.xlsx`.
- On some hosting platforms a save dialog appears first. Confirm it to save.

Open the file in Excel or a similar program and check it before printing or submitting.

---

## 5. Understanding the generated Excel file

The file is your institution's own mark statement template with the following filled in.

**Header area**
- Department, Batch, Year & Sec (for example `I -CSE-A`), Subject code and name, Faculty name, Date of exam and the test title.
- Column headings update to match your choice, for example "For 25" and "For 7.5".

**Student area**
- Up to 32 students in the left block and a further 32 in the right block, so 64 in total.
- For each student: register number, attendance %, marks and converted marks.

**Conversion formula**

> Converted mark = Mark × (Convert-to value ÷ Marks-entered-out-of value)

Example: 18 out of 40 converted to 15 gives 18 × 15 ÷ 40 = 6.75. Values are rounded to two decimal places.

**Summary area at the bottom**
Total students, attended, absentees, malpractice, passed, failed, class average and pass percentage, using the same rules as the on-screen summary.

**Distribution table and chart**
The band counts are filled in and the template's built-in chart shows them.

**Red highlighting**
The template highlights failing marks in red. The system adjusts this limit to the scale you chose, so a 60-mark test highlights marks below 30, and the converted column highlights values below half of the converted scale.

**Note:** The numbers in the file are fixed values, not live Excel formulas. If you edit a mark inside Excel, the summary will not recalculate. To change a mark, fix it in the app and generate the file again.

---

## 6. A worked example

**Scenario:** Section A of Year I CSE, a test out of 25, converted to 7.5, with five students.

| Register number | Marks entered |
|---|---|
| RA001 | 22 |
| RA002 | AB |
| RA003 | 15 |
| RA004 | MP |
| RA005 | 9 |

- Converted marks: 6.60, AB, 4.50, MP, 2.70.
- Pass mark is 12.5, so RA005 (9) fails.
- Total = 5, Absentees = 1, Malpractice = 1, Attended = 4.
- Failed = 1, Passed = 4 - 1 - 1 = 2.
- Class average = (22 + 15 + 9) ÷ 3 = 15.33.
- Pass % = 2 ÷ (4 - 1) = 66.67%.

---

## 7. Saving, privacy and using several devices

- Roster, marks and test details are saved in your browser on **this device only**.
- No student data is sent to any server.
- Clearing browser data, using private/incognito mode, or switching to another browser or device means the saved entries will not be there.
- To keep a permanent record, download the Excel file and store it safely.

## 8. Troubleshooting

| Problem | What to do |
|---|---|
| "JSZip failed to load" when generating | The internet connection or a network filter is blocking the library. Check your connection, reload the page and try again |
| "Load a class roster first" | Upload or paste the roster before generating |
| "No RegisterNumber column found" | The first row of the CSV must be exactly `RegisterNumber` |
| Fewer students loaded than expected | The template supports 64 students; extra ones are ignored |
| Pasted marks did not apply | The register numbers must match the roster exactly. Check for spaces or typing differences |
| The file did not download | Allow downloads for the site in the browser, or try another browser |
| Chart looks old in a viewer | Some non-Excel viewers do not refresh charts. Open the file in Microsoft Excel |
| Marks disappeared | They were saved in a different browser or device, or browser data was cleared |
| Wrong department name in the sheet | The full department name is set inside the app. Ask the developer to correct the wording |

## 9. Limitations to keep in mind

- The tool produces one mark statement layout only.
- The maximum is 64 students per sheet.
- Marks above the maximum are not rejected, so check your entries.
- Data is stored per device and is not shared between faculty.
- Always review the generated file before official submission.

## 10. Frequently asked questions

**Do I need to install anything?** No. It runs in the browser.

**Does it work on a phone?** Yes, the page adapts to small screens, although entering marks is easier on a computer.

**Can two faculty use it at the same time?** Yes, but each person's data stays on their own device.

**Can I generate the file again after correcting a mark?** Yes. Change the mark in the app and click Generate again.

**What if a student has no mark yet?** Leave the box empty. The student counts in the total but not in attended, passed or failed, and the row stays blank in the file.

**Is my data safe?** The data never leaves your device, except for the Excel file you choose to download.
