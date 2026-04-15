# Enterprise Operations Analytics

A simulated enterprise data platform modeling operations, workforce, assets, and financial activity, designed to support end-to-end SQL analysis and business intelligence workflows.

---

## Overview

This project represents a relational database designed to simulate a real-world enterprise environment. It integrates operational, financial, and workforce data into a unified model to support analytical use cases.

The system is structured to mirror how organizations track:
- Equipment and asset lifecycle
- Maintenance activity and associated costs
- Workforce roles and regional structure
- Operational usage and utilization patterns
- Vendor relationships and financial transactions

All data within this repository is synthetic and created for demonstration purposes.

---

## Objectives

- Design a scalable relational database schema
- Simulate realistic enterprise data across multiple domains
- Perform SQL-based analysis on operational and financial metrics
- Build a foundation for business intelligence workflows (Power BI, dashboards, etc.)

---

## Data Model

### Core Entities

- **Equipment** — asset inventory, financial attributes, lifecycle status  
- **Employees** — workforce structure across operations, maintenance, and administration  
- **Regions** — organizational segmentation and supervisory hierarchy  
- **Vendors** — external service providers  

### Operational Data

- **Maintenance Logs** — service events, downtime, and activity tracking  
- **Maintenance Invoices** — cost data associated with maintenance events  
- **Equipment Usage Logs** — utilization, runtime, and operational behavior  

---

## Key Relationships

- Equipment is assigned to a region  
- Employees are assigned to regions and roles  
- Maintenance logs reference equipment and vendors  
- Maintenance invoices link to maintenance events  
- Usage logs track equipment activity by operator and project  

---

## Example Analytical Use Cases

This dataset supports analysis such as:

- Equipment utilization vs. maintenance cost  
- Vendor spend and performance analysis  
- Identification of high-cost or underperforming assets  
- Workforce distribution and operational workload  
- Idle vs. active equipment behavior  

---

## Sample Query

```sql
SELECT 
    e.equipment_id,
    COUNT(ml.maintenance_id) AS maintenance_events,
    SUM(mi.total_invoice_amount) AS total_maintenance_cost
FROM equipment e
LEFT JOIN maintenance_logs ml
    ON e.equipment_id = ml.equipment_id
LEFT JOIN maintenance_invoices mi
    ON ml.maintenance_id = mi.maintenance_id
GROUP BY e.equipment_id
ORDER BY total_maintenance_cost DESC;

---

## Tools Used
- SQLite (Database Engine)
- DB Browser for SQLite (Query Execution and Data Management)
- Microsoft Excel (Mock-Data Generation and Transformation)
- Power BI (Planned for Dashboarding and Visualization)

---

## Future Enhancements
- Expand dataset to include project-level financial tracking
- Introduce inventory and procurement tables
- Add workforce scheduling and payroll modeling
- Develop Power BI dashboards for operational insights
- Implement more advanced SQL queries (window functions, CTEs, etc.)

---

## Notes
- All data is synthetic and created for demonstration purposes
- This project is intended for portfolio and learning use only
