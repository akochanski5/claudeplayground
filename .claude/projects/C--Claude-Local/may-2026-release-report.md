# May 2026 Production Report

**WD Development Project | May 1–31, 2026**
**Tickets promoted from IN RELEASE → IN PRODUCTION: 13**

---

## Section One: Promoted to Production – Executive Summary

---

### Estimated Delivery Date in Customer Notifications
*Epic WD-1140 | Tickets: WD-1157, WD-1184, WD-1185*

Three related improvements work together to bring estimated delivery dates into customer-facing shipment notifications — completing the end-to-end delivery of this capability.

**WD-1157 – Shipment Estimated Delivery Date Field**
The system now correctly captures and stores the estimated delivery window start date for each shipment. This field is formatted as a clean date value (free of timezone complications), providing an accurate foundation for displaying delivery dates across all notification channels.

**WD-1185 – Estimated Delivery Date in Notification Events**
The shipment event pipeline has been updated to include the estimated delivery date alongside other standard shipment details (such as shipped date and carrier information). This ensures the delivery date is available to the notification engine at the moment customer emails and SMS messages are triggered.

**WD-1184 – Estimated Delivery Date Merge Field Activation**
The `EXPECTED_DELIVERY_DATE` merge tag is now fully populated and delivered through notification workflows. A bug that caused this field to appear blank in Out-for-Delivery notifications has been resolved. Clients who include this merge tag in their email or SMS templates will now see the estimated delivery date appear correctly for every shipment.

> **Business Impact**: Customers receiving shipment notifications can now see when their order is expected to arrive — reducing inbound "where's my order?" inquiries and improving the overall delivery experience.

---

### Lot Control, Serialization & Marketplace Product Flags
*Epic WD-320 | Tickets: WD-699, WD-700, WD-712, WD-714*

A full end-to-end implementation adding three new product-level configuration options for clients with premium tracking requirements or marketplace selling programs. Changes span the Portal, the data transmission layer, and the warehouse management system.

**WD-699 – New Product Flags in Salesforce**
Three new settings are now available on every product/SKU record:
- **Lot Control** — tracks inventory in defined lots, required for certain compliance or premium programs (applies additional fees; can only be set when a product is first created).
- **Serialized** — assigns a unique identifier to each individual bottle or unit (applies additional fees).
- **Marketplace SKU** — marks a product as available for marketplace or third-party seller channels.

**WD-700 – Product Flags Sent to the Warehouse**
When product information is transmitted to the warehouse management system, it now includes the Lot Control and Serialized flags. This ensures warehouse operations are aligned with how clients have configured their SKUs.

**WD-712 – Warehouse System Support for Lot Control & Serialization**
The warehouse management system has been updated to accept and store the Lot Control and Serialized flags for each product. Both flags default to "No" unless explicitly enabled. The lot control setting is applied at product creation and cannot be changed after a product is registered.

**WD-714 – Product Flags Available in the Portal & API**
Clients and administrators can now view and configure the Lot Control, Serialized, and Marketplace SKU flags directly in the WineDirect Fulfillment Portal when creating or editing products. These settings are also accessible via the REST API for clients managing products programmatically.

> **Business Impact**: Clients with compliance tracking, premium bottle-level traceability, or marketplace selling programs can now configure these requirements directly in the portal. This lays the groundwork for automated lot and serial number tracking through the full fulfillment process.

---

### UPS 3-Attempt Delivery Configuration
*Epic WD-1079 | Tickets: WD-1136, WD-1137*

Two related changes deliver per-client configuration support for UPS to make up to three delivery attempts before returning a package to the warehouse.

**WD-1136 – New UPS 3-Attempt Settings**
Two new configuration fields have been added at the order type level: one to enable the 3-attempt delivery option and one to specify the alternate UPS carrier code (NI1) that activates this behavior. These settings allow individual clients to opt into the 3-attempt program independently of other clients.

**WD-1137 – UPS NI1 Carrier Code Routing**
When a wine or alcohol shipment belongs to a client with the 3-attempt flag enabled, the system will now automatically route it through the NI1 UPS carrier code instead of the standard UPS code. This behavior is active across all four WineDirect fulfillment centers (Glenwillow OH, Napa/PSO, Sonoma/SHW, and SMA). Orders will receive up to three delivery attempts before being returned — reducing failed delivery rates and improving customer satisfaction.

> **Business Impact**: Clients who experience high rates of missed deliveries (e.g., residential customers with variable schedules) can now opt into a 3-attempt delivery program, improving successful delivery rates before packages are returned to the warehouse.

---

### General Updates

**WD-571 – Separate Internal and External Product Descriptions (Commerce7 Integration)**
For clients using the Commerce7 integration, product descriptions are now managed separately for two distinct purposes. The *internal* description is used by warehouse staff during quality control and picking operations. The *external* description is what appears on packing slips and customer-facing documents. Clients control the external description; operations staff manage the internal one. This change improves warehouse workflow accuracy without affecting any customer-facing content.

---

**WD-489 – Improved Inventory Adjustment Options in the Dashboard**
When operations staff process an inventory out-pick and identify a quantity discrepancy, they can now specify whether the adjustment should be recorded in both the fulfillment system and the warehouse system (for physically missing inventory) or in the fulfillment system only (for a system-level discrepancy that doesn't reflect an actual physical shortage). New adjustment codes have also been added to correctly handle storage subinventory types, including standard storage, bonded storage, and long-term storage.

> **Business Impact**: Operations teams have clearer, more precise tools for resolving inventory discrepancies — reducing the risk of inaccurate inventory records cascading into order fulfillment issues.

---

**WD-1181 – Operational Conditions Surcharge Now Displays Correctly in Invoice Exports (Bug Fix)**
The Operational Conditions Surcharge (OCS) — a carrier-imposed fee that appears as a line item on client invoices — was not displaying in the Excel export of the Direct Shipping Invoice report. The column mapping has been corrected, and OCS values now appear alongside the Temperature Control Linehaul Fee in the exported file.

> **Business Impact**: Finance and accounting teams relying on the invoice Excel export for reconciliation will now see complete billing data, including all OCS charges.

---

**WD-634 – Warehouse Case Quantity Preserved When Products Are Updated (Bug Fix)**
When an existing product record was updated or re-synced with the warehouse management system, the system was incorrectly resetting the case pack quantity (units per case) to a default value of 12 — overwriting the actual configured value. This has been fixed: if a product already exists in the warehouse system, its case quantity will be left unchanged during updates. Only newly created products will receive a default case quantity assignment.

> **Business Impact**: Clients with non-standard case quantities (e.g., 6-packs, 3-packs) will no longer see those quantities silently reset during routine product updates, preventing picking and inventory errors downstream.

---

## Section Two: Mintlify-Compatible MDX Release Notes

*The following is formatted for direct use in the WineDirect Fulfillment documentation site (docs.winedirectfulfillment.com). Save as `v26.5.1-release.mdx`.*

```mdx
---
title: "v26.5.1 Release"
description: "May 2026"
---

# v26.5.1 Release

v26.5.1 Release - May 2026

### New Features

* **Notifications**: The **Estimated Delivery Date** merge tag is now fully active in shipment notification workflows. Notification templates that include the `EXPECTED_DELIVERY_DATE` merge field will now display the correct estimated arrival date for each shipment in customer emails and SMS messages. A bug causing this field to appear blank in Out-for-Delivery notifications has also been resolved. *(WD-1157, WD-1184, WD-1185)*

* **Portal**: Added three new product configuration flags — **Lot Control**, **Serialized**, and **Marketplace SKU** — to the product create and edit pages in the Portal. Lot Control designates a SKU for lot-tracked inventory management; Serialized assigns a unique identifier to each individual unit; Marketplace SKU marks a product as available for third-party or marketplace selling programs. All three flags are also accessible via the REST API. *(WD-699, WD-714)*

* **System**: Updated the product data transmission pipeline to include the Lot Control and Serialized flags when sending product information to the warehouse. The warehouse management system has been updated to accept and store these settings; both flags default to "No" unless explicitly enabled, and lot control may only be set at product creation. *(WD-700, WD-712)*

* **System**: Added per-client configuration support for **UPS 3-Attempt Delivery** (NI1 carrier code). New settings at the order type level allow individual clients to opt into this program. When enabled, alcohol shipments automatically route through the NI1 UPS carrier code, triggering up to three delivery attempts before a package is returned to the warehouse. Active across all four WineDirect fulfillment centers. *(WD-1136, WD-1137)*

---

### Improvements to Existing Features

* **C7**: Product descriptions in the Commerce7 integration are now managed separately for internal and external use. The internal description is used by warehouse staff during quality control and picking operations; the external description appears on packing slips and customer-facing documents. *(WD-571)*

* **Portal**: Operations staff processing an inventory out-pick can now specify whether a quantity adjustment should be applied to both the fulfillment system and the warehouse system (physically missing inventory) or to the fulfillment system only (system-level discrepancy). New adjustment codes have been added to support storage subinventory types including standard storage (STS), bonded storage (BOND), and long-term storage (LTS). *(WD-489)*

---

### Bug Fixes

* **Billing**: Resolved an issue where Operational Conditions Surcharge (OCS) values were not displaying in the Excel export of the Direct Shipping Invoice report. Column mapping has been corrected; OCS charges now appear correctly alongside the Temperature Control Linehaul Fee in the exported file. *(WD-1181)*

* **WMS**: Fixed a bug where updating or re-syncing an existing product would incorrectly reset the case pack quantity to a default value of 12. The system now preserves the existing case quantity for products already registered in the WMS; the default is only assigned to newly created products. *(WD-634)*
```
