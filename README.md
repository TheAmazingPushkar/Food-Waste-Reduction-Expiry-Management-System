# 🥗 Food Waste Reduction & Expiry Management System

> **Project Mission:** Minimize household and organizational food waste through smart inventory tracking, automated expiration alerts, and actionable usage suggestions.

---

## 📌 Project Overview

| Property | Details |
| :--- | :--- |
| **Project Name** | Food Waste Reduction & Expiry Management System |
| **Status** | 🟡 In Development |
| **Target Audience** | Households, University Dorms, Small Kitchens |
| **Primary Goal** | Reduce food wastage by at least 30% through timely notification alerts & recipe matching |

---

## 🚀 Key Modules & Features

### 📦 1. Inventory & Expiry Tracker
* **Item Cataloging:** Record item name, category, quantity, purchase date, and expiration date.
* **Storage Categorization:** Organize by Fridge, Freezer, and Pantry.
* **Status Tracking:** Mark items as `Fresh`, `Expiring Soon`, `Consumed`, or `Wasted`.

### 🔔 2. Smart Notification System
* **Automated Batch Alerts:** Daily background job checking database for expiring items.
* **Urgency Thresholds:**
  * 🔴 **Critical:** Expires within 24–48 hours.
  * 🟡 **Warning:** Expires within 3–5 days.
  * 🟢 **Safe:** > 5 days remaining.

### 📸 3. Fast Data Entry (Friction Reduction)
* **Barcode Scanning:** Fetch product names and standard shelf life using Open Food Facts API.
* **Receipt OCR (Optional):** Extract text from grocery receipts to batch-add items.

### 🍳 4. Waste Reduction Engine
* **Recipe Recommendations:** Fetch recipes based on ingredients that are expiring soon (Spoonacular / Edamam API).
* **Donation Connector:** Flag unexpired surplus food for community sharing/donations.

### 📊 5. Analytics & Impact Dashboard
* Track total money saved vs. lost to spoiled items.
* Visualize top wasted food categories to improve future shopping habits.

---

## 🛠️ Recommended Tech Stack

| Layer | Technology Selected | Notes / Alternatives |
| :--- | :--- | :--- |
| **Frontend** | React Native / Flutter | Cross-platform mobile access |
| **Backend** | Node.js (Express) / Python (FastAPI) | RESTful API server |
| **Database** | PostgreSQL / Supabase | Relational database for user data & inventory logs |
| **External APIs** | Open Food Facts API, Spoonacular API | Barcode lookup & recipe suggestions |
| **Background Jobs** | Node-Cron / Celery | Daily notification triggers |

---

## 🗄️ Database Schema Outline

### **Users Table**
* `id` (PK)
* `name` (String)
* `email` (String)
* `created_at` (Timestamp)

### **Inventory_Items Table**
* `id` (PK)
* `user_id` (FK -> Users)
* `item_name` (String)
* `category` (Enum: Dairy, Produce, Meat, Pantry, Bakery)
* `storage_location` (Enum: Fridge, Freezer, Pantry)
* `purchase_date` (Date)
* `expiry_date` (Date)
* `quantity` (Integer / Float)
* `status` (Enum: Active, Consumed, Wasted)

### **Waste_Logs Table**
* `id` (PK)
* `user_id` (FK -> Users)
* `item_id` (FK -> Inventory_Items)
* `reason` (String)
* `estimated_cost_lost` (Float)
* `logged_at` (Timestamp)

---

## 📅 Roadmap & Milestones

* [ ] **Phase 1: Setup & Core Architecture**
  * Setup database connection and API routes.
  * Create basic CRUD for inventory items.
* [ ] **Phase 2: UI & Expiry Engine**
  * Build user dashboard & item cards with color-coded expiry badges.
  * Implement background cron job for daily expiry reminders.
* [ ] **Phase 3: Integrations (Barcodes & Recipes)**
  * Add camera barcode scanner & API lookup.
  * Integrate recipe suggestion API based on expiring items.
* [ ] **Phase 4: Analytics & Testing**
  * Build waste analytics charts.
  * Perform end-to-end testing and launch MVP.

---

> 💡 **Tip:** Start by building the manual inventory CRUD and the automated daily expiration check before moving into OCR or Barcode APIs!
