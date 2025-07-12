# event-grid-storage-account-blob-notifier-by-direct-portal-entry
az-204 learning project for event grid
# Blob Upload Notifier

## Purpose

This project demonstrates how to set up an automated notification system in Azure that responds whenever a file (blob) is uploaded to a storage account container. The notification is routed through Event Grid and triggers an Azure Function, which can log the event or send an email.

This repo is part of my AZ-204 learning journey. Its goal is to create small, focused examples that are easy to revisit and expand.

---

## Azure Resources Used/Tested

- **Storage Account**: The source of blob events.
- **Event Grid System Topic**: Optional. Subscribes to storage events.
- **Event Subscription**: Routes events from Event Grid to the Azure Function.
- **Azure Function**: Processes the incoming event (logs, emails, etc.).

---

## Step-by-Step Procedure

### 1. Create a Storage Account

- Use the Azure Portal or CLI.
- Example resource name: `az204blobdemo<unique>`

### 2. Enable Event Grid Integration

- Ensure the Storage Account is configured to emit events to Event Grid.
- No manual action is needed for System Topics; Azure creates these automatically.

### 3. Create an Azure Function

- Recommend starting with an **Event Grid Trigger** function.
- Use the Portal, VS Code, or Azure CLI to scaffold the function.
- Function logs received event data (can be extended to email, etc.).

### 4. (Optional) Create an Event Grid System Topic

- For most cases, direct wiring from Storage Account to Function is sufficient.
- If testing advanced routing or filtering, create a System Topic manually.

### 5. Create an Event Subscription

- Point the Event Subscription to the Azure Function's endpoint.
- Select the correct event type (e.g., `BlobCreated`).

### 6. Upload a Blob

- Use Portal or CLI to upload a file to the container.
- This triggers the event flow.

### 7. Inspect Function Logs

- View logs via Azure Portal, Application Insights, or local development tools.
- Confirm event details: blob name, time, size, etc.

### 8. Cleanup

- Delete the storage account, function app, and any Event Grid topics/subscriptions to avoid resource sprawl.
- Double-check for lingering resources (especially Event Grid subscriptions).

---

## Completion Checklist

- [x] Storage account created and configured.
- [x] Azure Function deployed and working.
- [x] Event Grid subscription routing events to function.
- [x] Blob upload triggers event and logs are generated.
- [x] Cleanup steps executed.

---

## Key Memorable Facts

- **Event Grid** automatically creates system topics for Azure resources (like Storage Accounts).
- **Event Grid Trigger** functions require a specially formatted payload; test with actual Azure events.
- You can filter events in the Event Subscription to only those you care about (`BlobCreated`).
- Always clean up Event Grid subscriptions—they can persist even after the source resource is deleted.

---

## Anki Card Ideas

- What is the purpose of an Event Grid System Topic?
- Steps for wiring a Storage Account event to an Azure Function.
- How to inspect and debug Azure Function logs for Event Grid events.
- Differences between direct wiring and using a System Topic.

---

## Resource Naming Convention

- All resources use a prefix indicating the project, e.g., `az204blobdemo`.
- Suffix with a short unique string or initials to avoid collisions.

---

## Additional Thoughts & Insights

- This pattern (event-driven notification) is fundamental for modern cloud automation and integration.
- Try variations: change the trigger to "BlobDeleted," or route events to Logic Apps or Service Bus.
- If the function needs to send emails, explore using SendGrid bindings or the Microsoft Graph API.
- Always review and reference this README and the [AZ-204-Projects conventions document](../CONVENTIONS.md) before starting new projects.

---

## References

- [Azure Event Grid documentation](https://learn.microsoft.com/en-us/azure/event-grid/)
- [Azure Functions documentation](https://learn.microsoft.com/en-us/azure/azure-functions/)
- [Storage Account documentation](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-overview)

---

_This project is intended for learning and experimentation. Feel free to fork, adapt, or extend for your own AZ-204 study!_
