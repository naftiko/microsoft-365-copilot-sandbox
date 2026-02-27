# Remove a Package

Remove an app or agent from your Microsoft 365 organization.

## API Details

- **API**: Microsoft 365 Copilot API
- **Method**: DELETE
- **Path**: `/copilot/packages/{packageId}`
- **Operation ID**: `deleteCopilotPackage`
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
| `packageId` | path | string | Yes | The unique identifier of the package to remove |

## Example Request

```bash
curl -X DELETE "http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/packages/pkg-001-abc" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

HTTP 204 No Content (empty response body on success).

## Instructions

When the user wants to remove or delete an app or agent from their Microsoft 365 organization, use this operation by making a DELETE request to `/copilot/packages/{packageId}`. Provide the package ID as a path parameter. A successful deletion returns a 204 status with no response body.
