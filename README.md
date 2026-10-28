# Topic 7: API Integration Patterns & Pagination
## API Authentication Methods

**Course:** n8n Hands-On Level 2 Automation Course  
**Topic:** Topic 7 - API Integration Patterns & Pagination (API Authentication Methods)  
**Author:** Rushikesh Karche  
**Status:** Approved  

---

## 📁 Repository Contents

| File | Description |
| :--- | :--- |
| **Topic 7 - API Integration Patterns & Authentication Methods.json** | Complete n8n production workflow demonstrating API Key, Bearer Token, and OAuth2 token refresh integration patterns. |
| **
8n_topic_7_requirement_document.md** | Official requirement document containing Learning Concepts, BRD, PRD, SRS, Test Cases, and Traceability Matrix. |
| **
8n_topic_7_requirement_document.pdf** | Official styled PDF export of the Topic 7 requirement document. |

---

## 🚀 Workflow Overview

This workflow demonstrates secure API authentication patterns and automatic token refresh handling in n8n without hardcoding secrets:

1. **Manual_Trigger:** Starts the workflow on demand for testing.
2. **Code_SetAuthMode:** Sets dynamic authentication mode and test payloads.
3. **Switch_AuthPattern:** Routes traffic through different auth patterns:
   * **API Key:** Demonstrates custom header authentication (\X-API-Key\).
   * **Bearer Token:** Injects JWT Bearer token into HTTP headers.
   * **OAuth2 with Token Refresh:** Checks token expiry, refreshes expired tokens via automated background POST, saves fresh tokens, and executes protected requests.
4. **HTTP_CallWithApiKey:** Makes authenticated API call using API Key header.
5. **Code_CheckTokenExpiry & IF_TokenIsExpired:** Evaluates token lifecycle.
6. **HTTP_RefreshAuthToken & Code_SaveFreshToken:** Transparently handles OAuth2 token refresh cycle.
7. **HTTP_CallWithBearerToken:** Dispatches authenticated request using Bearer JWT.
8. **Code_AuditAuthSuccess:** Audits execution details and verifies that no raw secrets are leaked in execution payloads.

---

## 🧪 Test Verification
* **TC-001 (API Key Header):** Verified \X-API-Key\ header injection.
* **TC-002 (Bearer Token Auth):** Verified \Authorization: Bearer <token>\ header injection.
* **TC-003 (OAuth2 Token Refresh):** Verified automated token exchange and transparent request retry.
* **TC-004 (Auth Failure Alert):** Verified 401 handling and error alerting.
* **TC-005 (Security Export Validation):** Verified that exported workflow JSON contains no plaintext secrets.
