# Healthcare Outbreak Detection Using Big Data
This project builds a big-data pipeline to detect outbreak patterns using streaming patient vitals, medical reports, clinical notes and demographics, and generate hospital resource alerts.
PS-1 → Detect early outbreak signals  
PS-2 → Identify high-risk demographic groups  
PS-3 → Compare outbreak vs healthcare load  
PS-4 → Trigger hospital resource alerts  

## PS-1 — Early Outbreak Detection
Dataset:
• streaming vitals (JSON)
• medical test results (CSV/JSON)
• demographics (CSV)

Pipeline Steps:
1. Load vitals, demographics and test results
2. Join using patient_id
3. Detect abnormal values (fever + test threshold)
4. Compute outbreak score hourly per region
5. Dashboard: heatmap of outbreak hotspots
   
## PS-2 -groupbased_risk
Datasets:
- Patient demographics (CSV): age, gender, zip code
- Medical test results (JSON): test results with severity levels

Pipeline Steps:
1. Load demographics and test result datasets and join on patient_id
2. Create demographic groups (ex: "0–18", "19–35", "36–50", "51–70", "70+")
3. Flag abnormal cases based on medical test values / thresholds
4. Compute risk score per age group + gender + region
5. Dashboard output: Stacked bar chart — age group vs abnormal count with gender split

## PS3_RegionLevelOutbreakVsLoad
Datasets:
- Clinical notes (TXT): unstructured symptoms text
- Billing/claims (Parquet): date, procedure code, visit cost
- Demographics (CSV): patient_id, city, region

Pipeline Steps:
1. Apply NLP/text processing to convert clinical notes into structured symptom indicators
2. Join symptoms + claims + demographics using patient_id
3. Compute outbreak intensity score per region (symptom freq + claim freq)
4. Compare outbreak intensity vs healthcare load (visit count, claim amount, symptoms spike)
5. Dashboard output: Dual-axis chart — outbreak intensity vs healthcare system load per region

## PS4_HospitalAlertSystem
Datasets:
- Streaming vitals (JSON): real-time patient vitals
- Billing/claims (Parquet): hospital visit & cost information
- Patient demographics (CSV)
- Hospital mapping (CSV): region → hospital

Pipeline Steps:
1. Real-time join: vitals + claims + demographics + hospital mapping
2. Detect abnormal vital readings per region/hospital in real-time
3. Compute Hospital Stress Index (abnormality count + load %)
4. Trigger alert if abnormal cases exceed threshold AND hospital load is high
5. Dashboard output: Hospital stress index map + alert status (Normal / Warning / Critical)

PS-1 Outbreak Signals  → PS-2 Risk Groups  → PS-3 System Load →PS-4 Hospital Alerts
Developed by: Keerti Shekhawat,Rupali Goyal,Taniska Nagal 
Big Data Project – 2025




