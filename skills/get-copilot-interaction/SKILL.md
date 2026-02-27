# Get a Specific Copilot Interaction

Retrieve details of a specific Copilot interaction by its ID.

## API Details

- **API**: Microsoft 365 Copilot API
- **Method**: GET
- **Path**: `/copilot/interactions/{interactionId}`
- **Operation ID**: `getCopilotInteraction`
- **Tag**: Interaction Exports
- **OpenAPI**: [microsoft-copilot-api.yaml](../../openapi/microsoft-copilot-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/interactions/{interactionId}`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scope

- `Copilot.Interaction.Read`

## Parameters

| Parameter | In | Type | Required | Description |
|-----------|-----|------|----------|-------------|
| `interactionId` | path | string | Yes | Unique identifier for the interaction |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/interactions/interaction-001" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
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
}
```

## Instructions

When the user wants to retrieve details about a specific Copilot interaction, use this operation by making a GET request to `/copilot/interactions/{interactionId}`. Provide the interaction ID as a path parameter. This returns the full interaction record including user, application, content, and context references.
