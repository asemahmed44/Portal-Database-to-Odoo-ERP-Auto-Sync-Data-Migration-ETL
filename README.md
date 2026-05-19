# Portal-Database-to-Odoo-ERP-Auto-Sync-Data-Migration-ETL
A robust n8n workflow designed to automate data migration and real-time synchronization between a custom web portal database and Odoo ERP.
## 🎯 Problem Solved
Manually migrating enterprise data (Invoices, Payments, and Customer Contacts) from a custom proprietary web portal to an Odoo ERP instance is time-consuming, highly complex, and prone to duplication errors. 

This workflow acts as an automated **ETL (Extract, Transform, Load) pipeline** that extracts new or updated enterprise records, transforms the data structure to match Odoo's schema, and seamlessly inserts or updates them in Odoo with strict validation.

---

## ⚡ Workflow Architecture
---

## 🔧 Tech Stack
| Tool | Role |
| :--- | :--- |
| **n8n** | Advanced workflow automation & ETL orchestration |
| **PostgreSQL / MySQL** | Source portal database engine |
| **Odoo API** | Target ERP integration (creating contacts, invoices, and payments) |
| **JavaScript (Node.js)** | Data cleaning, structuring, and type casting inside Code nodes |

---

## 📋 Key Sync Modules
The automation is divided into dedicated sync paths:
* **👥 Contact Sync:** Maps portal user profiles to Odoo `res.partner` records, ensuring no duplicate contacts are created.
* **🧾 Invoice Migration:** Extracts complex billing records, line items, and taxes, converting them into structured Odoo `account.move` objects.
* **💳 Payment Matching:** Captures transaction histories and logs them securely under Odoo payments, linking them directly to their corresponding invoices.

---

## 🚀 Setup Instructions

### Prerequisites
* n8n instance (Self-hosted or Cloud).
* Read-access credentials to the source Portal Database.
* Odoo Instance with Developer Mode enabled (Admin credentials or API Key).

### Steps to Deploy
1.  **Import:** Download and import `Portal_to_Odoo_Sync.json` into your n8n dashboard.
2.  **Database Connection:** Update the Database node with your source portal credentials (Host, DB Name, User, Password).
3.  **Odoo Connection:** Set up your Odoo node credentials (URL, Database, Username, API Key).
4.  **Field Adjustments:** Modify the `Code` node if your custom portal uses different column naming conventions.
5.  **Activate:** Set the workflow to active. It can be scheduled using a *Cron/Schedule Trigger* to poll for changes every X minutes or run continuously.

---

## 📁 Repository Structure
```bash
portal-to-odoo-sync/
├── Portal_to_Odoo_Sync.json       # The clean n8n ETL workflow file (Import this)
├── architecture-canvas.png        # Visual screenshot of the n8n ETL pipeline
└── README.md                      # Project documentation

## Author
Asem Ahmed — AI Automation
