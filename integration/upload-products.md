---
layout: default
title: My Page Title
---

## Upload Products

### Purpose
Accept a product data file (CSV or JSON) and uploads products to **SmartShelf** online application 

### Endpoint
- **POST** /api/external/uploadProducts  
- Content-Type: multipart/form-data

### Authentication & headers

| Header | Required | Description        |
|---|:---:|--------------------|
| Authorization | Yes | `Bearer <JWT>`     |
| key | Yes | API key            |
| Accept | Recommended | `application/json` |

### Form fields

| Field | Required | Type    | Description                 |
|---|:--------:|---------|-----------------------------|
| datafile |   Yes    | MultipartFile | Product data (CSV or JSON)  |
| deleteAll |   Yes    | boolean | true/false                  |

- Download template: [mst_product-template.csv](./mst_product-template.csv)


### Sample curl — CSV only
```bash
curl -v -X POST "https://api.example.com/api/external/uploadProducts" \
  -H "Authorization: Bearer YOUR_JWT_TOKEN" \
  -H "key: ENCRYPTED_COMPANY_KEY" \
  -F "datafile=@/path/to/products.csv;type=text/csv" \
  -F "deleteAll=true"
```

### Success response (200)
```json
{
  "status": 200,
  "data": [
    "Data uploaded successfully"
  ]
}
```

### Errors

| HTTP | Reason |
|---:|---|
| 400 | Missing file or invalid format |
| 401 | Unauthorized (invalid token) |
| 403 | Invalid/missing `key` |
| 500 | Processing/storage failure |

### Integration notes
- Use streaming for large files and set adequate timeouts.
- When images are submitted with the file, associate by exact filename.
- Processing may be asynchronous
