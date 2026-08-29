# Emby Service Production Audit

- **Code baseline:** `a4c361a6f`
- **Status:** `EMBY_SERVICE_PLATFORM=WITHHOLD_GO`
- **Member gate:** `HOLD`
- **Worker deployment:** `ad397412-cf65-4e72-a438-e392d8533b54`
- **Pages production deployment:** `fb16530a-de67-443b-b754-9f2a8c65f95e`
- **Gateway:** deployment not required; no gateway source path changed in the mission

## Member Management Gate

The production schema migration and deployment completed, and the deployed Worker version endpoint reports `web_commit=a4c361a6f`. The production Admin bundle is available at `https://media.hengmao.org/admin/emby` and includes the requested credential/lifecycle controls and collapse controls.

The authenticated production acceptance is not complete. The Admin API correctly rejects unauthenticated requests with `401`, and no secure owner/admin session was available. The database currently contains four Emby members, so creating and testing five labeled production test members through the audited workflow remains blocked.

The detailed evidence and final member machine gate are in [`emby-member-production-acceptance.json`](./emby-member-production-acceptance.json).

## Hard Gates intentionally not passed

The following remain false or unverified and must not be inferred from the member management deployment:

- Movies, TV, and Stream Library Adapter
- PlaybackInfo / MediaSources
- Real media bytes
- Automatic fallback
- Emby Web, iOS, Android, and TV client matrix
- Final total audit

A successful member Admin deployment does not authorize a platform GO.

## Required next action

Provide or authorize a secure production owner/admin login session for the acceptance run. Do not place the password in source, reports, chat, or shell history. After authenticated access is available, create at least five clearly labeled test members and complete the matrix in the detailed acceptance report.
