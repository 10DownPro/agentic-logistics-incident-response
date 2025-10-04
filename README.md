# PepsiCo Delivery Delay Incident Response System

## Project Scenario  
PepsiCo’s logistics team faced repeated issues with late deliveries.  
Every delay created ripple effects: customer dissatisfaction, contractual penalties, & operational bottlenecks.  
Engineers had no single system to capture delays, escalate quickly, & measure penalty risk.  

**Solution:** Build a scoped ServiceNow application that records delays in real-time, automates escalation, & integrates AI for predictive insights.  

---

## Business Need  
The system needed to:  
- Provide structured visibility into delivery incidents.  
- Automatically notify logistics managers & assign incidents to regional ops teams.  
- Escalate based on ETA thresholds or penalty cost triggers.  
- Lay groundwork for AI-assisted predictions of late deliveries before they occur.  

---

## System Architecture  
*High-level view of app design, tables, & workflow.*  

![System Overview Diagram](./screenshots/system-overview.png)  

---

## Data Model (Custom Table)  
The **Delivery Delay** table includes:  
- `Order ID` (string)  
- `Route Number` (integer)  
- `Distance (miles)` (integer)  
- `ETA (minutes)` (integer)  
- `Penalty Cost ($)` (currency)  
- `Status` (choice: Open, Escalated, Resolved)  

![Table & Field Configuration](./screenshots/table-fields.png)  
![Delivery Delay Form Layout](./screenshots/form-layout.png)  

---

## Workflow Automation (Flow Designer)  
The **Delivery Delay Flow** executes when a new incident is logged:  
1. **Trigger**: new Delivery Delay record created.  
2. **Notify**: alert sent to Logistics Manager.  
3. **Assignment**: route assigned to Regional Ops if ETA exceeds threshold.  
4. **Escalation**: if penalty > X, escalate to Senior Ops Manager.  

![Flow Designer Trigger](./screenshots/flow-trigger.png)  
![Flow Designer Action Steps](./screenshots/flow-actions.png)  
![Test Incident Before After](./screenshots/test-incident.png)  

---

## Testing & Validation – Results
- Record successfully created & escalated per rules.
- Notifications delivered as expected.
- Escalation triggered correctly on penalty condition.

---

## Update Sets
Two Update Sets created:
- **Scoped Update Set** → Delivery Delay App (tables, flows, configs).
- **Non-Scoped Update Set** → Email templates & notifications.

**Version:** 1.0.0  
**Release Notes:** Initial release of Delivery Delay Incident Response system with escalation workflow.

---

## AI Enhancement Scenario
Future upgrade with AI Agent:
- Agent analyzes historical route data to **predict late deliveries before they occur**.
- Auto-generates Delivery Delay records for at-risk routes.
- Populates ETA & penalty risk automatically.

**Mock Input:**
```json
{
  "order_id": "ORD-67890",
  "route_number": 12,
  "predicted_eta_minutes": 220,
  "predicted_penalty_cost": 500
}
```
**Mock Output:**  
Delivery Delay record created & escalated before driver check-in.  

---

## Results & Impact
- Reduced manual reporting effort.  
- Accelerated escalation process for late deliveries.  
- Clear audit trail of delay incidents.  
- Foundation for AI-driven proactive incident response.  

---

## Next Steps
- Integrate with PepsiCo’s ERP for real delivery data ingestion.  
- Deploy AI model for predictive routing.  
- Add analytics dashboard for monitoring delivery health.  


