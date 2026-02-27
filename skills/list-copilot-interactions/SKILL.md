# List Copilot Interactions

Retrieve a list of user interactions with Copilot across Microsoft 365 applications. Supports filtering by date range, user, and application. Enables compliance solutions to capture and archive AI interactions.

## API Details

- **API**: Microsoft 365 Copilot API
- **Method**: GET
- **Path**: `/copilot/interactions`
- **Operation ID**: `listCopilotInteractions`
- **Tag**: Interaction Exports
- **OpenAPI**: [microsoft-copilot-api.yaml](../../openapi/microsoft-copilot-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/interactions`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scope

- `Copilot.Interaction.Read`

## Parameters

| Parameter | In | Type | Required | Description |
|-----------|-----|------|----------|-------------|
| `$top` | query | integer | No | Maximum number of results (1-999, default 25) |
| `$skip` | query | integer | No | Number of results to skip for pagination |
| `$filter` | query | string | No | OData filter expression |
| `$orderby` | query | string | No | OData order-by expression |
| `startDateTime` | query | string (date-time) | No | Start of the date/time range (ISO 8601) |
| `endDateTime` | query | string (date-time) | No | End of the date/time range (ISO 8601) |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/interactions?$top=25&startDateTime=2025-09-01T00:00:00Z" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "value": [
    {
      "id": "interaction-001",
      "createdDateTime": "2025-09-10T10:15:00Z",
      "userId": "user-abc-123",
      "userDisplayName": "Jane Doe",
      "appId": "Word",
      "interactionType": "prompt",
      "content": "Summarize the key points from the Q3 sales report.",
      "contextReferences": [
        {
          "type": "driveItem",
          "id": "01ABCDEF11111111",
          "name": "Q3-Sales-Report.docx",
          "webUrl": "https://contoso.sharepoint.com/sites/sales/Q3-Sales-Report.docx"
        }
      ]
    },
    {
      "id": "interaction-002",
      "createdDateTime": "2025-09-10T10:15:05Z",
      "userId": "user-abc-123",
      "userDisplayName": "Jane Doe",
      "appId": "Word",
      "interactionType": "response",
      "content": "The Q3 sales report highlights a 12% increase in revenue year-over-year driven by strong performance in the enterprise segment.",
      "contextReferences": []
    }
  ],
  "@odata.count": 2,
  "@odata.nextLink": "https://graph.microsoft.com/v1.0/copilot/interactions?$skip=2&$top=25"
}
```

## Instructions

When the user wants to list, browse, or audit Copilot interactions across Microsoft 365, use this operation by making a GET request to `/copilot/interactions`. Use query parameters to filter by date range, user, or application. This is useful for compliance monitoring and audit trails.
