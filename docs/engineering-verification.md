# Engineering verification before public release

This checklist records what must be verified against the production Whatsable MCP server. It is not a statement that every item has passed.

## Current Cursor Desktop audit

The read-only audit performed with the Axel Meta Whatsable account reported:

- Cursor Desktop OAuth and live MCP connection: passed.
- 48 Whatsable tools and 35 resources visible under the tested **Send and read** authorization.
- The tool catalogue contains non-empty descriptions and object input schemas.
- Some list and analytics schemas omit `additionalProperties: false`.
- Cursor's visible tool catalogue did not expose tool annotation hints (`readOnlyHint`, `destructiveHint`, `idempotentHint`, `openWorldHint`) or titles.
- The audit identified 12 additional tools and two resources hidden by the scopes not granted to this connection.
- Cursor Web callback, Cloud Agent authentication, production refresh-token rotation, and revocation were not exercised.

The above is scoped to the tested account and connection. Do not generalize the counts to every Whatsable account or permission level.

## Backend and protocol checks

- [ ] Confirm `https://api.whatsable.app/mcp` remains the production MCP endpoint.
- [ ] Confirm Streamable HTTP transport.
- [x] Cursor Desktop initialization and OAuth were reported working in the read-only audit.
- [ ] Capture a sanitized raw production `tools/list` response and compare it with Cursor's displayed catalogue.
- [ ] Verify tool titles and annotations reach the client, or document why Cursor does not display them.
- [ ] Align each tool description with the scopes required to call it.
- [ ] Decide whether list and analytics schemas should reject unknown fields consistently with strict schemas such as `get_account`.
- [ ] Verify every tool's side effects and classify read-only, additive, and destructive operations truthfully.
- [ ] Review the conservative classification of `schedule_message`; its documented behavior should match whether it queues or sends.
- [ ] Test OAuth Authorization Code with PKCE S256 in Cursor Desktop.
- [ ] Test Cursor Web / Agents callback and Cloud Agent authentication.
- [ ] Test refresh-token rotation, expiry, and revocation in a dedicated test session, not the currently working live session.
- [ ] Verify Protected Resource Metadata, authorization-server metadata, scopes, and resource/audience handling.

## Permission-aware tool catalogue

The audited connection used **Send and read** access. The following tools were reported hidden because their scopes were not granted:

| Tools | Additional scope |
|---|---|
| `create_template`, `delete_template` | `templates:write` |
| `create_label`, `update_label`, `delete_label` | `labels:write` |
| `create_broadcast`, `cancel_broadcast`, `set_broadcast_status` | `broadcasts:write` |
| `create_ai_bot`, `update_ai_bot`, `duplicate_ai_bot`, `delete_ai_bot` | `ai:configure` |

Do not request additional scopes simply to increase the visible tool count. Request only the scopes required by the intended use case.

## Tool annotation review

The audit's expected classifications, derived from the server definitions, were:

- Read-only tools: `readOnlyHint: true`, `destructiveHint: false`.
- Additive tools: `readOnlyHint: false`, `destructiveHint: false`.
- Destructive or externally consequential tools: `destructiveHint: true`.

Engineering must verify the raw MCP response and actual side effects before treating these classifications as final. Sending messages, media, and template messages has external effects and must be classified accordingly.

## Security checks

- [x] No API keys, tokens, or private keys were found in the audited plugin repository.
- [x] The audited MCP configuration relies on OAuth rather than a hardcoded client secret.
- [ ] Confirm logs and error responses never expose access tokens, refresh tokens, or sensitive message content.
- [ ] Verify credential rotation and revocation in a dedicated test account/session.
- [ ] Review the least-privilege scopes requested by the consent flow.

## Product and legal checks

- [ ] Confirm the legal publisher and repository owner are authorized to publish this integration.
- [ ] Obtain approval for the open-source license for this repository.
- [ ] Confirm the Cursor Marketplace terms are compatible with the Whatsable subscription and access model.
- [x] Public Whatsable website, Privacy Policy, Terms of Service, and support email are linked in the README.
- [ ] Approve any logo or other brand asset use in this repository.
