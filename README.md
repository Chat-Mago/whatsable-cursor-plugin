# Whatsable for Cursor

Connect Cursor to **Whatsable**, the WhatsApp Business communication and automation platform, through the Model Context Protocol (MCP).

Whatsable exposes account and WhatsApp Business workflows to compatible AI clients. Depending on the permissions granted during authorization and the account's configuration, the available tools can cover account information, contacts, conversations, messages, labels, templates, scheduled messages, broadcasts, AI bots, and analytics.

- Website: [whatsable.app](https://whatsable.app)
- Documentation: [docs.whatsable.app](https://docs.whatsable.app)
- Support: [team@whatsable.app](mailto:team@whatsable.app)

## What the integration provides

The hosted Whatsable MCP server lets Cursor discover and use the tools and resources authorized for the connected Whatsable account. The tool catalogue is permission-aware: the tools visible to one account or OAuth connection may differ from another.

Examples of supported workflow areas include:

- Inspecting account information and connected WhatsApp numbers.
- Finding contacts and reviewing conversations and messages.
- Working with labels, templates, scheduled messages, and broadcasts when the required scopes are granted.
- Accessing available AI bot and analytics functionality when permitted.

Some tools can create, update, delete, schedule, or send content. Review the proposed action, recipient, content, and account before approving any operation that changes data or sends a message.

## MCP server

- **Endpoint:** `https://api.whatsable.app/mcp`
- **Transport:** Streamable HTTP
- **Authentication:** OAuth 2.1 authorization flow; users authenticate with Whatsable through Cursor.

This repository contains client-side plugin configuration and documentation. It does not contain or replace the hosted Whatsable MCP backend.

## Install

Once the listing is available, find **Whatsable** in Cursor's Customize / Marketplace experience or through Cursor Directory, install it, and select **Authenticate** to authorize your Whatsable account.

For local development and testing, follow [Cursor's plugin documentation](https://cursor.com/docs/plugins).

## Account and permission requirements

You need a Whatsable account and the relevant account access to use the integration. The tools and resources exposed to Cursor depend on the OAuth scopes approved for the connection, the Whatsable account's permissions, and its connected WhatsApp Business setup. Some capabilities may require a particular subscription or additional permissions.

If a tool is not listed, check the permissions granted to the Cursor connection and the corresponding Whatsable account role before assuming the server is unavailable.

## Security and safe use

- Authentication is handled by Whatsable's OAuth flow. Do not put API keys, access tokens, refresh tokens, client secrets, or private keys in this repository.
- Grant only the Whatsable permissions needed for the intended workflows.
- Review message recipients and content before sending.
- Review the effect of create, update, delete, scheduling, broadcast, and AI configuration actions before approving them.
- Do not place customer data, message content, or account credentials in issues or public logs.
- Disconnect the integration from Cursor or revoke its authorization in Whatsable when access is no longer needed.

## Privacy, terms, and support

- [Privacy Policy](https://whatsable.app/privacy/)
- [Terms of Service](https://whatsable.app/terms)
- [Whatsable documentation](https://docs.whatsable.app)
- [Email support](mailto:team@whatsable.app)

Whatsable is a product of **Automazing, LLC**. Whatsable is not affiliated with, endorsed by, or sponsored by WhatsApp LLC or Meta Platforms, Inc. WhatsApp is a registered trademark of Meta Platforms, Inc.

## Publisher and repository

- Publisher: **Automazing, LLC (doing business as Whatsable)**
- Repository: [Chat-Mago/whatsable-cursor-plugin](https://github.com/Chat-Mago/whatsable-cursor-plugin)
- Product homepage: [https://whatsable.app](https://whatsable.app)

## License

A license has not yet been assigned to this repository. Do not assume that the license on another Whatsable integration repository automatically applies here. The rights holder must approve the license for this repository before public marketplace submission.
