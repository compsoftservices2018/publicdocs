---
layout: default
title: My Page Title
---

### Send Orders

### Purpose
Push new orders into RetailProcessor for processing and fulfillment.

### Endpoint
- POST /api/external/sendOrders  
- Content-Type: application/json  
- Accept: application/json

### Authentication & headers

| Header | Required | Description |
|---|:---:|---|
| Authorization | Yes | `Bearer <JWT>` |
| key | Yes | API key |
| Accept | Recommended | `application/json` |


### Request body (example)
```json
[
  {
    "updUser": "admin",
    "updDate": "2025-12-26",
    "companyCode": "10001",
    "orderNo": "0000000000",
    "version": 1,
    "refOrderNo": null,
    "orderDate": "2025-12-26",
    "customerCode": "00000",
    "customerName": "Pradeep Chawadkar",
    "altCustomerCode": null,
    "altCustomerName": null,
    "mobile": "1234567890",
    "email": "",
    "gstinNo": "12ABCDE1234F1Z5",
    "pin": "400101",
    "remark": "",
    "status": "Submitted",
    "cancellationDate": null,
    "scheduleDeliveryDate": null,
    "deliveryDate": null,
    "deliveredBy": null,
    "deliveryAddress": "B-1-302, Mokareshwar CHS Ltd\nMalad, Mumbai 400097, Pin: 400101, State: null, Country: null",
    "deliveredTo": null,
    "altMobile": null,
    "billNo": null,
    "orderDetails": [
      {
        "updUser": "admin",
        "updDate": "2025-12-26",
        "id": "3f4ae616-444d-443e-a6f5-ab7d8ff049ca",
        "productCode": "10059",
        "productName": "SHREOS RAJGEERA FLAKES PACK 200 GM",
        "altProductCode": null,
        "altProductName": null,
        "orderQty": 1,
        "fixedSellingPrice": 44.00,
        "perOff": null,
        "priceOff": null,
        "mrp": 80.00,
        "netSellingPrice": 44.00,
        "billedQty": 1,
        "billMrp": 80,
        "billSellingPrice": 44,
        "hsnCode": "0",
        "gstPercentage": 5.00,
        "cessPercentage": 0.00,
        "imageName": "default"
      },
      {
        "updUser": "admin",
        "updDate": "2025-12-26",
        "id": "091dffd6-a03f-4232-9043-c4336020965c",
        "productCode": "10001",
        "productName": "AIR FRESHENER (COMBI PACK) 20+20 GM",
        "altProductCode": null,
        "altProductName": null,
        "orderQty": 1,
        "fixedSellingPrice": 73.00,
        "perOff": null,
        "priceOff": null,
        "mrp": 130.00,
        "netSellingPrice": 73.00,
        "billedQty": 1,
        "billMrp": 130,
        "billSellingPrice": 73,
        "hsnCode": "33074900",
        "gstPercentage": 18.00,
        "cessPercentage": 0.00,
        "imageName": "default"
      }
    ],
    "orderPayments": [
      {
        "updUser": "admin",
        "updDate": "2025-12-26",
        "id": "c9724361-a59e-4184-b56f-3a103efb931d",
        "status": "Pending",
        "remark": "0000000000",
        "paymentMode": "Cash",
        "rzrOrderId": "order_RwBBRGElb1jGnZ",
        "rzrOrderStatus": "created",
        "rzrPaymentId": null,
        "rzrSign": null,
        "paymentDate": null,
        "paymentAmt": 11700,
        "paymentId": "1"
      }
    ],
    "totalMrp": 210.00,
    "totalNetSellingPrice": 117.00,
    "totalOrderQty": 2
  },
  {
    "updUser": "admin",
    "updDate": "2025-12-26",
    "companyCode": "10001",
    "orderNo": "0000000001",
    "version": 1,
    "refOrderNo": null,
    "orderDate": "2025-12-26",
    "customerCode": "00000",
    "customerName": "Pradeep Chawadkar",
    "altCustomerCode": null,
    "altCustomerName": null,
    "mobile": "1234567890",
    "email": "",
    "gstinNo": "12ABCDE1234F1Z5",
    "pin": "400101",
    "remark": "",
    "status": "Submitted",
    "cancellationDate": null,
    "scheduleDeliveryDate": null,
    "deliveryDate": null,
    "deliveredBy": null,
    "deliveryAddress": "B-1-302, Mokareshwar CHS Ltd\nMalad, Mumbai 400097, Pin: 400101, State: null, Country: null",
    "deliveredTo": null,
    "altMobile": null,
    "billNo": null,
    "orderDetails": [
      {
        "updUser": "admin",
        "updDate": "2025-12-26",
        "id": "0b5b3fe7-13ee-48f4-ac12-225a1a709144",
        "productCode": "10059",
        "productName": "SHREOS RAJGEERA FLAKES PACK 200 GM",
        "altProductCode": null,
        "altProductName": null,
        "orderQty": 2,
        "fixedSellingPrice": 44.00,
        "perOff": null,
        "priceOff": null,
        "mrp": 80.00,
        "netSellingPrice": 44.00,
        "billedQty": 2,
        "billMrp": 80,
        "billSellingPrice": 44,
        "hsnCode": "0",
        "gstPercentage": 5.00,
        "cessPercentage": 0.00,
        "imageName": "default"
      },
      {
        "updUser": "admin",
        "updDate": "2025-12-26",
        "id": "cf43548d-b7a4-4763-8d5a-38856854e3f3",
        "productCode": "10002",
        "productName": "ANUVED SHAHI KHAS BATH SOAP 112.5 GM",
        "altProductCode": null,
        "altProductName": null,
        "orderQty": 2,
        "fixedSellingPrice": 44.00,
        "perOff": null,
        "priceOff": null,
        "mrp": 80.00,
        "netSellingPrice": 44.00,
        "billedQty": 2,
        "billMrp": 80,
        "billSellingPrice": 44,
        "hsnCode": "34011190",
        "gstPercentage": 18.00,
        "cessPercentage": 0.00,
        "imageName": "default"
      }
    ],
    "orderPayments": [
      {
        "updUser": "admin",
        "updDate": "2025-12-26",
        "id": "fa954fd6-4277-4610-a6ea-fd56ac033dc2",
        "status": "Paid",
        "remark": "0000000001",
        "paymentMode": "Online",
        "rzrOrderId": "order_RwBBnU0OwsqyVi",
        "rzrOrderStatus": "created",
        "rzrPaymentId": "pay_RwBCLVJHWaFsTV",
        "rzrSign": "20c7cfe0682b39916db113206ff51bdf6a11d7e9a71e05d286f197cdd963d23f",
        "paymentDate": null,
        "paymentAmt": 17600,
        "paymentId": "1"
      }
    ],
    "totalMrp": 320.00,
    "totalNetSellingPrice": 176.00,
    "totalOrderQty": 4
  }
]
```

### Sample curl
```bash
curl -v -X POST "https://api.example.com/api/external/sendOrders" \
  -H "Authorization: Bearer YOUR_JWT_TOKEN" \
  -H "key: ENCRYPTED_COMPANY_KEY" \
  -H "Content-Type: application/json" \
  -d @order.json
```

### Success response (200)
```json
{
  "status": 200,
  "data": true
}
```

### Errors

<!-- blank line ensured before table -->
| HTTP | Reason |
|---:|---|
| 400 | Validation errors — missing required fields |
| 401 | Unauthorized |
| 409 | Conflict — duplicate order/version mismatch |
| 500 | Persistence error |
<!-- blank line ensured after table -->

### Integration notes
- Server may derive `companyCode` from `key` when omitted.
- Server ensures orderDetails receive `companyCode`, `orderNo` and `version` before persisting.
- On validation failure, inspect returned error details and resubmit corrected payload.
