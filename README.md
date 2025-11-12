````markdown
# DataStreams Email Verification API

Comprehensive REST API for real-time, batch, and bulk email verification.

![DataStreams Logo](https://YOUR_STATIC_PATH/ds-logo-new.svg)

---

## Overview

The **DataStreams Email Verification API** offers a reliable and scalable solution to verify email addresses through DNS, MX, and SMTP checks. You can validate single or multiple emails, or upload large files for bulk verification.

- **Base URL:** `https://api.datastreams.com/api/v1/`
- **Authentication:** Use the `x-api-key` header for all requests.

---

## Authentication & API Keys

Users can create up to **five custom API keys** for project-level access control.

| Feature         | Description                               |
|-----------------|-------------------------------------------|
| API Key         | Create, edit or delete existing keys      |
| Whitelisted IPs | Add or remove allowed IP addresses        |
| Status          | Active / Inactive                         |

---

## Verification Types

| Type       | Description                                |
|------------|--------------------------------------------|
| Real-Time  | Verify a single email instantly            |
| Batch      | Verify up to 100 emails in a single call   |
| Bulk       | Upload files for large-scale verification  |

---

## 1. Real-Time Single Email Verification

**Endpoint:**  
`GET /email_verify?email=EMAIL_ADDRESS`

**Example cURL Request:**
```bash
curl -X GET "https://api.datastreams.com/api/v1/email_verify?email=john@datastreams.com" \
  -H "x-api-key: YOUR_API_KEY"
````

**Success Response:**

```json
{
  "email": "example@datastreams.com",
  "email_status": "valid",
  "advance_status": "Deliverable",
  "domain": "datastreams.com",
  "ai_rationale": "This email address has been confirmed as valid, so you're good to send messages there",
  "smtp_provider": "aspmx.l.google.com",
  "all_mx_records": ["aspmx.l.google.com","alt2.aspmx.l.google.com"]
}
```

**Error Response:**

```json
{"error": "Invalid or missing API credentials","status":"401"}
```

---

## Error Codes

| Code | Description                                        |
| ---- | -------------------------------------------------- |
| 200  | ✅ Success/OK                                       |
| 400  | Invalid request format                             |
| 401  | Invalid or missing API credentials                 |
| 402  | Insufficient credits. Please recharge your account |
| 403  | Invalid or Inactive API key                        |
| 451  | Access restricted                                  |
| 502  | Email verification unavailable                     |
| 429  | Rate limit exceeded                                |
| 500  | Internal server error                              |

---

> **Note:**
> Ensure your account has enough verification credits. Bulk uploads support CSV/Excel files up to 50 MB. IP whitelisting is strongly recommended for production environments.

---

**Support:**
For assistance, contact: [support@datastreams.ai](mailto:support@datastreams.ai)

```
If you want, I can also **add sections for Batch and Bulk email verification** with example requests and responses so the README becomes **complete API documentation**.  

Do you want me to do that?
```
