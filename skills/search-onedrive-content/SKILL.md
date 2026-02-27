# Search OneDrive Content Using Natural Language

Perform hybrid search (semantic and lexical) across OneDrive for work or school content using natural language queries. Results are returned with contextual understanding and intelligent ranking while maintaining security and compliance.

## API Details

- **API**: Microsoft 365 Copilot API
- **Method**: POST
- **Path**: `/copilot/search/query`
- **Operation ID**: `querySearchContent`
- **Tag**: Content Search
- **OpenAPI**: [microsoft-copilot-api.yaml](../../openapi/microsoft-copilot-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/search/query`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scope

- `Copilot.Search.Read`

## Request Body

```json
{
  "queryString": "budget presentation Q3",
  "from": 0,
  "size": 10
}
```

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `queryString` | string | Yes | Natural language search query |
| `from` | integer | No | Offset for pagination |
| `size` | integer | No | Number of results to return |

## Example Request

```bash
curl -X POST "http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/search/query" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{"queryString": "budget presentation Q3", "from": 0, "size": 10}'
```

## Example Response

```json
{
  "value": [
    {
      "hitId": "hit-001",
      "rank": 1,
      "summary": "Q3 2025 budget presentation covering departmental allocations and projected spending through year end.",
      "resource": {
        "@odata.type": "#microsoft.graph.driveItem",
        "id": "01XYZABC12345678",
        "name": "Q3-2025-Budget-Presentation.pptx",
        "webUrl": "https://contoso-my.sharepoint.com/personal/jdoe/Documents/Q3-2025-Budget-Presentation.pptx",
        "lastModifiedDateTime": "2025-08-15T14:30:00Z",
        "createdBy": {
          "user": {
            "displayName": "Jane Doe",
            "id": "user-abc-123"
          }
        }
      }
    },
    {
      "hitId": "hit-002",
      "rank": 2,
      "summary": "Annual budget planning template with quarterly breakdown and variance tracking worksheets.",
      "resource": {
        "@odata.type": "#microsoft.graph.driveItem",
        "id": "01XYZABC87654321",
        "name": "Annual-Budget-Template.xlsx",
        "webUrl": "https://contoso-my.sharepoint.com/personal/jsmith/Documents/Annual-Budget-Template.xlsx",
        "lastModifiedDateTime": "2025-07-01T09:00:00Z",
        "createdBy": {
          "user": {
            "displayName": "John Smith",
            "id": "user-def-456"
          }
        }
      }
    }
  ],
  "@odata.count": 2,
  "moreResultsAvailable": true
}
```

## Instructions

When the user wants to search for files in OneDrive using natural language, use this operation by making a POST request to `/copilot/search/query`. This performs hybrid semantic and lexical search with intelligent ranking. Results include file metadata, summaries, and links.
