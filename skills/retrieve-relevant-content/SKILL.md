# Retrieve Relevant Content from Microsoft 365

Retrieve contextually relevant information from Microsoft 365 content (documents, policies, knowledge bases) while respecting document access controls and sensitivity labels. Useful for building specialized assistants grounded in organizational data.

## API Details

- **API**: Microsoft 365 Copilot API
- **Method**: POST
- **Path**: `/copilot/retrieval/query`
- **Operation ID**: `queryRetrievalContent`
- **Tag**: Content Retrieval
- **OpenAPI**: [microsoft-copilot-api.yaml](../../openapi/microsoft-copilot-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/retrieval/query`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scope

- `Copilot.Retrieval.Read`

## Request Body

```json
{
  "queryString": "remote work policy",
  "from": 0,
  "size": 10,
  "queryType": "natural_language"
}
```

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `queryString` | string | Yes | The natural language query to retrieve relevant content |
| `from` | integer | No | Offset for pagination |
| `size` | integer | No | Number of results to return |
| `queryType` | string | No | Type of query (e.g., natural_language) |

## Example Request

```bash
curl -X POST "http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/retrieval/query" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{"queryString": "remote work policy", "from": 0, "size": 10}'
```

## Example Response

```json
{
  "value": [
    {
      "id": "ret-result-001",
      "relevanceScore": 0.94,
      "content": {
        "snippet": "The company remote work policy allows employees to work from home up to three days per week with manager approval.",
        "sensitivityLabel": "Internal"
      },
      "resource": {
        "type": "driveItem",
        "id": "01ABCDEF23456789",
        "name": "Remote-Work-Policy-2025.docx",
        "webUrl": "https://contoso.sharepoint.com/sites/hr/Shared%20Documents/Remote-Work-Policy-2025.docx"
      }
    },
    {
      "id": "ret-result-002",
      "relevanceScore": 0.87,
      "content": {
        "snippet": "Eligible employees must complete the remote work agreement form and submit it to HR before beginning any remote arrangement.",
        "sensitivityLabel": "Internal"
      },
      "resource": {
        "type": "driveItem",
        "id": "01ABCDEF98765432",
        "name": "HR-Onboarding-Guide.docx",
        "webUrl": "https://contoso.sharepoint.com/sites/hr/Shared%20Documents/HR-Onboarding-Guide.docx"
      }
    }
  ],
  "@odata.count": 2
}
```

## Instructions

When the user wants to retrieve or search for relevant organizational content, documents, policies, or knowledge base articles from Microsoft 365, use this operation by making a POST request to `/copilot/retrieval/query`. Provide a natural language query describing what content to find. Results respect document access controls and sensitivity labels.
