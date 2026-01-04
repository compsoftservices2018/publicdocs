---
layout: default
title: My Page Title
---

## Upload Product Images

### Purpose
Upload one or more product images when images are provided separately to **SmartShelf** online application.

### Endpoint
- **POST** /api/external/uploadImages
- Content-Type: multipart/form-data

### Authentication & headers

| Header | Required | Description        |
|---|:---:|--------------------|
| Authorization | Yes | `Bearer <JWT>`     |
| key | Yes | API key            |
| Accept | Recommended | `application/jpeg` |

### Form fields

| Field | Required | Type | Description |
|---|:---:|---|---|
| images | Yes | MultipartFile[] | Image files (JPEG) |

### Sample curl
```bash
curl -v -X POST "https://api.example.com/api/external/uploadProductImages" \
  -H "Authorization: Bearer YOUR_JWT_TOKEN" \
  -H "key: ENCRYPTED_COMPANY_KEY" \
  -F "images=@/path/to/image1.jpg" \
  -F "images=@/path/to/image2.png" \
```

### Success response (200)
```json
{
  "status": 200,
  "data": [
    "Images uploaded successfully"
  ]
}
```

### Errors & tips

| HTTP | Reason / Recommendation |
|---:|---|
| 400 | No images or invalid mapping — ensure JSON mapping matches filenames |
| 413 | Payload too large — split or chunk uploads |
| 500 | Storage error — retry with backoff |

### Integration tips
- Use unique product name as filenames to prevent collisions.
- Always verify server filename normalization before relying on exact names.
