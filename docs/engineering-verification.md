# Engineering verification before public release

This repository packages the existing hosted Whatsable MCP endpoint. It does not implement or modify the Whatsable backend.

## Backend and OAuth checks

- Confirm `https://api.whatsable.app/mcp` is the correct production endpoint.
- Confirm Streamable HTTP transport is enabled in production.
- Test MCP initialization, `tools/list`, and representative `tools/call` operations from Cursor.
- Test OAuth Authorization Code with PKCE S256 in Cursor Desktop.
- Test OAuth in Cursor Web / Agents if supported by the production deployment.
- Verify Dynamic Client Registration if required by the OAuth implementation.
- Verify Protected Resource Metadata and resource/audience handling.
- Verify refresh-token rotation, expiration, revocation, and authorization errors.
- Confirm which Cursor redirect URIs must be registered by the OAuth provider; use Cursor's current official documentation rather than assuming callback URLs.
- Review tool schemas, descriptions, and annotations against actual behavior, especially read-only, additive, and destructive operations.
- Confirm subscription and permission errors are understandable and do not expose sensitive information.

## Product and legal checks

- Confirm the legal publisher name and approved support contact.
- Add public website, Privacy Policy, and Terms of Service URLs.
- Confirm the plugin's open-source license with the rights holder.
- Review Cursor Marketplace terms against Whatsable's subscription and account-access model.
- Approve use of the Whatsable logo and product description.

## Security checks

- No secrets, tokens, private keys, or customer data in Git history.
- No hardcoded credentials in plugin configuration.
- OAuth must use the supported host authorization flow.
- Logging must not expose credentials or sensitive message content.
