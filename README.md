# vehicle-reservation-stage3-mcp-server

## Confirmed reservation storage

Confirmed administrator approvals are appended to
`data/confirmed_reservations.txt` in this format:

`Name | Car Number | Reservation Period | Approval Time`

The administrator approval routes write the record through the integrated
reservation store. Each reservation reference is written only once.

For an HTTP MCP server, run:

```powershell
uvicorn mcp_server:app --host 127.0.0.1 --port 8000
```

The MCP tool is available at
`POST /mcp/tools/write_confirmed_reservation`. Set `MCP_API_KEY` and send:

```text
Authorization: Bearer <MCP_API_KEY>
```

For Flask administrator routes, set `ADMIN_API_KEY` and send
`X-Admin-Key: <ADMIN_API_KEY>`. Requests are rejected with HTTP 401 without a
matching key.