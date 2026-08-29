# Emby Member Production Acceptance

- **Baseline:** `a4c361a6f`
- **Run date:** 2026-08-10
- **Result:** `HOLD`
- **Platform status:** `EMBY_SERVICE_PLATFORM=WITHHOLD_GO`

## What completed

### Production migration

The production D1 database `fireball-auth` (`1bf03bee-501d-4465-8217-4da9aa911818`) reported one pending migration before deployment:

```text
0021_emby_member_credentials_lifecycle.sql
```

The migration executed successfully. A repeat migration check returned `No migrations to apply!`. The new tables were verified without changing existing rows:

- `emby_members`
- `emby_audit_events`
- `emby_stream_leases`

Post-migration counts were 4 users, 4 Emby members, and 0 Emby audit events.

### Worker

Production Worker `fileball-api` was deployed from the detached clean worktree at `a4c361a6f`.

- Final deployment ID: `ad397412-cf65-4e72-a438-e392d8533b54`
- Earlier asset deployment ID: `4e010204-1a38-41a3-afe8-03f3e3a35e64`
- Verification endpoint: `https://v8.hengmao.org/api/v1/version`
- Verified `web_commit`: `a4c361a6f`
- Verified `EMBY_SERVICE_PLATFORM`: `WITHHOLD_GO`

### Pages

The `fireball` Pages project received a production deployment:

- Production deployment ID: `fb16530a-de67-443b-b754-9f2a8c65f95e`
- Preview URL: `https://fb16530a.fireball-b4q.pages.dev`
- Production custom route: `https://media.hengmao.org/admin/emby`
- Verified custom-domain bundle: `assets/index-Cep-8wbN.js`
- Verified custom-domain stylesheet: `assets/index-DCwb2cXy.css`

The deployed bundle contains the Emby management controls, including Create Member, Reset Password, Copy Connection Info, Manage Devices, Terminate Sessions, Archive, and the expand/collapse controls. The page was served from the custom domain after deployment.

### Gateway

`emby-gateway` was **not deployed** because no gateway source path changed between `858590569` and `a4c361a6f`; the member credential lifecycle implementation is in the main Worker and shared D1 migration. Existing gateway health, version, and ready endpoints were checked successfully:

- `https://emby.hengmao.org/health`
- `https://emby.hengmao.org/version`
- `https://emby.hengmao.org/ready`

This is recorded as `gateway_deploy_not_required`, not as a gateway feature verification.

## Production probes

| Probe | Result |
|---|---|
| Worker `/api/v1/version` matches `a4c361a6f` | PASS |
| Admin member endpoint rejects unauthenticated request | PASS (`401`) |
| `https://emby.hengmao.org` is reachable over HTTPS | PASS |
| Gateway health/version/ready | PASS |
| Static production bundle includes requested management controls | PASS |
| Negative Emby login probe rejects an invalid password | PASS |
| Five-member Admin lifecycle acceptance | **BLOCKED** |

## Blocking condition

The production D1 database contains an admin account, but no owner/admin password or browser session was available to this run. The Admin member endpoint correctly returned `401 UNAUTHORIZED` without a session. The production Emby login password is intentionally non-retrievable and was not guessed or bypassed.

There are currently 4 existing Emby members, not the requested 5 new test members. I did not create rows directly in D1 because that would bypass the Admin workflow, omit the required actor audit trail, and invalidate the acceptance evidence.

**One required external action:** provide or authorize a secure production owner/admin login session for the acceptance run. Do not send the password in source, reports, chat, or command history.

## Not falsely marked PASS

Because the authenticated Admin workflow could not be exercised, the following production gates remain unverified:

- Create five clearly labeled test members and receipt contents
- One-time password display and post-close memory cleanup
- Normal copy without password versus receipt copy with password
- Username rename while preserving `user_id` and history/device bindings
- Password reset, old-password rejection, and session/device revocation
- Expiry edit, expiry rejection, and renew recovery
- Role, Movies/TV/Stream, Remote Access, Download, and Transcode enforcement
- Device limit, concurrent-stream limit, device revoke, and session termination
- Production audit records and statistics changes
- Production UI recent-two behavior with five or more members
- Two real Emby authentications using the deployed Host/HTTPS 443 credentials

No plaintext passwords, access tokens, or session tokens are present in this report.

## Automated verification from baseline

- Worker typecheck: **PASS**
- Worker tests: **372 passed**
- Web typecheck: **PASS**
- Web tests: **94 passed**
- Web lint: **PASS**
- Web production build: **PASS**
- Migration SQLite validation: **PASS**
- `git diff --check`: **PASS**

The web dependency tree reported existing npm audit findings; no dependency update was made during this deployment.

## Final machine gate

```json
{
  "emby_member_credentials_gate": {
    "migration_production": true,
    "worker_deployed": true,
    "pages_deployed": true,
    "gateway_synced_or_not_required": true,
    "create_username": false,
    "one_time_password": false,
    "host": true,
    "port_443": true,
    "expiry": false,
    "role_permissions": false,
    "library_permissions": false,
    "admin_edit_username": false,
    "admin_reset_password": false,
    "password_never_retrievable": false,
    "copy_connection_info": false,
    "device_limits": false,
    "concurrency_limits": false,
    "enable_disable": false,
    "renew_expiry": false,
    "device_management": false,
    "session_management": false,
    "audit_trail": false,
    "latest_two_expanded": true,
    "older_members_collapsed": true,
    "expand_all_collapse_all": true,
    "production_synced": false,
    "tests": true
  },
  "status": "HOLD"
}
```

The member gate is not allowed to pass while the authenticated production acceptance is blocked. The broader platform remains `WITHHOLD_GO`; Library, Playback, Client Matrix, real media bytes, fallback, and final audit gates remain false or unverified.
