# Parking-Management-Solution

A **Microsoft Power Platform solution** that streamlines daily parking inspections, requests, and reporting — built using **Power Apps**, **Power Automate**, and **Power BI**.  
Designed for tablet use, the app helps staff efficiently log, review, and manage parking spaces and requests in real time.  

---

## 📋 Overview  
The **Parking Inspection Management System** enables staff to perform and review parking inspections once daily, ensuring compliance with available parking space limits and request rules.  
This solution is adaptable for school or business environments with restricted parking capacity.  

---

## 🧩 Features  

### 🖥 Power Apps (Canvas App)
**Screens Included:**
1. **Home Screen**
   - Two navigation buttons:
     - ➡️ “New Inspection”
     - 🔍 “Review Inspections”
   - Initializes inspection form using `NewForm()`.

2. **New Inspection Screen**
   - Logs new vehicle inspections.  
   - Defaults:
     - Inspection Date → Today  
     - Inspection Time → Current Hour/Minute  
   - ComboBox filters **available vehicles** not yet inspected today.  
   - Submit button creates a record and refreshes the inspection table.  
   - Navigation to “New Vehicle” screen for adding new vehicles.  

3. **Review Screen**
   - Displays **today’s inspections** using a gallery view.  
   - Columns shown:
     - Inspection ID  
     - Vehicle  
     - Inspection Date/Time  
     - Make & Model  
     - Parking Request ID and Time  
   - Includes search box to filter inspections by vehicle or request ID.  

4. **New Vehicle Screen**
   - Form for registering new vehicles with:
     - Vehicle Name  
     - Make  
     - Model  
     - Optional Vehicle Image  
   - On submit:
     - Navigates back to Home screen.  
     - Refreshes inspection data.  

---

## ⚙️ Power Automate Flow  
**Flow Name:** `Parking Request Notification`  

### 🧠 Trigger
- Dataverse → **When a row is added or modified** in the **Parking Request** table.  

### 📨 Action
- Sends a confirmation email using the **Outlook connector**.  
- **Email Subject:**  
  `Parking Request Confirmation <vehicle name>`  

- **Email Body:**  
  ```html
  Please be advised that your parking request for vehicle <vehicle name> today has been granted.  
  Request ID: <parking request name>  
  <br><br>
  Many thanks,<br>
  <b>Contoso School Administration</b><br>
  <img src="cid:SchoolLogo" alt="School Logo">

🧾 Includes dynamic school logo and formatted HTML signature.
________________________________________
📊 Power BI Dashboard
Key Insights:
•	Total available parking spaces (15 daily).
•	Daily inspection summary (performed at 5 PM).
•	Invalid parking detection (vehicles parked with active requests).
•	Rejected requests (made after 5 PM).
•	Utilization trend across days/weeks.
________________________________________
🧠 Business Logic & Rules
Rule	Description
🕔 Inspection Time	Inspections occur daily at 5 PM.
🚫 Invalid Parking	Vehicles parked with pending requests at inspection time are invalid.
⏰ Late Requests	Parking requests after 5 PM are not approved.
🚙 Capacity	Maximum of 15 spaces available daily.
🔁 Single Inspection	Each vehicle can be inspected only once per day.
________________________________________
🧱 Technology Stack
Component	Purpose
Power Apps (Canvas App)	Tablet app for inspection entry and review
Microsoft Dataverse	Data storage for Vehicles, Parking Requests, and Inspections
Power Automate	Email notification flow
Power BI	Reporting and analytics dashboard
Outlook / Office 365 Connector	Email delivery
________________________________________
🚀 How It Works
1.	Staff logs into the tablet app.
2.	Performs the 5 PM daily inspection.
3.	Power Automate sends email confirmations for approved requests.
4.	Power BI visualizes parking and inspection data for administrators.
________________________________________
📅 Future Enhancements
•	✅ Relate inspections directly to parking requests (lookup relationship).
•	✅ Add GPS tagging for inspection validation.
•	✅ Include QR code scanning for faster vehicle identification.
•	✅ Real-time dashboard refresh via Power BI streaming dataset.
________________________________________
👨‍💻 Author
Toluwani Okunola
Power Platform Developer | Data Analyst

