# Update a Package

Update configuration or status of an app or agent deployed in Microsoft 365.

## API Details

- **API**: Microsoft 365 Copilot API
- **Method**: PATCH
- **Path**: `/copilot/packages/{packageId}`
- **Operation ID**: `updateCopilotPackage`
- **Tag**: Packages
- **OpenAPI**: [microsoft-copilot-api.yaml](../../openapi/microsoft-copilot-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/packages/{packageId}`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scope

- `Copilot.Package.ReadWrite.All`

## Parameters

| Parameter | In | Type | Required | Description |
|-----------|-----|------|----------|-------------|
| `packageId` | path | string | Yes | The unique identifier of the package |

## Request Body

```json
{
  "description": "AI agent that helps sales teams draft proposals and analyze pipeline data. Updated with Q4 product catalog.",
  "status": "active"
}
```

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `displayName` | string | No | Updated display name |
| `description` | string | No | Updated description |
| `status` | string | No | Updated status (active, disabled) |

## Example Request

```bash
curl -X PATCH "http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/packages/pkg-001-abc" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{"description": "AI agent that helps sales teams draft proposals and analyze pipeline data. Updated with Q4 product catalog."}'
```

## Example Response

```json
{
  "id": "pkg-001-abc",
  "displayName": "Contoso Sales Assistant",
  "description": "AI agent that helps sales teams draft proposals and analyze pipeline data. Updated with Q4 product catalog.",
  "type": "agent",
  "publisher": "Contoso IT",
  "version": "2.1.0",
  "status": "active",
  "createdDateTime": "2025-06-01T09:00:00Z",
  "lastModifiedDateTime": "2025-09-11T08:00:00Z",
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

When the user wants to update the configuration or status of an existing app or agent, use this operation by making a PATCH request to `/copilot/packages/{packageId}`. Provide the package ID and the fields to update (description, status, display name).
