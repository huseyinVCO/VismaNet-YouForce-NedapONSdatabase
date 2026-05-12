# VismaNet-YouForce-NedapONSdatabase

PostgreSQL schema and trigger logic for managing integrations between VismaNet, YouForce WFM, and Nedap ONS.

## Repository Contents

- `DatabaseTables`: SQL script containing table definitions, functions, and triggers.

## Included Database Objects

The SQL script creates and maintains the following core tables:

- `dbusers`
- `wfm_nedapons_clients`
- `vismanet_nedapons_clients`
- `nedapons`

It also includes:

- Trigger functions for automatic `changeuser` and `changetimestamp` maintenance.
- Client lookup helper function (`get_clientid`).
- Active-state synchronization logic between `nedapons` and client tables.

## Prerequisites

- PostgreSQL with `plpgsql` enabled.
- Extension/function support for `gen_random_uuid()` (typically from `pgcrypto`).

## How To Apply

Run the SQL script against your target database:

```bash
psql -d <database_name> -f DatabaseTables
```

## Notes

- The schema enforces that each `nedapons` row is linked to exactly one client source (VismaNet or WFM).
- Triggers update audit fields and client active status automatically.
