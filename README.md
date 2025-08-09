# Guided Tour Insights Dashboard Generator

> **Status**: 🟡 Beta — Functional and complete for portfolio purposes, but improvements are planned.

## Project Goal
The aim of this project is to build a Python-based tool, running in a Jupyter Notebook, that automatically generates dashboards from tour booking datasets.  
It produces business insights on booking trends, guide performance, popular tours, time slots, and more.

> **Note:**  
> This project was developed for a Spanish-based company. In the final product, chart titles are in Spanish.

**No CSV files are provided in this repository.**  
Instead, the exact **dataset structures** are documented below so you can create synthetic or anonymized data to run the notebook successfully.

---

## Features
- Automated dashboard generation from monthly datasets  
- Static charts and tables for key KPIs  
- Fully reproducible with synthetic or anonymized data  
- Works directly from a Jupyter Notebook (`jupyter-notebook.ipynb`)  

---

## Required Libraries

All required Python dependencies are listed in the `requirements.txt` file.  
Install them using:

```bash
pip install -r requirements.txt
```

**`requirements.txt` contents:**
```
pandas
matplotlib
numpy
```

> The built-in `calendar` module is part of the Python Standard Library and does not need to be listed.

---

## Data Requirements

### 1) Bookings Datasets  
**Files:**  
`bookings_03-2025.csv`, `bookings_04-2025.csv`, `bookings_05-2025.csv`, `bookings_06-2025.csv`

**Schema:**

| Column Name  | Type | Format     | Description |
|--------------|------|------------|-------------|
| id           | int  | n/a        | Unique booking ID |
| TourID       | int  | n/a        | ID of booked tour (matches `tours.id`) |
| BookingDate  | date | YYYY-MM-DD | Date of booking |
| GuideID      | int  | n/a        | ID of assigned guide (matches `guides.id`) |

---

### 2) Tours Datasets  
**Files:**  
`tours_03-2025.csv`, `tours_04-2025.csv`, `tours_05-2025.csv`, `tours_06-2025.csv`

**Schema:**

| Column Name   | Type   | Format     | Description |
|---------------|--------|------------|-------------|
| id            | int    | n/a        | Unique tour ID (matches `bookings.TourID`) |
| TourName      | string | free text  | Tour name (fictional or anonymized) |
| TourLocation  | string | free text  | City or region of the tour |
| TimeStart     | time   | HH:MM      | Start time |
| TimeEnd       | time   | HH:MM      | End time |
| Op_Monday     | int    | 0/1        | Operative flag for Monday |
| Op_Tuesday    | int    | 0/1        | Operative flag for Tuesday |
| Op_Wednesday  | int    | 0/1        | Operative flag for Wednesday |
| Op_Thursday   | int    | 0/1        | Operative flag for Thursday |
| Op_Friday     | int    | 0/1        | Operative flag for Friday |
| Op_Saturday   | int    | 0/1        | Operative flag for Saturday |
| Op_Sunday     | int    | 0/1        | Operative flag for Sunday |

---

### 3) Guides Datasets  
**Files:**  
`guides_03-2025.csv`, `guides_04-2025.csv`, `guides_05-2025.csv`, `guides_06-2025.csv`

**Schema:**

| Column Name   | Type   | Format     | Description |
|---------------|--------|------------|-------------|
| id            | int    | n/a        | Unique guide ID |
| GuideName     | string | free text  | Name (fictional or anonymized) |
| GuideLocation | string | free text  | Base city or region |

---

### 4) Guide Availability Datasets  
**Files:**  
`guide_avail_03-2025.csv`, `guide_avail_04-2025.csv`, `guide_avail_05-2025.csv`, `guide_avail_06-2025.csv`

**Schema:**

| Column Name        | Type   | Format                      | Description |
|--------------------|--------|-----------------------------|-------------|
| GuideID            | int    | n/a                         | Matches `guides.id` |
| AvailabilityDate   | date   | YYYY-MM-DD                  | Availability date |
| GuideAvailability  | string | HH:MM-HH:MM (use `/` for multiple ranges) | Available time slots |

---

### 5) Guide Skills Datasets  
**Files:**  
`guide_skills_03-2025.csv`, `guide_skills_04-2025.csv`, `guide_skills_05-2025.csv`, `guide_skills_06-2025.csv`

**Schema:**

| Column Name | Type | Format | Description |
|-------------|------|--------|-------------|
| GuideID     | int  | n/a    | Matches `guides.id` |
| TourID      | int  | n/a    | Matches `tours.id` |

---

## Insights Generated
When run with correctly structured data, the notebook produces:

1. Top 10 Most Reserved Tours (Single Month) — Bar Chart  
2. Peak Booking Dates (Single Month) — Line Chart  
3. Number of Bookings Over Time — Line Chart  
4. Top 10 Most Active Guides (Single Month) — Bar Chart  
5. Top 10 Guides with Most Available Days (Single Month) — Bar Chart  
6. Guide Available Days — All Guides (Single Month) — Bar Chart  
7. Guide Available Days — All Guides (All Months Combined) — Bar Chart  
8. Guide Not Available Days (Single Month) — Bar Chart  
9. Guide Occupied Days (Single Month) — Bar Chart  
10. Guide Occupancy Rate (%) (Single Month) — Table  
11. Top 10 Guides Skilled for the Most Tours (Single Month) — Bar Chart  
12. Total Weekly Operating Days per Location (Each Month) — Bar Chart  
13. Total Weekly Operating Days per Location (All Months Combined) — Bar Chart  
14. Most Common Time Slot per Location (Each Month) — Bar Chart  

---

## How to Run

1. **Create a virtual environment** (recommended):
    ```bash
    python -m venv .venv
    source .venv/bin/activate  # On Windows: .venv\Scripts\activate
    ```

2. **Install dependencies**:
    ```bash
    pip install -r requirements.txt
    ```

3. **Start Jupyter Notebook**:
    ```bash
    jupyter notebook
    ```

4. **Open and run the notebook**:
    - Open `jupyter-notebook.ipynb`
    - Run all cells to generate the dashboards

> **Note**: You must create synthetic datasets matching the schemas described in this README, as no CSV files are included.