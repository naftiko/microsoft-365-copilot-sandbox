# Get Per-User Copilot Usage Details

Retrieve detailed per-user usage data for Microsoft 365 Copilot, including feature-level breakdowns.

## API Details

- **API**: Microsoft 365 Copilot API
- **Method**: GET
- **Path**: `/reports/copilot/usage/userDetail`
- **Operation ID**: `getCopilotUsageUserDetail`
- **Tag**: Usage Reports
- **OpenAPI**: [microsoft-copilot-api.yaml](../../openapi/microsoft-copilot-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/reports/copilot/usage/userDetail`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scope

- `Reports.Read.All`

## Parameters

| Parameter | In | Type | Required | Description |
|-----------|-----|------|----------|-------------|
| `period` | query | string | Yes | Reporting period: D7, D30, D90, or D180 |
| `$top` | query | integer | No | Maximum number of results (1-999, default 25) |
| `$skip` | query | integer | No | Number of results to skip for pagination |
| `$filter` | query | string | No | OData filter expression |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/reports/copilot/usage/userDetail?period=D30&$top=25" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "value": [
    {
      "userId": "user-abc-123",
      "userPrincipalName": "jdoe@contoso.com",
      "displayName": "Jane Doe",
      "lastActivityDate": "2025-09-10",
      "wordUsed": true,
      "excelUsed": true,
      "powerPointUsed": false,
      "outlookUsed": true,
      "teamsUsed": true,
      "oneNoteUsed": false,
      "loopUsed": false,
      "copilotChatUsed": true
    },
    {
      "userId": "user-def-456",
      "userPrincipalName": "jsmith@contoso.com",
      "displayName": "John Smith",
      "lastActivityDate": "2025-09-09",
      "wordUsed": false,
      "excelUsed": true,
      "powerPointUsed": true,
      "outlookUsed": true,
      "teamsUsed": true,
      "oneNoteUsed": true,
      "loopUsed": false,
      "copilotChatUsed": false
    }
  ],
  "@odata.count": 2,
  "@odata.nextLink": "https://graph.microsoft.com/v1.0/reports/copilot/usage/userDetail?$skip=2&$top=25"
}
```

## Instructions

When the user wants to see per-user Copilot usage details including which applications each user has used, use this operation by making a GET request to `/reports/copilot/usage/userDetail`. The `period` parameter is required. Results show per-user feature-level usage breakdowns across all Microsoft 365 applications.
