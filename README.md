# wday-demo-ci

Postman CI demo for the Workday May 15 deep dive with Alex Wang + John Yates.

Runs the `worker-demo` Postman collection via the Postman CLI in GitHub Actions on every push:

- **GET /workers?search=Adam** — live Workday GMS sandbox. 4-test script: status / structural / contract (jsonSchema) / behavior (search filter actually filters).
- **POST /workers/:workerId/checkInTopics** — Postman mock (the Workday sandbox Bearer token is read-only). 4 write-path tests: status 201 / round-trip name integrity / server-assigned ID in Workday WID format / response schema conformance.

The same JSON file runs:
1. In Postman desktop on a developer's laptop (manual exploration)
2. Via Postman CLI on a laptop (one command, same result)
3. In GitHub Actions on every push (this repo's workflow)

No Rest Assured re-implementation required. The rewrite step disappears for net-new APIs.

## Configuration

| | |
|---|---|
| Workspace | `wday-demo` (`5b18a086-833b-4346-af5f-95a1eb672e4c`) |
| Collection | `worker-demo` (`52509354-d6cd65db-36ba-448b-9f89-a2154462cdfb`) |
| Environment | `worker-demo-env` (`52509354-ea9fbd53-5aca-4520-91e3-b3c564d698bb`) |
| Postman team | philip V12 |
| Required secret | `POSTMAN_API_KEY` (philip V12 user key) |

## Workday Bearer Token

The Bearer token for the live Workday sandbox is stored in `worker-demo-env` as a `secret`-type environment variable. It expires daily — refresh from the Workday community site before each demo run, then update the env variable in Postman.




