# List Meetings with Available Insights

List Teams meetings for which AI-generated insights are available. Supports filtering by date range and participants.

## API Details

- **API**: Microsoft 365 Copilot API
- **Method**: GET
- **Path**: `/copilot/meetings`
- **Operation ID**: `listMeetingsWithInsights`
- **Tag**: Meeting Insights
- **OpenAPI**: [microsoft-copilot-api.yaml](../../openapi/microsoft-copilot-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/meetings`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scope

- `Copilot.MeetingInsights.Read`

## Parameters

| Parameter | In | Type | Required | Description |
|-----------|-----|------|----------|-------------|
| `$top` | query | integer | No | Maximum number of results (1-999, default 25) |
| `$skip` | query | integer | No | Number of results to skip for pagination |
| `$filter` | query | string | No | OData filter expression |
| `startDateTime` | query | string (date-time) | No | Start of the date/time range (ISO 8601) |
| `endDateTime` | query | string (date-time) | No | End of the date/time range (ISO 8601) |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/meetings?$top=25&startDateTime=2025-09-01T00:00:00Z" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "value": [
    {
      "meetingId": "meeting-xyz-789",
      "subject": "Q3 Product Roadmap Review",
      "startDateTime": "2025-09-10T14:00:00Z",
      "endDateTime": "2025-09-10T15:00:00Z",
      "insightsAvailable": true
    },
    {
      "meetingId": "meeting-uvw-456",
      "subject": "Weekly Engineering Standup",
      "startDateTime": "2025-09-09T09:00:00Z",
      "endDateTime": "2025-09-09T09:30:00Z",
      "insightsAvailable": true
    }
  ],
  "@odata.count": 2,
  "@odata.nextLink": "https://graph.microsoft.com/v1.0/copilot/meetings?$skip=2&$top=25"
}
```

## Instructions

When the user wants to browse or list meetings that have AI-generated insights available, use this operation by making a GET request to `/copilot/meetings`. Filter by date range to narrow results. Use the returned meeting IDs to then fetch detailed insights for specific meetings.
