# Get a Specific Package

Retrieve details about a specific app or agent deployed in Microsoft 365.

## API Details

- **API**: Microsoft 365 Copilot API
- **Method**: GET
- **Path**: `/copilot/packages/{packageId}`
- **Operation ID**: `getCopilotPackageById`
- **Tag**: Packages
- **OpenAPI**: [microsoft-copilot-api.yaml](../../openapi/microsoft-copilot-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/packages/{packageId}`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scope

- `Copilot.Package.ReadWrite.All`

## Parameters

| Parameter | In | Type | Required | Description |
|-----------|-----|------|----------|-------------|
| `packageId` | path | string | Yes | The unique identifier of the package |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/packages/pkg-001-abc" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "id": "pkg-001-abc",
  "displayName": "Contoso Sales Assistant",
  "description": "AI agent that helps sales teams draft proposals and analyze pipeline data.",
  "type": "agent",
  "publisher": "Contoso IT",
  "version": "2.1.0",
  "status": "active",
  "createdDateTime": "2025-06-01T09:00:00Z",
  "lastModifiedDateTime": "2025-09-01T14:30:00Z",
  "permissions": [
    { "name": "Sites.Read.All", "type": "delegated" },
    { "name": "Mail.Read", "type": "delegated" }
  ],
  "deployedTo": [
    { "id": "group-sales-team", "displayName": "Sales Team", "type": "group" }
  ]
}
```

## Instructions

When the user wants to get details about a specific app or agent package, use this operation by making a GET request to `/copilot/packages/{packageId}`. Provide the package ID as a path parameter. This returns full package details including permissions and deployment targets.
