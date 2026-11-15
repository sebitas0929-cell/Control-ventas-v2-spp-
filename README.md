# 🛒 Sales, Inventory & Accounts Receivable ERP System (V.2SPP)

> **A relational, hybrid business operations platform built on Google Sheets and AppSheet, engineered to manage end-to-end inventory movements, parent-child sales invoicing, real-time profit/capital recovery tracking, and customer credit ledgers.**

---

## 📌 Executive Overview
**Control de Ventas V.2SPP** is a lightweight, modular ERP system designed from scratch to solve commercial operations without expensive enterprise software. Operating on a relational Parent-Child data model (`Registro_Ventas` + `Detalle_Ventas`), the system automates stock balances, tracks working capital vs. net realized profit, and manages customer accounts receivable. 

Because of its decoupled relational architecture, this core framework has been successfully adapted into other operational domains, such as Legal Case & File Management Systems (*Sistema de Gestión Legal y Expedientes*).

---

## ⚙️ Technical Architecture & Hybrid Engine

### 1. Relational Database Structure (6 Modules)
* **`Inventario`:** Master product catalog (360+ SKUs across categories like Stationery and Boutique) with image handling, real-time stock calculation, unit margins, total capital invested, warehouse capital valuation, and potential stock profit.
* **`Registro_Ventas` (Parent Table):** Master sales ledger tracking transaction IDs, customer accounts, payment methods (Cash / SINPE Móvil), bank verification flags, delivery statuses, and separated cash-flow metrics (*Recovered Cost* vs. *Cash-in-Hand Profit*).
* **`Detalle_Ventas` (Child Table - `IsPartOf`):** Line-item transaction breakdown linked to parent invoices, calculating itemized subtotals, unit costs, total line costs, and net line profit.
* **`Cuentas_Por_Cobrar`:** Master customer credit directory monitoring active balances, last payment dates, and collection statuses (`Pendiente` vs. `Cancelado`).
* **`Consulta_Cliente`:** Interactive customer lookup portal displaying account IDs, total outstanding debt, and itemized transaction/installment history.
* **`Instructivo_y_Commits`:** Built-in system governance tab featuring an operational Business Rules Dictionary and a semantic version changelog (`v2.0.0` – `v2.4.0`).

### 2. Engineering & Automation Highlights
* **Dynamic Array Formulas (`MAP` + `LAMBDA`):** Eliminated fragile drag-down formulas by implementing self-expanding array functions in row 2 to compute outbound units (`Salidas`) and physical stock (`Stock Real`) dynamically as new SKUs are added.
* **AppSheet Event Actions:** Automated restock workflows (`Ingreso_Nuevo`) that add incoming shipments to historical `Entradas` and reset temporary form fields upon saving, plus automated shrinkage/write-off handling (`CTA-MERMA`).
* **Financial & Cash-Flow Auditing:** Separates gross sales from actual cash recovery, ensuring inventory cost is accounted for before recognizing realized net profit in hand.

---

## 🛠️ Tech Stack
* **Database & Computation Engine:** Google Sheets (`MAP`, `LAMBDA`, `SUMIF`, relational cross-sheet lookups)

* **Frontend & Workflow Automation:** Google AppSheet (Parent-Child IsPartOf forms, conditional actions, image capture)

* **Governance & Documentation:** Semantic Versioning (Conventional Commits), Data Dictionary & Business Rule Mapping


