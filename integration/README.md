# SmartShelf API Documentation (Third‑Party Integration)

This document contains integration guides for the public APIs exposed by **SmartShelf**  online application. Each document includes endpoint details, required headers, sample requests (curl), example responses, and integration notes.

## Integration flow

Below is a high-level sequence diagram that shows authentication and how a third‑party system interacts with Smartshelf online application endpoints.

```mermaid
sequenceDiagram
    participant OnlineAppDB as SmartShelf Database
    participant OnlineAppStorage as SmartShelf Storage
    participant OnlineApp as SmartShelf App
    participant Billing as Billing
    participant BillingDB as Billing Database


    Billing->>OnlineApp: Call /uploadProducts
    OnlineApp->>OnlineAppDB: Updates products to online app
    Billing->>OnlineApp: Call /uploadProductImages
    OnlineApp->>OnlineAppDB: Updates products images to online app
    Billing->>OnlineApp: Call /receiveOrders
    Billing->>Billing: Update order process
    Billing->>BillingDB: Updates submitted orders to billing
    Billing->>OnlineApp: Call /sendOrders with status "Processing"
    OnlineApp->>OnlineAppDB: Updates order status to "Processing"
    Billing->>Billing: Process order routine & create invoices
    Billing->>BillingDB: Updates order status to "Processed"
    Billing->>OnlineApp: Call /sendOrders with status "Processed"
    OnlineApp->>OnlineAppDB: Updates order status to "Processed"
    Billing->>OnlineApp: Call /sendInvoices
    OnlineApp->>OnlineAppStorage: Uploads invoices to Smartsheld app
    Billing->>BillingDB: Updates order status to any subsequent statuses
    Billing->>OnlineApp: Call /sendOrders with any subsequent statuses
    OnlineApp->>OnlineAppDB: Updates order status marked status



```


## APIs

- [Upload Products](./upload-products.md) — Instructions and sample payloads for uploading product data (CSV or JSON), field mappings, validation rules, and common errors.
- [Upload Product Images](./upload-product-images.md) — Guide for uploading product images using multipart/form-data, naming conventions, and size/format requirements.
- [Receive Orders](./receive-orders.md) — Details on pulling orders from RetailProcessor (GET endpoints), pagination, filters, and sample responses.
- [Send Orders](./send-orders.md) — Steps and examples for pushing orders into RetailProcessor (POST), required headers, idempotency notes, and error handling.
- [Send Invoices](./upload-invoices.md) — How to upload invoice PDF files (multipart), expected metadata, and downstream processing behavior.



Integration notes
- Request application administrator for endpoint url, API keys and token details.
- All requests require authentication. Include an Authorization header with a bearer token (or as specified by your agreement).
- Many endpoints expect an encrypted key header (named `key`) — see each doc for details.
- For file uploads, use multipart/form-data with proper Content-Type boundaries.
- For downloads, the API returns Content-Type: application/pdf and Content-Disposition: attachment.

If you need a machine-readable OpenAPI (Swagger) file, request it from the API owner.
