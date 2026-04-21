# Data Center SLA Analytics: Environmental Stability & Power Performance Using SPC
This project designs and implements a data-driven SLA analytics framework to monitor environmental stability and power performance in a data center.

It transforms raw telemetry into KPI-driven dashboards that track thermal behavior, humidity control, liquid cooling consistency, and energy utilization across Building 1 Areas A–D and Core using Statistical Process Control (SPC).

## Business Problem
Data center operations lacked **standardized SLA thresholds** for environmental and power systems, limiting visibility into:
- Operational stability across different areas
- Risk exposure due to temperature or humidity excursions
- Energy efficiency and power performance inconsistencies
  
Additionally, the absence of unified KPIs made it difficult to compare performance across systems and identify underperforming zones.

## Solution
A complete analytics pipeline was developed to address these challenges:
- Cleaned and standardized multiple raw telemetry datasets from the BMS
- Designed a unified data model across environmental and power systems
- Implemented SPC-based SLA thresholds (2-sigma approach)
- Built KPI-driven dashboards to monitor stability and performance

The solution bridges the gap between raw telemetry and decision-making by enabling both operational monitoring and analytical insight generation.

## KPI Framework
### Operational Stability KPIs
- **Stability %** → Percentage of time within control limits 
- **Out-of-Control Events** → Number of excursions beyond SLA thresholds 
- **ΔT (Cooling Differential)** → Indicator of cooling effectiveness 

### Energy Performance KPIs
- **PUE (Power Usage Effectiveness)** → Efficiency of power utilization 
- **Power Stability %** → Variability in energy consumption 
- **IT vs Total Load Ratio** → Alignment between IT demand and total power usage

## Data & Modeling
- Integrated 7 independent datasets with inconsistent structure and naming  
- Performed extensive data cleaning and normalization using Power Query (M)  
- Standardized tagging conventions across systems and areas  
- Designed and implemented a dimensional data model (fact and dimension tables) to enable scalable cross-system analysis  

### Key Modeling Features
- Time-based aggregation at the timestamp level  
- Unpivoted structure for scalable KPI analysis  
- Tag classification by System / Metric / Subgroup for flexible slicing  
- Dimensional modeling based on star schema principles to support analytical queries

## Dashboard Pages
The Power BI dashboard is structured into five analytical views:

**1. Air Temperature – Distribution Systems**
- Supply, Return, and ΔT control charts 
- Stability monitoring by system
  
**2. Cooling Performance – CRAH Units (Core)**
- Control temperature analysis 
- Distribution and variability assessment

**3. Environmental Stability – Humidity** 
- Relative humidity trends and excursions 
- Sensor-level stability comparison 

**4. Thermal Stability – Liquid Cooling (TCS)** 
- Node temperature control performance 
- Distribution and out-of-control detection 

**5. Power Utilization Analysis** 
- IT vs Total Load trends 
- PUE and energy stability metrics

## Key Insights
**1. Thermal Stability vs Energy Efficiency Decoupling**

Environmental systems across all areas maintain high stability (92–100%), while power performance shows significantly lower stability (~65–70%).  
This indicates a structural decoupling between thermal control and energy efficiency.

**2. Area C Identified as a Multi-System Hotspot**

Area C exhibits the highest instability across multiple systems:
- Air Supply: 3 out-of-control events (89.3% stability) 
- Liquid Cooling: 3 out-of-control events (89.3% stability)

This suggests localized operational inefficiencies rather than isolated anomalies.

**3. Critical Anomaly in Core Power Metrics**

The Core shows stable cooling performance, but extreme PUE values and near-zero power stability.  
This strongly suggests a data quality or measurement anomaly in power telemetry.

**4. Event-Driven Instability Pattern**

Instability appears as discrete out-of-control events rather than continuous drift.  
This suggests deviations are driven by transient operational conditions.

**5. Operational Variability Across Areas**

Performance differences between areas highlight lack of standardization:  
- Humidity is perfectly stable in Areas A and D (100%) but variable in others  
- Liquid cooling ranges from 100% (Area B) to 89.3% (Area C).

## Tools & Technologies
- **Power BI** → Data visualization and dashboard development 
- **Power Query (M)** → Data transformation and ETL 
- **Statistical Process Control (SPC)** → SLA definition and monitoring 
- **Data Modeling (Star Schema principles)** → Structured analytics layer

## Repository Structure
```bash
data-center-sla-analytics/
│
├── data/          # Anonymized datasets (raw and cleaned)
├── dashboard/     # Power BI file (.pbix)
├── images/        # Dashboard screenshots
└── README.md
```
## Future Improvements
- Implement real-time data ingestion for continuous SLA monitoring  
- Develop automated alerting based on SPC rule violations  
- Perform correlation and multivariate analysis between thermal variables (ΔT, CRAH, liquid cooling) and power utilization to identify key efficiency drivers
- Introduce predictive models for anomaly detection and early failure identification  
- Enhance data validation and anomaly detection for power telemetry  
- Expand the model to support cross-system performance optimization and energy efficiency analysis  

## Dashboard Preview
