# Microsoft 365 Copilot Sandbox
This is sandbox for the Microsoft 365 Copilot Sandbox API, using an OpenAPI specification with examples, Microcks and Bruno as the sandbox interface, and this GitHub repository as the vehicle for delivering as a localized sandbox, or also enabling the working directly with production APIs.

## APIs.json Index
There is an APIs.yml file in the root of this repository, providing an index of all the artifacts used as part of this capability, providing a machine-readable way to read, manage, and execute the resources available here.

## OpenAPI
This capability uses OpenAPI as the definition, providing a complete definition of all available paths for the Microsoft 365 Copilot Sandbox. The OpenAPI for this capability uses examples and Microcks extensions to mock the requests and responses for each API operation, something we will iterate and expand upon with richer examples as the capability evolves.

## Microcks
This capability uses Microcks to deliver the mock API. [You just install Microcks, with the Docker extension being the easiest](https://microcks.io/documentation/guides/installation/docker-desktop-extension/), [import the OpenAPI as a service](openapi/notion-openapi.yml), and you have a mocked API for all APIs, available via REST and MCP APIs--providing a multi-protocol sandbox.

## Bruno
This capability [uses Bruno as the client](https://www.usebruno.com/), leveraging Bruno Collections pre-generated from the OpenAPI and Bruno environments that uses the localhost and port of Microcks to work with the mocked API. You just have to install Microcks, then open the collection provided in this repository, select the available environments, and begin calling the Microsoft 365 Copilot Sandbox via the sandbox or production.

## OpenAPIs
These are the OpenAPIs available for the Microsoft 365 Copilot Sandbox, which are made available via this sandbox API, which can be imported into Microcks and deployed as a sandbox using their mock feature.

  - [Microsoft Copilot Api.yaml](openapi/microsoft-copilot-api.yaml)

## Agent Skills
These are the individual agent skills available for the Microsoft 365 Copilot Sandbox, each mapping to a specific API operation and providing the context needed for AI agents to interact with the API.

### Content Retrieval
  - [Retrieve Relevant Content](skills/retrieve-relevant-content/SKILL.md) - POST `/copilot/retrieval/query`

### Content Search
  - [Search OneDrive Content](skills/search-onedrive-content/SKILL.md) - POST `/copilot/search/query`

### Interaction Exports
  - [List Copilot Interactions](skills/list-copilot-interactions/SKILL.md) - GET `/copilot/interactions`
  - [Get Copilot Interaction](skills/get-copilot-interaction/SKILL.md) - GET `/copilot/interactions/{interactionId}`

### Change Notifications
  - [Create Change Notification Subscription](skills/create-change-notification-subscription/SKILL.md) - POST `/copilot/subscriptions`
  - [List Change Notification Subscriptions](skills/list-change-notification-subscriptions/SKILL.md) - GET `/copilot/subscriptions`
  - [Get Subscription](skills/get-subscription/SKILL.md) - GET `/copilot/subscriptions/{subscriptionId}`
  - [Update Subscription](skills/update-subscription/SKILL.md) - PATCH `/copilot/subscriptions/{subscriptionId}`
  - [Delete Subscription](skills/delete-subscription/SKILL.md) - DELETE `/copilot/subscriptions/{subscriptionId}`

### Meeting Insights
  - [Get Meeting Insights](skills/get-meeting-insights/SKILL.md) - GET `/copilot/meetings/{meetingId}/insights`
  - [List Meetings with Insights](skills/list-meetings-with-insights/SKILL.md) - GET `/copilot/meetings`

### Chat Completions
  - [Send Message to Copilot](skills/send-message-to-copilot/SKILL.md) - POST `/copilot/chat/completions`
  - [Create Chat Thread](skills/create-chat-thread/SKILL.md) - POST `/copilot/chat/threads`
  - [Get Chat Thread](skills/get-chat-thread/SKILL.md) - GET `/copilot/chat/threads/{threadId}`

### Usage Reports
  - [Get Copilot Usage Report](skills/get-copilot-usage-report/SKILL.md) - GET `/reports/copilot/usage`
  - [Get Per-User Usage Details](skills/get-per-user-usage-details/SKILL.md) - GET `/reports/copilot/usage/userDetail`

### Packages
  - [List Apps and Agents](skills/list-apps-and-agents/SKILL.md) - GET `/copilot/packages`
  - [Get Specific Package](skills/get-specific-package/SKILL.md) - GET `/copilot/packages/{packageId}`
  - [Update Package](skills/update-package/SKILL.md) - PATCH `/copilot/packages/{packageId}`
  - [Remove Package](skills/remove-package/SKILL.md) - DELETE `/copilot/packages/{packageId}`

## Support
Please provide any questions or feedback via GitHub issues, or just email kinlane@naftiko.io with feedback. The goal is to keep iterating upon this sandboxes using existing OpenAPI, Microcks, and Bruno features, offering value out of the box via this forkable capability.

