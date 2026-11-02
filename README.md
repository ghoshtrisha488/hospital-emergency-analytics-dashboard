# 🏥 Hospital Emergency Room (ER) Analytics & Patient Flow Dashboard

![Dashboard Overview]
<img width="1912" height="1011" alt="image" src="https://github.com/user-attachments/assets/89bbc58b-d6a0-4748-89e2-85b45273f4b3" />
<img width="1912" height="1017" alt="image" src="https://github.com/user-attachments/assets/e0351b2c-c9de-4f66-af9f-c489e73402d7" />
<img width="1911" height="1010" alt="image" src="https://github.com/user-attachments/assets/aa9cd9b9-7904-4a69-8e2b-f274bbf01844" />
<img width="1906" height="1011" alt="image" src="https://github.com/user-attachments/assets/f3e254c7-9fbf-4e62-9d1b-d1f987bd7a8b" />





## 📌 Project Overview
This Power BI project provides real-time and historical analytics on **Hospital Emergency Department Operations, Patient Triage Management, Wait Times, and Resource Allocation**. 

The primary objective of this dashboard is to assist clinical leadership, ER unit managers, and hospital administrators in optimizing **patient throughput**, reducing **Door-to-Doctor initial wait times**, monitoring **ESI (Emergency Severity Index) triage distribution**, and balancing **bed occupancy rates**.

---

## 📊 Key Healthcare Operational Metrics & Insights
* **Patient Volume Tracking:** Total ER admissions categorized by arrival mode (Ambulance vs. Walk-in), peak hours, and day-of-week trends.
* **Wait Time Analytics:** Door-to-Doctor wait times, treatment length of stay (LOS), and discharge times broken down by acuity levels.
* **Triage Severity Distribution:** Patient allocation across **ESI Levels 1 to 5** (Resuscitation down to Non-Urgent).
* **Capacity & Throughput Management:** Hospital bed utilization, admission vs. discharge rates, and Left Without Being Seen (LWBS) ratios.

---

## 🛠️ Data Architecture & Pipeline
1. **Data Sanitization & Compliance:** All patient records were completely anonymized/synthetic to ensure compliance with HIPAA/data privacy protocols (no real PII/PHI used).
2. **Data Cleaning & Transformation (Power Query):**
   * Standardized datetime timestamps to calculate accurate duration intervals (Arrival Time, Triage Time, Physician Contact, Discharge/Admission Time).
   * Handled missing value logic for patient transfer codes and specialized clinical notes.
   * Constructed custom age bins (*0-17 Pediatric*, *18-64 Adult*, *65+ Senior*) and acuity groups.
3. **Data Modeling (Star Schema):**
   * Built a optimized relational schema with `Fact_ER_Visits` at the grain of individual patient encounters.
   * Linked dimension tables: `Dim_Patients`, `Dim_Physicians`, `Dim_Triage_Level`, and `Dim_Date_Time`.

---

## 📐 Core DAX Measures & Calculations

Below are key custom DAX measures engineered for hospital operational analysis:

* **Total ER Admissions:**
  ```dax
  Total ER Admissions = COUNTROWS('Fact_ER_Visits')
