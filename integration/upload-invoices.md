---
layout: default
title: My Page Title
---

### Upload Invoice PDFs

### Purpose
Upload invoice PDF files to be stored under the configured invoice storage folder for a company.

### Endpoint
- POST /api/orders/invoices  
- Content-Type: multipart/form-data

### Authentication & headers

| Header | Required | Description       |
|---|:---:|-------------------|
| Authorization | Yes | `Bearer <JWT>`    |
| key | Yes | API key           |
| Accept | Recommended | `application/pdf` |

### Form fields

| Field | Required | Type | Description |
|---|:---:|---|---|
| invoices | Yes | file[] | One or more PDF files |

### Storage behavior
- Base folder: `{app.storage.invoice}` (server configuration)  
- Company folder: `{app.storage.invoice}/{companyCode}/`  
- Filenames: server may prefix with UUID to avoid collisions. Response contains `originalName`, `storedName`, and `path`.

### Sample curl
```bash
curl -v -X POST "https://api.example.com/api/orders/invoices" \
  -H "Authorization: Bearer YOUR_JWT_TOKEN" \
  -H "key: ENCRYPTED_COMPANY_KEY" \
  -F "invoices=@/path/to/invoice1.pdf;type=application/pdf" \
  -F "invoices=@/path/to/invoice2.pdf" \
```

### Success response (200)
```json
{
  "status": 200,
  "data": true
}
```

### Errors

| HTTP | Reason |
|---:|---|
| 400 | No files or non-PDF content |
| 401 | Unauthorized |
| 500 | Storage write failure |

### Integration notes
- Validate PDFs on client-side before upload.
- Use the returned `path`/`storedName` to reference files for later download.
- Consider including `orderNo` in metadata to simplify reconciliation.
