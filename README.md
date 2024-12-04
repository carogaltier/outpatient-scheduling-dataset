# medical-appointment-scheduling
This dataset simulates a medical appointment scheduling system, designed to demonstrate practical applications of data generation techniques in the healthcare field. Although synthetic, the data is based on real-world values to enhance its realism and utility.

## Purpose

The primary goals of this dataset are:

- **Learning**: To help newcomers to data science or software development understand how data is structured and applied in real-world contexts.
- **Prototyping**: To provide a foundation for developing and testing projects or features related to appointment scheduling systems.
- **Portfolio Showcase**: To demonstrate skills in data manipulation, software development, and system design within a healthcare context.

## Dataset Structure

The dataset contains three main tables:

### 1. Slots Table

- **slot_id** *(Integer)*: Unique identifier for each time slot.
- **appointment_date** *(Date)*: Date of the appointment.
- **appointment_time** *(Time)*: Scheduled time of the appointment (15-minute intervals).
- **is_available** *(Boolean)*: Indicates if the slot is available (True) or not (False).

### 2. Patients Table

- **patient_id** *(Integer)*: Unique identifier for each patient.
- **name** *(String, up to 60 characters)*: Full name of the patient.
- **sex** *(String)*: Gender of the patient ('Male', 'Female', 'Non-binary').
- **dob** *(Date)*: Date of birth in YYYY-MM-DD format.
- **insurance** *(String, up to 30 characters)*: Name of the patient's insurance provider from a predefined list of fictitious names.

### 3. Appointments Table

- **appointment_id** *(Integer)*: Unique identifier for each appointment.
- **slot_id** *(Integer)*: References the slot in the Slots table.
- **scheduling_date** *(Date)*: Date when the appointment was scheduled.
- **appointment_date** *(Date)*: Date of the appointment.
- **appointment_time** *(Time)*: Scheduled time of the appointment.
- **scheduling_interval** *(Integer)*: Days between scheduling date and appointment date.
- **status** *(String)*: Appointment status ('available', 'scheduled', 'completed', 'cancelled', 'no-show').
- **check_in_time** *(Time)*: Actual time the patient checked in.
- **appointment_duration** *(Float)*: Duration of the appointment in minutes.
- **start_time** *(Time)*: Actual start time of the appointment.
- **end_time** *(Time)*: Actual end time of the appointment.
- **waiting_time** *(Float)*: Waiting time in minutes.
- **patient_id** *(Integer)*: References the patient in the Patients table.
- **sex** *(String)*: Gender of the patient.
- **age** *(Integer)*: Age of the patient.
- **age_group** *(String)*: Age group category of the patient.

## Key Parameters

The dataset simulates a medical office operating Monday to Friday, from 8:00 AM to 6:00 PM, with appointments scheduled every 15 minutes (4 per hour). Key parameters include:

- **Booking Horizon**: Appointments can be scheduled up to 30 days in advance.
- **Fill Rate**: 90% of available slots are filled.
- **Rebooking Rate**: 50% of cancelled appointments are rescheduled.
- **Average Scheduling Interval**: Appointments are scheduled an average of 7 days in advance.
- **Appointment Duration**:
  - Mean: 17.4 minutes.
  - Median: 15.8 minutes.
- **Patient Arrival Times**:
  - 84.4% of patients arrive before their scheduled time.
  - Average early arrival: 10 minutes early.
- **Appointment Status Rates**: Outcomes include:
  - Attended.
  - Cancelled (in advance).
  - No-show (missed without cancellation).
  - Unknown (unspecified or indeterminate).
- **Future Appointments**: Simulated for the next 30 days, following an exponentially decreasing occupancy rate model.
- **Patient Visit Frequency**: Patients visit an average of 1.2 times per year.
- **Age Groups**: Defined in 5-year intervals, starting at 15 years and above.
- **Insurance Data**:
  - A Pareto principle distribution is applied to simulate realistic market coverage.
  - Fictitious names are used for insurance providers.

## Patient Demographics

- **Names**: Generated using the Faker library to create realistic, unique names.
- **Age and Sex**: Based on real-world outpatient attendance data, excluding pediatric patients (under 15 years).

## Date Ranges

- **Covered Period**: January 1, 2015, to December 31, 2024.
- **Reference Date**: December 1, 2024, dividing past attended appointments from future appointments.

---

## References

1. Tai-Seale, M., McGuire, T. G., & Zhang, W. (2007). *Time allocation in primary care office visits.* Health Services Research, 42(5), 1871–1894. [https://doi.org/10.1111/j.1475-6773.2006.00689.x](https://doi.org/10.1111/j.1475-6773.2006.00689.x)
2. Cerruti, B., Garavaldi, D., & Lerario, A. (2023). *Patient's punctuality in an outpatient clinic: the role of age, medical branch and geographical factors.* BMC Health Services Research, 23(1), 1385. [https://doi.org/10.1186/s12913-023-10379-w](https://doi.org/10.1186/s12913-023-10379-w)
3. NHS England. (2024). *Outpatient appointment numbers and percentages for selected attendance types 2023-24.* Hospital Episode Statistics.
4. Rao, A., Shi, Z., Ray, K. N., Mehrotra, A., & Ganguli, I. (2019). *National Trends in Primary Care Visit Use and Practice Capabilities, 2008–2015.* Annals of Family Medicine, 17(6), 538–544. [https://doi.org/10.1370/afm.2474](https://doi.org/10.1370/afm.2474)


## Author

**María Carolina González Galtier**

- [Profile](https://github.com/carogaltier "María Carolina González Galtier")

## License
[GNU General Public License v3.0](https://choosealicense.com/licenses/gpl-3.0/)

## 🤝 Support

Contributions, issues, and feature requests are welcome!

Give a ⭐️ if you like this project!
