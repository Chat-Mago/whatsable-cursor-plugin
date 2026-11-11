# Whatsable for Cursor

Connect Cursor to Whatsable through the hosted Model Context Protocol (MCP) server.

Whatsable provides WhatsApp Business capabilities through MCP. The tools and actions available to a user depend on their Whatsable account, permissions, connected WhatsApp Business setup, and subscription.

## MCP connection

- **Server:** `https://api.whatsable.app/mcp`
- **Transport:** Streamable HTTP
- **Authentication:** OAuth — production compatibility must be verified in Cursor before public release.

## Install

Once listed, install Whatsable from the Cursor Marketplace or Cursor Directory and complete the Whatsable authorization flow when prompted.

For local testing, follow [Cursor's plugin documentation](https://cursor.com/docs/plugins).

## Account requirements

Some capabilities may require an active Whatsable subscription, a connected WhatsApp Business account, and appropriate account permissions. Availability is determined by Whatsable.

## Security

- Never place API keys, access tokens, refresh tokens, client secrets, or private keys in this repository.
- Users should authenticate through the official Whatsable authorization flow.
- Do not share your Whatsable credentials with anyone.

## Support and legal

Before publication, add and verify the official public URLs for:
- Whatsable website
- Support contact
- Privacy Policy
- Terms of Service

## Publisher

Whatsable / Chat-Mago. Confirm the legal publisher name and contact details before marketplace submission.

## License

A license has intentionally not been added yet. Obtain approval from the rights holder and confirm Cursor Marketplace licensing requirements before choosing and publishing a license.
