# List Apps and Agents

View all apps and agents deployed across Microsoft 365 in your organization. Useful for inventory management and governance.

## API Details

- **API**: Microsoft 365 Copilot API
- **Method**: GET
- **Path**: `/copilot/packages`
- **Operation ID**: `listCopilotPackages`
- **Tag**: Packages
- **OpenAPI**: [microsoft-copilot-api.yaml](../../openapi/microsoft-copilot-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/packages`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scope

- `Copilot.Package.ReadWrite.All`

## Parameters

| Parameter | In | Type | Required | Description |
|-----------|-----|------|----------|-------------|
| `$top` | query | integer | No | Maximum number of results (1-999, default 25) |
| `$skip` | query | integer | No | Number of results to skip for pagination |
| `$filter` | query | string | No | OData filter expression |
| `$orderby` | query | string | No | OData order-by expression |
| `type` | query | string | No | Filter by package type: app, agent, or all (default: all) |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-365-copilot-apis/1.0.0/copilot/packages?type=all&$top=25" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "value": [
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
    },
    {
      "id": "pkg-002-def",
      "displayName": "IT Helpdesk Bot",
      "description": "Application for automated IT support ticket triage and resolution.",
      "type": "app",
      "publisher": "Contoso IT",
      "version": "1.5.3",
      "status": "active",
      "createdDateTime": "2025-03-15T10:00:00Z",
      "lastModifiedDateTime": "2025-08-20T11:00:00Z",
      "permissions": [
        { "name": "User.Read.All", "type": "application" }
      ],
      "deployedTo": [
        { "id": "org-contoso", "displayName": "Contoso", "type": "organization" }
      ]
    }
  ],
  "@odata.count": 2
}
```

## Instructions

When the user wants to list, browse, or inventory apps and agents deployed across Microsoft 365, use this operation by making a GET request to `/copilot/packages`. Use the `type` parameter to filter by app, agent, or all. Results include package details, permissions, and deployment targets.
