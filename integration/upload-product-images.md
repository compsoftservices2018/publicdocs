---
layout: default
title: My Page Title
---

### Upload Product Images

### Purpose
Upload one or more product images when images are provided separately from the product file.

### Endpoint
- POST /api/external/uploadProductImages  
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
| images | Yes | file[] | Image files (JPEG/PNG) |

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
    "C:\\OnlineApp\\server\\html\\browser\\assets\\site-img\\10001\\banner-1.jpg",
    "C:\\OnlineApp\\server\\html\\browser\\assets\\site-img\\10001\\banner-2.jpg",
    "C:\\OnlineApp\\server\\html\\browser\\assets\\site-img\\10001\\banner-3.jpg",
    "C:\\OnlineApp\\server\\html\\browser\\assets\\site-img\\10001\\default.jpg",
    "C:\\OnlineApp\\server\\html\\browser\\assets\\site-img\\10001\\dummy.jpg",
    "C:\\OnlineApp\\server\\html\\browser\\assets\\site-img\\10001\\dummy2.jpg",
    "C:\\OnlineApp\\server\\html\\browser\\assets\\site-img\\10001\\dummy3.jpg",
    "C:\\OnlineApp\\server\\html\\browser\\assets\\site-img\\10001\\home-page.jpg",
    "C:\\OnlineApp\\server\\html\\browser\\assets\\site-img\\10001\\site-logo.jpg",
    "C:\\OnlineApp\\server\\html\\browser\\assets\\site-img\\10001\\wall.jpg"
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
- Prefer unique filenames (SKU prefix or UUID) to prevent collisions.
- Always verify server filename normalization before relying on exact names.
