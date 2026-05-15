# Promoted to Production – Executive Summary
### April 2026 | WD Development

---

## SECTION ONE — Executive Summary

A total of **50 items** were promoted to production during April 2026, spanning billing automation, Commerce7 integration stability, shipping and carrier improvements, product management enhancements, and platform reliability. Below is a plain-language summary of what was delivered, grouped by theme.

---

### Billing & Invoicing
*WD-188 · WD-1094*

**WD-188 — Automated Temperature Control Invoicing**
The billing engine now automatically calculates and generates invoice line items for temperature-controlled shipments — wine delivered with cooling materials or climate-controlled carriers. Previously, these linehaul fees had to be tracked and billed manually. This change ensures clients are billed accurately and consistently for every temp-control delivery without staff intervention.

**WD-1094 — Operational Conditions Surcharge**
A new billing line item called "Operational Conditions Surcharge" has been added to the invoicing system. This surcharge reflects carrier-imposed fees tied to fluctuating operational conditions such as fuel costs and network capacity constraints. It now appears as a distinct, transparent line item on client invoices, making it easier to understand total shipping costs.

---

### Carrier Hold Location Notifications
*Epic WD-1148 · WD-728 · WD-1123 · WD-1131*

This group of related enhancements improves how "hold at location" shipment pickup information is communicated to wine club members.

When UPS or FedEx redirects a shipment to a retail Access Point or hold location instead of delivering it to the recipient's home, customers now receive an email or text message that includes the exact pickup address — removing the guesswork about where to retrieve their order.

**WD-728** — Notification templates now support a merge tag that dynamically inserts the current carrier hold location address into customer emails and SMS messages.

**WD-1123** — The hold location address is now recorded on the Salesforce shipment record, giving customer service teams direct visibility into where a held shipment is located.

**WD-1131** — The notification messaging system now correctly processes and delivers the pickup address through its email and SMS integration.

---

### Commerce7 Integration Improvements
*WD-598 · WD-688 · WD-697 · WD-1073 · WD-1077 · WD-1099 · WD-1102 · WD-1107 · WD-1109 · WD-1115 · WD-1143 · WD-1144*

Twelve improvements were delivered to the Commerce7 (C7) eCommerce integration this month, addressing reliability issues and adding new configuration options for winery clients.

**WD-1115 — Bundle/Gift Set SKU Sync Fix**
Bundle products (gift sets) were not syncing correctly between Commerce7 and the fulfillment portal, causing fulfillment errors. The system now correctly identifies and matches bundle variant IDs so that gift set orders are fulfilled without issue.

**WD-1099 — Point-of-Sale Orders Filter**
Commerce7 in-store (point-of-sale) orders were being incorrectly sent to the fulfillment warehouse for processing — a problem for wineries that handle in-person sales separately. A per-client on/off toggle has been added so POS orders can be excluded from fulfillment workflows where they don't belong.

**WD-1073 — Duplicate Tracking Numbers Fix**
A bug was causing duplicate tracking numbers to appear on Commerce7 orders. A pre-check has been added that prevents duplicate tracking records from being created during the fulfillment process.

**WD-1109 — Scheduled Inventory Sync Error Fix**
An error that was intermittently failing during scheduled inventory synchronization between Commerce7 and the fulfillment system has been identified and resolved.

**WD-697 — Product Sync Restricted to Matching Types**
Product updates syncing from Commerce7 to the fulfillment portal are now restricted so that only like-for-like product types can overwrite each other. This prevents mismatched product data from being incorrectly applied during sync.

**WD-1102 — Orders and Inventory Sync Control Setting**
A new configuration setting is now available that gives clients control over how orders and inventory sync between Commerce7 and WineDirect Fulfillment — providing more flexibility for client-specific workflows.

**WD-1077 — Transaction Confirmation Emails on Fulfillment**
Commerce7 now sends transaction confirmation emails to customers when a shipping fulfillment record is created, improving the end-customer communication experience.

**WD-688 & WD-1107 — Order Sales Tags Now Sync Correctly**
Two related fixes ensure that custom sales attributes and tags applied to orders in Commerce7 are now correctly captured and reflected in the fulfillment system — both when orders are first created and when they are subsequently approved.

**WD-1144 — Inventory Sync Error Fix**
An intermittent error occurring during inventory sync that had no clear error message has been diagnosed and resolved.

**WD-1143 — Non-Wine Items in Bundles Now Sync**
Non-wine products (e.g., accessories, merchandise) included in bundle packages were not appearing correctly in Commerce7 bundles. This has been fixed so all bundle components sync properly.

**WD-598 — Third-Party Dependency Upgrades**
All third-party software libraries used by the Commerce7 integration have been updated to their latest versions, improving security posture and long-term maintainability.

---

### Shipping & Carrier Updates
*WD-1085 · WD-1088 · WD-1100 · WD-1127 · WD-1133*

**WD-1133 — New "Returning" Shipment Status**
A new shipment status called **Returning** has been added to the portal. This status is applied when a shipment is on its way back to the warehouse (e.g., undeliverable or refused delivery). Operations teams and clients now have clearer, real-time visibility into shipments in the return process, rather than seeing an ambiguous status.

**WD-1088 — Estimated Ship Date Sent to Arrive55**
When uploading carrier manifests for Arrive55 shipments, the system now includes the estimated ship date in the data transmission. This helps Arrive55 better plan pickup scheduling and manage their delivery calendar.

**WD-1100 — Temperature Control Orders Now Support Damage Claims**
A bug was preventing customer service from filing damage claims for UPS and FedEx temperature-controlled shipments. When a temp-control order was delivered damaged, the claims interface returned an error and blocked submission. This has been fixed — CS teams can now file claims for temp-control orders the same way they would for standard shipments. The error messaging in the claims portal has also been made clearer.

**WD-1127 — Arrive55 Texas ZIP Code Expansion (Hotfix)**
A hotfix was deployed to add two new Texas ZIP codes — 75071 and 75072 (McKinney/Frisco area near Dallas) — to the Arrive55 DFW delivery region. Orders destined for these ZIP codes now route correctly to Arrive55 rather than being sent to an incorrect carrier.

**WD-1085 — Accurate Carrier Code in Notifications**
The notification system now retrieves the carrier code directly from the warehouse management system (WMS) for each shipment. This ensures that carrier information shown in customer notification emails and texts is always accurate and reflects the actual carrier assigned at the warehouse level.

---

### Products & Inventory
*Epic WD-320: WD-713 · WD-475 · WD-1095 · WD-1108 · WD-1132 · WD-1135*

**WD-713 — Lot Control & Serialization Product Flags (Epic WD-320)**
Product SKUs can now be flagged as subject to lot control or serialization tracking in the warehouse. These flags are transmitted from the fulfillment portal to the warehouse management system (WMS) and form the foundation for future bottle-level traceability features. This is particularly relevant for clients with compliance or premium product tracking requirements.

**WD-1132 & WD-1108 — WMS Description Field Added to Products**
A new "WMS Description" field has been added to the product setup and editing screens in the portal. This allows a separate, warehouse-specific product description to be sent to the WMS — useful for supporting internal warehouse labeling, scanning, and picking workflows without changing the customer-facing product name.

**WD-475 — Storage Subinventories in Inventory Transfers**
Two storage-specific subinventory types (used for bonded and long-term storage) are now fully supported in Inventory OUT requests and warehouse-to-warehouse transfer workflows. Previously, attempting to move storage inventory through these workflows produced errors. Clients using storage services can now initiate and complete inventory transfers correctly.

**WD-1095 — Non-Wine Product WMS Transmission Fix**
Non-wine products (such as merchandise or accessories) were failing to reach the WMS because the system was unexpectedly requiring a "bottle size" field that doesn't apply to non-wine items. This has been corrected so non-wine SKUs transmit to the warehouse without errors.

**WD-1135 — Bundle Product Lookup Fix**
A bug causing product lookup calls to fail for bundle/pack items that don't have an associated seller product has been resolved, preventing downstream errors in order processing.

---

### Order Management
*WD-396 · WD-703*

**WD-396 — Order Export Now Includes Line-Item Detail**
The order export file available from the View Orders screen has been significantly enhanced. It now includes line-item detail for every order — including SKU, quantity ordered, quantity shipped, unit price, and shipment status — with each line appearing as its own row in the export. This makes the export far more useful for order auditing, reconciliation, and downstream reporting without requiring a separate data request.

**WD-703 — Automated Retry for Compliance-Held Orders**
A nightly automated process has been added to retry orders that were previously blocked due to quantity or volume compliance limits (e.g., state shipping restrictions). Once those limits reset, the system now automatically attempts to re-process affected orders overnight, reducing the manual effort required to release these holds.

---

### Notifications & Reporting
*Epic WD-1159: WD-1165 · WD-704 · WD-1084 · WD-1086 · WD-1089 · WD-1126*

**WD-1165 — Daily Notification Usage Data Sync (Epic WD-1159)**
An automated daily data pipeline has been established to sync email and SMS notification usage metrics into the data warehouse (Snowflake). This enables ongoing reporting on how notification programs — such as shipment alerts and delivery confirmations — are being utilized across client accounts, supporting future product analytics and billing reconciliation.

**WD-704 — Estimated Delivery Date Merge Tag**
A new merge tag for **Estimated Delivery Date** is now available for use in shipment notification email and SMS templates. Winery clients can insert this tag into their notification templates, and it will dynamically populate with the expected delivery date for each individual shipment — giving wine club members better visibility into when to expect their order.

**WD-1089 — Notification Report Improvements**
The Shipment Notification Report has been updated with two improvements: timezone display has been corrected to consistently show Pacific Standard Time (PST), and the overall layout and data presentation have been improved for easier reading.

**WD-1126 — Customer Order Number Now Included in Notifications**
The customer's own order reference number was missing from certain outgoing notification emails. This has been corrected so that the customer order number is reliably included in all applicable notification communications.

**WD-1086 — Order Number Email Mapping Fix**
A follow-up fix was deployed to ensure the order number appears correctly in all email notification field mappings, closing a gap that remained from an earlier partial fix.

**WD-1084 — Shipped Date Consistency Fix**
The shipped date shown in the Shipments Report was displaying one day behind the date shown in the Order Detail screen, causing confusion during order research. Both screens now display the same, accurate shipped date.

---

### Portal & System Reliability
*WD-603 · WD-692 · WD-723 · WD-1072 · WD-1081 · WD-1097 · WD-1098 · WD-1116 · WD-1128 · WD-1129 · WD-1130 · WD-1134 · WD-1142 · WD-1145*

**WD-1130 — Live System Status on Portal Login Page (Epic WD-1119)**
The WineDirect Fulfillment portal login page now displays a live system status indicator. If there is an active incident — such as a service disruption or degraded performance — users will see an alert when they log in, keeping them informed without having to visit a separate status page. Scheduled maintenance windows are also displayed. This is powered by WineDirect Fulfillment's incident.io status page.

**WD-1145 — Client Account Deactivation Fix**
An issue preventing client accounts from being properly deactivated in the Ops Portal has been resolved. The problem was caused by deleted or inactive users who were still associated with the account, blocking the deactivation process.

**WD-603 — High-Resolution WineDirect Logo**
The WineDirect Fulfillment logo displayed in the portal has been updated to a high-resolution version, improving visual quality on high-density and large-format screens.

**WD-723 — Packing Station Infrastructure Migration**
The warehouse packing station interface has been migrated to updated infrastructure as part of ongoing platform modernization. This is a behind-the-scenes improvement that keeps the packing station tooling current and supportable.

**WD-1072 — Constellation Sub-Inventory Move Fix**
An error occurring during sub-inventory move operations for Constellation accounts has been identified and resolved.

**WD-1081 — IN-Request Retry Enhancement**
The automatic retry mechanism for inventory IN requests has been extended to also handle cases where SKUs are not yet registered in the WMS. Previously, these failures required manual resolution; they now retry automatically.

**WD-1097 — Batch Shipment Processing Fix**
An issue where shipment items arriving in different processing batches were not being handled correctly together has been resolved, improving the reliability of the shipment processing pipeline.

**WD-1098 — Inventory IN Auto-Close Logic Update**
The automatic close logic for inventory IN requests has been refined to more accurately determine when an IN request is fully complete, reducing false early-closures.

**WD-1116 — Carrier Validation Threading Fix**
A threading issue in the carrier validation service has been resolved. This fix prevents potential slowdowns or failures during periods of high order volume when many carrier validations are running simultaneously.

**WD-1128 — Carrier Validation Crash Fix**
An intermittent application crash related to system monitoring in the carrier validation service has been further stabilized, improving overall reliability.

**WD-1129 — Cancel-Out Query Reference Number Fix**
The query used to match and process inventory cancel-outs has been updated to accept only the correct reference number format, preventing incorrect record matches.

**WD-1134 — Automated Event Log Cleanup**
A scheduled job has been added to automatically purge event log records for closed orders older than 60 days. This routine maintenance reduces database bloat and improves system query performance over time.

**WD-1142 — Qlik Analytics Connected to Salesforce Production**
A Qlik analytics application has been connected to the Salesforce production environment, enabling live reporting and analytics from Salesforce data across the organization.

**WD-692 — Build Infrastructure Update**
Internal development tooling has been updated to align with modern .NET build standards (.slnx format and Directory.Build.props). This is a behind-the-scenes engineering improvement that reduces build configuration overhead.

---
---

## SECTION TWO — Mintlify-Compatible MDX

*The following is a ready-to-load `.mdx` file formatted for the WineDirect Fulfillment docs site (`docs.winedirectfulfillment.com`), matching the versioned release notes structure used for v26.x.x releases.*

```mdx
---
title: "v26.4.1"
description: "April 2026 — Billing automation, Commerce7 stability, carrier hold location notifications, and platform improvements."
---

<Update label="April 2026" description="v26.4.1">

## Billing & Invoicing

**Automated Temperature Control Invoicing** — The billing engine now automatically calculates and generates invoice line items for temperature-controlled shipments. These linehaul fees no longer require manual tracking, ensuring clients are billed accurately for every temp-control delivery. *(WD-188)*

**Operational Conditions Surcharge** — A new "Operational Conditions Surcharge" billing line item is now included on client invoices. This carrier-imposed fee reflects fluctuating operational conditions such as fuel costs and network capacity, providing transparency into total shipping costs. *(WD-1094)*

---

## Carrier Hold Location Notifications

When a UPS or FedEx shipment is redirected to a retail Access Point or hold location, customers now receive a notification that includes the exact pickup address — removing the guesswork about where to retrieve their order.

- **Merge tag for hold location address** — Notification templates now support a dynamic tag that inserts the carrier hold location address into customer emails and SMS messages. *(WD-728)*
- **Hold location stored in Salesforce** — The pickup address is recorded on the Salesforce shipment record, giving customer service teams direct visibility. *(WD-1123)*
- **Notification system integration** — The email and SMS messaging system now correctly delivers pickup address data through its merge field pipeline. *(WD-1131)*

---

## Commerce7 Integration

Twelve improvements were delivered to the Commerce7 eCommerce integration, addressing reliability issues and adding new configuration options.

- **Bundle/Gift Set SKU Sync** — Bundle products now sync correctly between Commerce7 and the fulfillment portal; fulfillment errors on gift set orders have been resolved. *(WD-1115)*
- **POS Orders Filter** — A per-client toggle is now available to exclude in-store point-of-sale orders from being sent to the fulfillment warehouse. *(WD-1099)*
- **Duplicate Tracking Numbers** — A pre-check now prevents duplicate tracking numbers from being created on Commerce7 orders. *(WD-1073)*
- **Scheduled Inventory Sync Error** — An error occurring during scheduled inventory synchronization has been resolved. *(WD-1109)*
- **Product Sync Type Restriction** — Product updates from Commerce7 are now restricted to matching product types, preventing incorrect data from overwriting existing records. *(WD-697)*
- **Orders & Inventory Sync Setting** — A new setting gives clients control over how orders and inventory synchronize between Commerce7 and WineDirect Fulfillment. *(WD-1102)*
- **Transaction Confirmation Emails** — Commerce7 now sends transaction confirmation emails to customers when a shipping fulfillment record is created. *(WD-1077)*
- **Order Sales Tags Sync** — Custom sales attributes and tags applied to orders in Commerce7 now sync correctly, both at order creation and after approval. *(WD-688, WD-1107)*
- **Inventory Sync Error** — An intermittent error during inventory sync has been diagnosed and resolved. *(WD-1144)*
- **Non-Wine Items in Bundles** — Non-wine products included in Commerce7 bundles now sync correctly. *(WD-1143)*
- **Dependency Updates** — All third-party libraries used by the Commerce7 integration have been upgraded to current versions. *(WD-598)*

---

## Shipping & Carriers

**"Returning" Shipment Status** — A new **Returning** status is now available in the portal, applied when a shipment is on its way back to the warehouse. This gives operations and clients clearer visibility into the return lifecycle. *(WD-1133)*

**Estimated Ship Date to Arrive55** — The carrier upload for Arrive55 shipments now includes the estimated ship date, helping Arrive55 better plan pickup scheduling. *(WD-1088)*

**Temperature Control Orders Now Claimable** — A bug that prevented customer service from filing damage claims on UPS and FedEx temperature-controlled shipments has been fixed. CS teams can now submit claims for these orders, and claim portal error messaging has been improved for clarity. *(WD-1100)*

**Arrive55 Texas ZIP Code Expansion** — A hotfix added ZIP codes 75071 and 75072 (McKinney/Frisco area, DFW) to the Arrive55 delivery region, ensuring correct carrier routing for orders to these areas. *(WD-1127)*

**Accurate Carrier Code in Notifications** — The notification system now retrieves carrier codes directly from the WMS for each shipment, ensuring accurate carrier information in all customer-facing messages. *(WD-1085)*

---

## Products & Inventory

**Lot Control & Serialization Flags** — Product SKUs can now be flagged for lot control or serialization tracking. These flags are transmitted to the warehouse management system, forming the foundation for bottle-level traceability. *(WD-713, Epic WD-320)*

**WMS Description Field** — A new "WMS Description" field has been added to the product setup screen. This allows a separate warehouse-specific product description to be sent to the WMS for labeling and picking workflows. *(WD-1132, WD-1108)*

**Storage Subinventories in Inventory Transfers** — Bonded and long-term storage subinventory types are now fully supported in Inventory OUT requests and warehouse transfer workflows. *(WD-475)*

**Non-Wine Product WMS Transmission** — Non-wine SKUs no longer fail transmission to the WMS due to a missing bottle size field. *(WD-1095)*

**Bundle Product Lookup** — A bug causing product lookup failures for bundle items without an associated seller product has been resolved. *(WD-1135)*

---

## Order Management

**Order Export Item Detail** — The order export file from the View Orders screen now includes full line-item detail — SKU, quantity ordered/shipped, unit price, and status — with each line item as its own row. This significantly enriches the data available for auditing and reconciliation. *(WD-396)*

**Automated Retry for Compliance-Held Orders** — A nightly job now automatically retries orders that were previously blocked by quantity or volume compliance limits, reducing the manual effort needed to release these holds once limits reset. *(WD-703)*

---

## Notifications & Reporting

**Notification Usage Data Pipeline** — Daily automated syncs now feed email and SMS notification usage metrics into the data warehouse, enabling ongoing reporting on notification program utilization. *(WD-1165, Epic WD-1159)*

**Estimated Delivery Date Merge Tag** — Notification templates now support an **Estimated Delivery Date** merge tag that dynamically populates with the expected delivery date for each shipment, giving wine club members better delivery visibility. *(WD-704)*

**Notification Report Improvements** — The Shipment Notification Report now displays timezone information consistently as PST, with improved layout and data presentation. *(WD-1089)*

**Customer Order Number in Notifications** — The customer order reference number is now reliably included in all applicable outgoing notification emails. *(WD-1126)*

**Order Number Email Mapping Fix** — A gap in order number field mapping in email notifications has been closed. *(WD-1086)*

**Shipped Date Consistency** — The shipped date displayed in the Shipments Report now matches the date shown in Order Detail, resolving a one-day discrepancy. *(WD-1084)*

---

## Portal & System Reliability

**Live System Status on Login Page** — The portal login page now displays a live system status widget. Active incidents and scheduled maintenance windows are shown at login, keeping users informed without needing to visit a separate status page. *(WD-1130, Epic WD-1119)*

**Client Account Deactivation Fix** — An issue preventing client account deactivation in the Ops Portal (caused by inactive users still linked to the account) has been resolved. *(WD-1145)*

**High-Resolution Portal Logo** — The WineDirect Fulfillment logo in the portal has been updated to high-resolution for improved visual quality. *(WD-603)*

**Packing Station Migration** — The warehouse packing station interface has been migrated to updated infrastructure as part of ongoing platform modernization. *(WD-723)*

**Constellation Sub-Inventory Move Fix** — An error affecting sub-inventory move operations for Constellation accounts has been resolved. *(WD-1072)*

**IN-Request Retry Enhancement** — Automatic retry logic for inventory IN requests now also handles SKUs not yet registered in the WMS, reducing manual intervention. *(WD-1081)*

**Shipment Batch Processing Fix** — An issue where items arriving in different processing batches were not being handled correctly together has been resolved. *(WD-1097)*

**Inventory IN Auto-Close Logic** — The automatic close logic for IN requests has been refined to more accurately reflect completion state. *(WD-1098)*

**Carrier Validation Performance** — A threading issue in the carrier validation service has been resolved, preventing slowdowns during high-volume periods. *(WD-1116)*

**Carrier Validation Stability** — An intermittent crash in the carrier validation service related to application monitoring has been further stabilized. *(WD-1128)*

**Cancel-Out Query Fix** — The cancel-out matching query now accepts only the correct reference number format, preventing incorrect record matches. *(WD-1129)*

**Event Log Cleanup Job** — A scheduled job now automatically removes event log records for closed orders older than 60 days, improving database performance over time. *(WD-1134)*

**Qlik Analytics — Salesforce Production** — A Qlik analytics application has been connected to Salesforce production, enabling live reporting across the organization. *(WD-1142)*

**Build Infrastructure Update** — Internal .NET build tooling has been modernized (.slnx + Directory.Build.props), reducing engineering overhead. *(WD-692)*

</Update>
```
