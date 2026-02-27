# Get Copilot Usage Report

Query aggregated user counts and usage data for Microsoft 365 Copilot across your organization. Use for tracking adoption and building internal reports.

## API Details

- **API**: Microsoft 365 Copilot API
- **Method**: GET
- **Path**: `/reports/copilot/usage`
- **Operation ID**: `getCopilotUsageReport`
- **Tag**: Usage Reports
- **OpenAPI**: [microsoft-copilot-api.yaml](../../openapi/microsoft-copilot-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/reports/copilot/usage`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scope

- `Reports.Read.All`

## Parameters

| Parameter | In | Type | Required | Description |
|-----------|-----|------|----------|-------------|
| `period` | query | string | Yes | Reporting period: D7, D30, D90, or D180 |
| `date` | query | string (date) | No | Specific date (ISO 8601). Omit for latest data |
| `$top` | query | integer | No | Maximum number of results (1-999, default 25) |
| `$skip` | query | integer | No | Number of results to skip for pagination |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/reports/copilot/usage?period=D30" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "value": [
    {
      "reportDate": "2025-09-10",
      "totalEnabledUsers": 5000,
      "totalActiveUsers": 3250,
      "wordActiveUsers": 2100,
      "excelActiveUsers": 1800,
      "powerPointActiveUsers": 1200,
      "outlookActiveUsers": 2800,
      "teamsActiveUsers": 2500,
      "oneNoteActiveUsers": 600,
      "loopActiveUsers": 350,
      "copilotChatActiveUsers": 1900
    }
  ],
  "@odata.count": 1
}
```

## Instructions

When the user wants to view aggregated Copilot usage statistics for their organization, use this operation by making a GET request to `/reports/copilot/usage`. The `period` parameter is required and accepts D7, D30, D90, or D180. Results include user counts broken down by Microsoft 365 application.
