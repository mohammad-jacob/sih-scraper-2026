# Smart India Hackathon 2026 — Problem Statement Scraper

A Python-based web scraper that automatically collects **Smart India Hackathon (SIH) 2026 problem statements** from the official SIH portal and exports them into a structured Excel (`.xlsx`) file.

The project uses **Selenium WebDriver** to interact with the SIH website, navigate through the problem-statement table, collect the available records, remove duplicates, and generate an Excel spreadsheet for further analysis.

> **Source:** [Smart India Hackathon 2026](https://www.sih.gov.in/sih2026PS)

---
## Demo Video

[![SIH 2026 Problem Statement Scraper Demo](https://img.youtube.com/vi/oV0Gv-9xMYo/sddefault.jpg )](https://youtu.be/oV0Gv-9xMYo)

---

## Features

* Automated browser-based web scraping using Selenium
* Extracts SIH 2026 problem statements from the official portal
* Handles multiple pages of problem statements automatically
* Displays up to 100 problems per page when supported
* Removes duplicate problem statements
* Exports the collected data to an Excel workbook
* Adds Excel filtering to the generated dataset
* Freezes the header row for easier navigation
* Automatically adjusts Excel column widths
* Checks the collected record count against the expected total
* Works with Google Chrome and ChromeDriver/Selenium Manager

---

## Data Collected

The generated Excel file contains the following fields:

| Column                         | Description                                                                    |
| ------------------------------ | ------------------------------------------------------------------------------ |
| `S.No.`                        | Serial number                                                                  |
| `Organization`                 | Ministry, department, organization, or institution associated with the problem |
| `Problem Statement Title`      | Title of the SIH problem statement                                             |
| `Category`                     | Problem category such as Software or Hardware                                  |
| `PS Number`                    | Official SIH problem-statement number                                          |
| `Submitted Idea(s) Count`      | Number of submitted ideas shown on the portal                                  |
| `Theme`                        | SIH theme associated with the problem                                          |
| `Deadline for Idea Submission` | Submission deadline displayed by the portal                                    |

The scraper currently expects **226 problem statements**, matching the dataset target configured in the script.

---

## Tech Stack

* **Python**
* **Selenium**
* **Google Chrome**
* **Chrome WebDriver / Selenium Manager**
* **OpenPyXL**
* **Pandas**
* **NumPy**

### Main libraries

```text
selenium
openpyxl
pandas
numpy
```

The repository includes pinned dependencies in `requirements.txt`.

---

## 📁 Project Structure

```text
sih-scraper-2026/
│
├── 📄 sih_scraper.py
├── 📄 requirements.txt
├── 📄 README.md
│
└── 📁 video/
    └── 🎥 Demo / project video
```

### `sih_scraper.py`

The main scraping program.

It:

1. Opens the official SIH 2026 problem-statement portal.
2. Waits for the problem table to load.
3. Attempts to display 100 records per page.
4. Reads the table rows.
5. Extracts the eight required fields.
6. Navigates through subsequent pages.
7. Removes duplicate problem statements.
8. Creates an Excel workbook.
9. Applies filters and formatting.
10. Saves the final dataset.
11. Reports whether the expected number of records was collected.

---

# Getting Started

## 1. Clone the Repository

```bash
git clone https://github.com/mohammad-jacob/sih-scraper-2026.git
```

Move into the project directory:

```bash
cd sih-scraper-2026
```

---

## 2. Create a Virtual Environment

### Windows

```powershell
python -m venv .venv
```

Activate it:

```powershell
.venv\Scripts\activate
```

### Linux / macOS

```bash
python3 -m venv .venv
```

Activate it:

```bash
source .venv/bin/activate
```

---

## 3. Install Dependencies

Upgrade `pip`:

```bash
python -m pip install --upgrade pip
```

Install the project's dependencies:

```bash
pip install -r requirements.txt
```

---

# Browser Requirements

The scraper uses Selenium to control **Google Chrome**.

Make sure Google Chrome is installed before running the program.

Recent Selenium versions can manage the appropriate browser driver automatically through Selenium Manager.

You can verify Selenium is installed with:

```bash
python -c "import selenium; print(selenium.__version__)"
```

---

# Run the Scraper

Run:

```bash
python sih_scraper.py
```

The program will open Chrome and navigate to:

```text
https://www.sih.gov.in/sih2026PS
```

It then processes the available problem-statement pages automatically.

At the end, an Excel file will be generated:

```text
SIH_2026_226_Problem_Statements.xlsx
```

---

# Example Output

The resulting workbook contains a sheet named:

```text
SIH 2026 Problems
```

Example structure:

```text
S.No. | Organization | Problem Statement Title | Category
      |              |                         |
      |              |                         |

PS Number | Submitted Idea(s) Count | Theme | Deadline
```

The generated spreadsheet also includes:

* Frozen header row
* Excel auto-filter
* Adjusted column widths
* Structured tabular data

---

# How the Scraper Works

```text
                ┌─────────────────────┐
                │ Official SIH Portal │
                └──────────┬──────────┘
                           │
                           ▼
                ┌─────────────────────┐
                │ Selenium WebDriver  │
                └──────────┬──────────┘
                           │
                           ▼
                ┌─────────────────────┐
                │ Load Problem Table  │
                └──────────┬──────────┘
                           │
                           ▼
                ┌─────────────────────┐
                │ Extract Table Rows  │
                └──────────┬──────────┘
                           │
                           ▼
                ┌─────────────────────┐
                │ Navigate Pages      │
                └──────────┬──────────┘
                           │
                           ▼
                ┌─────────────────────┐
                │ Remove Duplicates   │
                └──────────┬──────────┘
                           │
                           ▼
                ┌─────────────────────┐
                │ Create Excel File   │
                └──────────┬──────────┘
                           │
                           ▼
             SIH_2026_226_Problem_Statements.xlsx
```

---

# 🧪 Validation

The scraper compares the number of successfully collected records against the configured expected total.

Expected:

```text
226
```

If the number matches:

```text
SUCCESS! All 226 problem statements collected.
```

If fewer records are collected, the program displays a warning so that the result can be investigated.

This is useful because websites can change their HTML structure, pagination behavior, or available records over time.

---

# ⚠️ Important Notes

### Website changes

This scraper depends on the current structure of the SIH website.

If the SIH website changes:

* HTML element IDs
* table structure
* pagination
* column order
* JavaScript behavior

the scraper may require modifications.

### Data freshness

The generated spreadsheet represents the information available on the SIH portal when the scraper was executed.

Problem statements, submission counts, and deadlines can change.

Always verify important information on the official SIH portal before relying on the scraped dataset.

---

# Responsible Scraping

This project is intended for:

* Educational purposes
* Data analysis
* Hackathon research
* Automation learning
* Personal research

The scraper uses Selenium browser automation rather than attempting to bypass authentication, access controls, or other security mechanisms.

---

# Learning Objectives

This project is also useful for learning practical concepts in:

* Python automation
* Web scraping
* Selenium WebDriver
* DOM interaction
* Browser automation
* Pagination handling
* Data cleaning
* Duplicate detection
* Excel automation
* Data extraction
* Exception handling
* Reproducible data collection

---

# Contributing

Contributions are welcome.

If you find a bug or have an improvement:

1. Fork the repository.
2. Create a new branch.

```bash
git checkout -b feature/improvement
```

3. Make your changes.
4. Commit them.

```bash
git add .
git commit -m "Add improvement"
```

5. Push the branch.

```bash
git push origin feature/improvement
```

6. Open a Pull Request.

---

# License

This repository contains code for educational and data-extraction purposes.

The SIH problem-statement content belongs to its respective publisher and should be attributed to the **Smart India Hackathon / Innovation Cell, Government of India**.

For authoritative information, refer to the official SIH portal:

https://www.sih.gov.in/sih2026PS

---

# 👨‍💻 Author

**Mohammad Jacob**

---

## Support

If you find this project useful for learning Python, Selenium, web scraping, or SIH research, consider giving the repository a on GitHub.

---

> **Disclaimer:** This is an independent educational project and is not affiliated with, endorsed by, or sponsored by Smart India Hackathon or the Government of India.
