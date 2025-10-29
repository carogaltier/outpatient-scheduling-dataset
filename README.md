# Synthetic Outpatient Scheduling Dataset (2016–2025)

![Simulated Outpatient Appointments](Simulated%20outpatient%20appointments.png)

## Description

This dataset simulates a realistic outpatient appointment scheduling system, generated using the open-source Python library **[Medscheduler (v0.2.2)](https://github.com/carogaltier/medscheduler)**.  
It is entirely synthetic — no real patient information is included — yet designed to reproduce statistically realistic appointment behaviors and patient demographics observed in real healthcare systems.

The dataset covers a **10-year simulation period (2016–2025)** and was generated using default library parameters with a fixed random seed for reproducibility.  
The configuration models a standard outpatient clinic operating **Monday to Friday, from 8:00 AM to 6:00 PM**, with 15-minute appointment intervals and approximately **90% calendar utilization**.

---

## Purpose

This dataset aims to provide a reproducible, realistic, and safe-to-use data resource for professionals and learners working in **health analytics**, **software engineering**, or **data science**.

**Intended uses include:**

- **Learning** — understanding healthcare data structures, relational modeling, and analytics workflows.  
- **Prototyping** — developing and testing dashboards, ML pipelines, or scheduling algorithms.  
- **Research & Teaching** — simulating outpatient operations without handling sensitive patient data.  
- **Portfolio Building** — demonstrating data manipulation, visualization, and reproducible modeling skills in a healthcare context.

---

## Dataset Structure

The dataset contains three main tables:

### 1. Slots Table (`slots.csv`)

| Column | Description |
|---------|-------------|
| `slot_id` | Unique identifier for each available time slot. |
| `appointment_date` | Date of the slot. |
| `appointment_time` | Scheduled time in 15-minute intervals. |
| `is_available` | Boolean flag indicating if the slot is free or booked. |
| `weekday` | Day of the week (0=Monday, …, 6=Sunday). |
| `month` | Month number of the year (1–12). |

### 2. Patients Table (`patients.csv`)

| Column | Description |
|---------|-------------|
| `patient_id` | Unique identifier for each synthetic patient. |
| `name` | Synthetic name generated using the [Faker library](https://faker.readthedocs.io/). |
| `sex` | Patient gender (“Male”, “Female”, “Non-binary”). |
| `dob` | Date of birth. |
| `age` | Age at the reference date (2025-12-01). |
| `age_group` | Age category (5-year bins, 15–90). |
| `visits_per_year` | Simulated mean annual visit frequency (≈1.2). |

### 3. Appointments Table (`appointments.csv`)

| Column | Description |
|---------|-------------|
| `appointment_id` | Unique identifier for each appointment. |
| `slot_id` | References the corresponding slot. |
| `patient_id` | References the patient. |
| `scheduling_date` | Date when the appointment was booked. |
| `appointment_date` | Date of the actual visit. |
| `scheduling_interval` | Days between booking and visit (median ≈10). |
| `status` | Appointment outcome: “attended”, “cancelled”, “did not attend”, or “unknown”. |
| `check_in_time` | Actual patient arrival time (mean ≈10 minutes early). |
| `start_time`, `end_time` | Simulated consultation times. |
| `appointment_duration` | Duration in minutes (mean ≈17, median ≈16). |
| `waiting_time` | Waiting time in minutes. |
| `age`, `sex`, `age_group` | Patient information replicated for convenience. |

---

## Key Simulation Parameters

| Parameter | Default Value | Source / Description |
|------------|----------------|-----------------------|
| Working Days | Monday–Friday | Typical outpatient operation |
| Working Hours | 08:00–18:00 | Continuous 10-hour day |
| Appointments per Hour | 4 | 15-minute slots |
| Fill Rate | 0.9 | Approx. 90% of slots filled |
| Booking Horizon | 30 days | Forward window for future bookings |
| Median Lead Time | 10 days | Typical booking delay |
| Check-in Offset | −10 min | Patients arrive early on average |
| Rebooking Intensity | “medium” | ~50% of cancellations are rescheduled |
| Visits per Year | 1.2 | Average outpatient visit frequency |
| Age Range | 15–90 years | Truncated at realistic limits |

---

## Evidence and Calibration

Medscheduler’s defaults are calibrated using open NHS datasets and published studies:

- [Ellis & Jenkins (2012)](https://doi.org/10.1371/journal.pone.0051365) – weekday attendance patterns.  
- [NHS England (2024)](https://files.digital.nhs.uk/34/18846B/hosp-epis-stat-outp-rep-tabs-2023-24-tab.xlsx) – monthly outpatient activity weights.  
- [Grande et al. (2018)](https://doi.org/10.1007/s11606-018-4407-9) – lead times and booking behaviors.  
- [Tai-Seale et al. (2007)](https://doi.org/10.1111/j.1475-6773.2006.00689.x) – consultation duration averages.  
- [Cerruti et al. (2023)](https://doi.org/10.1186/s12913-023-10379-w) – punctuality and arrival offsets.

All probabilistic models (attendance, timing, seasonality) are implemented as parameterized stochastic distributions, with optional control via random seed and noise factor for reproducibility.

---

## Reference Date and Simulation Window

- **Date range:** January 1st, 2016 – December 31st, 2025  
- **Reference date:** December 1st, 2025  

Appointments before this date are considered *historical*, while those after are *upcoming*.

---

## Licensing and Reuse

This dataset is released under the **Creative Commons Attribution 4.0 (CC BY 4.0)** license.  
You are free to use, share, and adapt it for any purpose, provided proper attribution is given.

- **Generator:** Medscheduler v0.2.2  
- **Repository:** [https://github.com/carogaltier/medscheduler](https://github.com/carogaltier/medscheduler)

---

## Suggested Citation

> González Galtier, C. (2025). *Synthetic Outpatient Scheduling Dataset (2016–2025) generated with Medscheduler* [Data set]. Zenodo.  
> [https://doi.org/10.5281/zenodo.17466783](https://doi.org/10.5281/zenodo.17466783)

---

## References

- Buttz, L. (2004). *How to use scheduling data to improve efficiency.* Family Practice Management, 11(7), 27–29. PMID: 15315285.  
- Cerruti, B., Garavaldi, D., & Lerario, A. (2023). *Patient's punctuality in an outpatient clinic: the role of age, medical branch and geographical factors.* BMC Health Services Research, 23(1), 1385. https://doi.org/10.1186/s12913-023-10379-w  
- Ellis, D. A., & Jenkins, R. (2012). *Weekday affects attendance rate for medical appointments: Large-scale data analysis and implications.* PLoS ONE, 7(12), e51365. https://doi.org/10.1371/journal.pone.0051365 
- Grande, D., Zuo, J. X., Venkat, R., Chen, X., Ward, K. R., Seymour, J. W., & Mitra, N. (2018). *Differences in Primary Care Appointment Availability and Wait Times by Neighborhood Characteristics: a Mystery Shopper Study.* Journal of General Internal Medicine, 33(9), 1441–1443. https://doi.org/10.1007/s11606-018-4407-9  
- NHS Digital. *Provisional Monthly Hospital Episode Statistics for Admitted Patient Care, Outpatient and Accident and Emergency Data.* https://digital.nhs.uk/data-and-information/publications/statistical/provisional-monthly-hospital-episode-statistics-for-admitted-patient-care-outpatient-and-accident-and-emergency-data/april-2025---may-2025  
- NHS England (2024). *Hospital Outpatient Activity 2023–24: Summary Reports 1–3.* https://files.digital.nhs.uk/34/18846B/hosp-epis-stat-outp-rep-tabs-2023-24-tab.xlsx  
- Rao, A., Shi, Z., Ray, K. N., Mehrotra, A., & Ganguli, I. (2019). *National Trends in Primary Care Visit Use and Practice Capabilities, 2008–2015.* Annals of Family Medicine, 17(6), 538–544. https://doi.org/10.1370/afm.2474  
- Tai-Seale, M., McGuire, T. G., & Zhang, W. (2007). *Time allocation in primary care office visits.* Health Services Research, 42(5), 1871–1894. https://doi.org/10.1111/j.1475-6773.2006.00689.x  
- Faker library documentation. https://faker.readthedocs.io/  


