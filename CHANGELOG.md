# OpenClaw DaaS — Changelog (Auto-generiert)
> Letzte Aktualisierung: 2026-03-02 18:04 UTC

## de4adc2 — feat: Admin Reset + KI-Wissensdatenbank (selbstlernendes System)
- **Datum:** 2026-03-02 08:17:55 +0000
- **Autor:** e2kk2e
- **Dateien:**


 backend/app/auth.py                     |  25 +++-
 backend/app/ki_learner.py               | 190 +++++++++++++++++++++++++++++
 backend/app/main.py                     |  70 +++++++++++
 backend/migrations/016_ki_knowledge.sql |  19 +++
 frontend/src/App.js                     | 204 +++++++++++++++++++++++++++++++-
 frontend/src/api.js                     |   7 ++
 6 files changed, 507 insertions(+), 8 deletions(-)
## f49ee61 — feat: DTVP-Collector (Deutsches Vergabeportal) + OpenClaw→DaaS Branding
- **Datum:** 2026-03-02 07:48:30 +0000
- **Autor:** e2kk2e
- **Dateien:**


 .../src/ausschreibungen/collectors/dtvp.py         | 114 +++++++++++++++++++++
 dsgvo_package/src/ausschreibungen/config.py        |   1 +
 dsgvo_package/src/ausschreibungen/orchestrator.py  |   3 +
 frontend/src/App.js                                |  10 +-
 4 files changed, 123 insertions(+), 5 deletions(-)
## 60c6e3a — v2.1: Favoriten-Kanban, Design-Optimierung, Playwright Web-Scraper
- **Datum:** 2026-03-02 07:29:01 +0000
- **Autor:** e2kk2e
- **Dateien:**


 PROGRESS.md                                        |  46 +++++
 backend/app/main.py                                |   3 +
 dsgvo_package/Dockerfile                           |   3 +
 dsgvo_package/requirements.txt                     |   1 +
 .../ausschreibungen/collectors/db_bieterportal.py  | 193 +++++++++++++--------
 .../src/ausschreibungen/collectors/evergabe_rss.py | 106 ++++++++---
 .../src/ausschreibungen/collectors/web_scraper.py  | 174 +++++++++++++++++++
 dsgvo_package/src/ausschreibungen/config.py        |   2 +
 dsgvo_package/src/ausschreibungen/orchestrator.py  |   9 +
 .../src/ausschreibungen/playwright_browser.py      | 175 +++++++++++++++++++
 frontend/src/App.css                               |  62 +++++--
 frontend/src/App.js                                | 111 +++++++++---
 frontend/src/api.js                                |   3 +-
 13 files changed, 754 insertions(+), 134 deletions(-)
## 2006d3c — Phase 6: Dokumentation aktualisiert (PROGRESS, README, ZUSAMMENFASSUNG, SOLL_IST)
- **Datum:** 2026-03-02 05:46:12 +0000
- **Autor:** e2kk2e
- **Dateien:**


 PROGRESS.md                | 51 ++++++++++++++++++++++++++++++++++++
 PROJEKT_ZUSAMMENFASSUNG.md | 54 ++++++++++++++++++++++++++++----------
 README.md                  | 49 ++++++++++++++++++++++++++++++++++
 docs/SOLL_IST_VERGLEICH.md | 65 ++++++++++++++++++++++++++++++++++++++++++++++
 4 files changed, 206 insertions(+), 13 deletions(-)
## 4c46d41 — Phase 5: Testing bestanden — Fixes für DeepSeek Token-Limit + CRM memoryview
- **Datum:** 2026-03-02 05:32:28 +0000
- **Autor:** e2kk2e
- **Dateien:**


 backend/app/crm_service.py                  | 6 +++++-
 backend/app/deepseek_v2_2.py                | 1 +
 backend/app/integrations/deepseek_client.py | 6 ++++--
 backend/requirements.txt                    | 1 +
 4 files changed, 11 insertions(+), 3 deletions(-)
## 934faec — Phase 4: Automatisierung — Scoring, Digest v2.2, CRM-Retry, Cron-Jobs
- **Datum:** 2026-03-02 02:55:17 +0000
- **Autor:** e2kk2e
- **Dateien:**


 backend/tasks/__init__.py        |   0
 backend/tasks/crm_retry.py       | 248 ++++++++++++++++++++++++++++
 backend/tasks/daily_digest_v2.py | 345 +++++++++++++++++++++++++++++++++++++++
 backend/tasks/daily_scoring.py   | 310 +++++++++++++++++++++++++++++++++++
 backend/tasks/run_tasks.py       |  64 ++++++++
 ops/crontab.example              |  18 +-
 ops/scripts/run_all_tasks.sh     |  11 ++
 ops/scripts/run_crm_retry.sh     |   6 +
 ops/scripts/run_digest_v2.sh     |   6 +
 ops/scripts/run_scoring.sh       |   6 +
 10 files changed, 1008 insertions(+), 6 deletions(-)
## ab3317a — Phase 3: Frontend Wizard + CRM + Lead-Detail v2.2 + Sidebar
- **Datum:** 2026-03-02 02:42:37 +0000
- **Autor:** e2kk2e
- **Dateien:**


 frontend/src/App.css |  79 +++++++
 frontend/src/App.js  | 614 ++++++++++++++++++++++++++++++++++++++++++++++++++-
 frontend/src/api.js  |  29 +++
 3 files changed, 713 insertions(+), 9 deletions(-)
## fac6b89 — Phase 2: Backend Scoring v3 + Analyse v2.2 + CRM-Service + Endpoints
- **Datum:** 2026-03-02 02:35:24 +0000
- **Autor:** e2kk2e
- **Dateien:**


 backend/app/crm_service.py   | 307 ++++++++++++++++++++++++++++++++++++++
 backend/app/deepseek_v2_2.py | 171 ++++++++++++++++++++++
 backend/app/main.py          | 341 ++++++++++++++++++++++++++++++++++++++++++-
 backend/app/scoring_v3.py    | 203 ++++++++++++++++++++++++++
 backend/app/settings.py      |   4 +
 5 files changed, 1025 insertions(+), 1 deletion(-)
## a6029a5 — Phase 1: DB-Migrationen 013-015 (Scoring v3, Analyse v2.2, CRM)
- **Datum:** 2026-03-02 02:26:07 +0000
- **Autor:** e2kk2e
- **Dateien:**


 backend/migrations/013_scoring_v3_and_catalog.sql | 124 ++++++++++++++++++++++
 backend/migrations/014_analyse_v2_2.sql           |  15 +++
 backend/migrations/015_crm_automation.sql         |  43 ++++++++
 3 files changed, 182 insertions(+)
## 3fd771a — fix: Cronjob-Fixes + System-Status Snapshot
- **Datum:** 2026-03-01 02:01:52 +0000
- **Autor:** e2kk2e
- **Dateien:**


 ops/scripts/run_digest.sh     |   6 ++
 ops/status/system_status.json | 104 +++++++++++++++++++++++
 ops/status/system_status.md   | 186 ++++++++++++++++++++++++++++++++++++++++++
 3 files changed, 296 insertions(+)
## be6ced4 — fix: TED API v3 Felder, nicht erreichbare Quellen deaktiviert
- **Datum:** 2026-02-28 22:06:13 +0000
- **Autor:** e2kk2e
- **Dateien:**


 dsgvo_package/config/ted_search_config.json        | 15 ++--
 .../src/ausschreibungen/collectors/evergabe_rss.py |  3 +-
 .../src/ausschreibungen/collectors/ted.py          | 92 ++++++++++++++++------
 dsgvo_package/src/ausschreibungen/config.py        |  6 +-
 4 files changed, 84 insertions(+), 32 deletions(-)
## 00eff7a — feat: Favoriten, Duplikate löschen, Parser-Fix, Score-Optimierung
- **Datum:** 2026-02-28 16:26:24 +0000
- **Autor:** e2kk2e
- **Dateien:**


 backend/app/main.py                                | 41 +++++++++++-
 .../migrations/007_bulk_score_apply_optimized.sql  |  2 +-
 backend/migrations/012_favorites.sql               |  5 ++
 .../src/ausschreibungen/collectors/evergabe_rss.py | 17 ++++-
 .../ausschreibungen/collectors/service_bund_rss.py | 32 +++++++--
 .../src/ausschreibungen/collectors/ted.py          |  8 ++-
 frontend/src/App.css                               | 10 +++
 frontend/src/App.js                                | 76 ++++++++++++++++++----
 frontend/src/api.js                                |  4 +-
 9 files changed, 171 insertions(+), 24 deletions(-)
## e217e2b — feat: Prio-5 komplett – Kanban, Notifications, Enrichment, Auto-Analyse, Trends
- **Datum:** 2026-02-28 02:56:27 +0000
- **Autor:** e2kk2e
- **Dateien:**


 PROGRESS.md                                 |  10 +
 backend/app/main.py                         | 236 +++++++++++++++++++-
 backend/migrations/011_buyer_enrichment.sql |   9 +
 dsgvo_package/src/ausschreibungen/config.py |   6 +-
 frontend/src/App.css                        | 102 +++++++++
 frontend/src/App.js                         | 334 +++++++++++++++++++++++++++-
 frontend/src/api.js                         |  14 +-
 scripts/daily_notifier.py                   |  13 +-
 8 files changed, 714 insertions(+), 10 deletions(-)
## 7e331f3 — fix: R2 Backup-Script nutzt korrekten Bucket-Namen aus .env
- **Datum:** 2026-02-28 02:28:23 +0000
- **Autor:** e2kk2e
- **Dateien:**


 ops/scripts/backup_to_r2.sh | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
## 29acae0 — feat: 100% Soll-Zustand – Buyer Bonus, 4 Parser, API-Version, Backup-Status, rclone
- **Datum:** 2026-02-28 01:52:32 +0000
- **Autor:** e2kk2e
- **Dateien:**


 PROGRESS.md                                        |  13 +++
 backend/app/main.py                                |  67 +++++++++--
 backend/migrations/010_buyer_bonuses.sql           |   6 +
 docker-compose.yml                                 |   2 +-
 docs/SOLL_IST_VERGLEICH.md                         |  60 +++++-----
 .../ausschreibungen/collectors/db_bieterportal.py  | 122 +++++++++++++++++++++
 .../src/ausschreibungen/collectors/evergabe_rss.py |  73 ++++++++++++
 .../ausschreibungen/collectors/handelsregister.py  |  81 ++++++++++++++
 .../ausschreibungen/collectors/subreport_elvis.py  | 111 +++++++++++++++++++
 dsgvo_package/src/ausschreibungen/config.py        |   3 +
 dsgvo_package/src/ausschreibungen/orchestrator.py  |   9 ++
 frontend/src/App.js                                |  28 ++++-
 ops/scripts/backup_to_r2.sh                        |   9 +-
 ops/scripts/setup_rclone_r2.sh                     |  47 ++++++++
 14 files changed, 581 insertions(+), 50 deletions(-)
## d9adbf8 — docs: Soll-Ist-Vergleich aktualisiert – 38% → 84% Umsetzungsgrad
- **Datum:** 2026-02-28 01:21:55 +0000
- **Autor:** e2kk2e
- **Dateien:**


 docs/SOLL_IST_VERGLEICH.md | 177 ++++++++++++++++++++++-----------------------
 1 file changed, 86 insertions(+), 91 deletions(-)
## c396b7b — feat: Prio-3 komplett – DeepSeek Digest, Security Headers, Usage Stats, Cronjobs
- **Datum:** 2026-02-28 01:17:13 +0000
- **Autor:** e2kk2e
- **Dateien:**


 PROGRESS.md                               |  15 ++--
 backend/app/logging_config.py             |  32 +++++++++
 backend/app/main.py                       |  69 +++++++++++++++++++
 backend/requirements.txt                  |   1 +
 frontend/src/App.js                       | 109 ++++++++++++++++++++++++++++++
 frontend/src/api.js                       |   3 +
 nginx.conf                                |   8 +++
 ops/crontab.example                       |  12 ++++
 ops/fail2ban/filter.d/daas-api.conf       |   4 ++
 ops/fail2ban/filter.d/daas-ratelimit.conf |   4 ++
 ops/fail2ban/jail.local                   |  24 +++++++
 scripts/daily_notifier.py                 |  61 ++++++++++++++++-
 12 files changed, 333 insertions(+), 9 deletions(-)
## 98f2f7d — feat: Prio-2 komplett – Multi-Tenant, Score-Config V2 UI, Sources Health, Datenquellen
- **Datum:** 2026-02-28 00:08:47 +0000
- **Autor:** e2kk2e
- **Dateien:**


 PROGRESS.md                                  |  11 +-
 backend/app/main.py                          | 157 +++++++++++++++++++++-----
 backend/migrations/009_leads_customer_id.sql |  10 ++
 dsgvo_package/config/db_bieterportal.json    |  36 +++++-
 dsgvo_package/config/evergabe_rss.json       |  37 ++++++-
 dsgvo_package/config/handelsregister.json    |  37 ++++++-
 dsgvo_package/config/subreport_elvis.json    |  42 ++++++-
 frontend/src/App.js                          | 159 +++++++++++++++++++++++++--
 8 files changed, 448 insertions(+), 41 deletions(-)
## 5c421fb — feat: Prio-1 komplett – Scoring V2, Multi-Tenant Notifier, Backup/Status Scripts
- **Datum:** 2026-02-27 21:53:54 +0000
- **Autor:** e2kk2e
- **Dateien:**


 PROGRESS.md                                        |  46 ++-
 backend/app/main.py                                | 322 +++++++++++++++++----
 backend/migrations/006_score_v2.sql                |  16 +-
 .../migrations/007_bulk_score_apply_optimized.sql  | 121 +++++++-
 backend/migrations/008_notification_tables.sql     |  33 ++-
 docs/SOLL_IST_VERGLEICH.md                         | 169 +++++++++++
 frontend/src/App.js                                |  38 +++
 frontend/src/api.js                                |   8 +
 nginx.conf                                         |   5 +
 ops/scripts/backup_to_r2.sh                        |  62 +++-
 ops/scripts/status.sh                              | 125 +++++++-
 scripts/daily_notifier.py                          | 227 ++++++++++++++-
 12 files changed, 1100 insertions(+), 72 deletions(-)
## b93d04c — chore: add docs, dsgvo configs, package-lock; remove 28 obsolete scripts
- **Datum:** 2026-02-27 20:24:59 +0000
- **Autor:** e2kk2e
- **Dateien:**


 BENUTZERANLEITUNG.md                      |   425 +
 DAAS_OPTIMIZATION_SUMMARY.md              |   205 +
 PROJEKT_ZUSAMMENFASSUNG.md                |    91 +
 SETUP_VPS.sh                              |    91 +
 STARTANLEITUNG.md                         |   166 +
 VPS_EINZEILER.sh                          |    12 +
 daas_smoke.sh                             |    41 +
 dsgvo_package/.env.example                |    50 +
 dsgvo_package/.github/workflows/ci.yml    |    20 +
 dsgvo_package/config/db_bieterportal.json |     1 +
 dsgvo_package/config/evergabe_rss.json    |     1 +
 dsgvo_package/config/handelsregister.json |     1 +
 dsgvo_package/config/subreport_elvis.json |     1 +
 frontend/package-lock.json                | 17076 ++++++++++++++++++++++++++++
 14 files changed, 18181 insertions(+)
## 3c38ccc — feat: score-config, deepseek analysis, dashboard rewrite, docker/infra fixes
- **Datum:** 2026-02-27 20:24:06 +0000
- **Autor:** e2kk2e
- **Dateien:**


 .env.example                                       |   10 +
 CLAUDE.md                                          |   38 +
 PROGRESS.md                                        |   68 ++
 backend/app/integrations/deepseek_client.py        |   54 +
 backend/app/main.py                                |  391 +++++-
 backend/app/settings.py                            |    4 +
 backend/migrations/003_score_config.sql            |   18 +
 backend/migrations/004_leads_status.sql            |    9 +
 backend/migrations/005_lead_analyses.sql           |   17 +
 backend/migrations/006_score_v2.sql                |    1 +
 .../migrations/007_bulk_score_apply_optimized.sql  |    1 +
 backend/migrations/008_notification_tables.sql     |    1 +
 backend/requirements.txt                           |    1 +
 docker-compose.vps.yml                             |   45 +-
 docker-compose.yml                                 |    9 +-
 docs/GROK_HANDOFF_LOG.md                           |  432 +++++++
 docs/PROJEKT_DOKUMENTATION.md                      |  883 ++++++++++++++
 frontend/package.json                              |    6 +-
 frontend/src/App.css                               | 1077 ++++++++++++----
 frontend/src/App.js                                | 1290 +++++++++++++++-----
 frontend/src/api.js                                |   30 +-
 nginx.conf                                         |   26 +
 ops/scripts/backup_to_r2.sh                        |    1 +
 ops/scripts/status.sh                              |    1 +
 scripts/daily_notifier.py                          |    1 +
 25 files changed, 3861 insertions(+), 553 deletions(-)
## ea515e2 — fix: update TED search config for new API v3 query syntax
- **Datum:** 2026-02-26 20:26:24 +0000
- **Autor:** e2kk2e
- **Dateien:**


 dsgvo_package/config/ted_search_config.json | 15 ++++++---------
 1 file changed, 6 insertions(+), 9 deletions(-)
## facdefc — feat: live collector log panel in dashboard
- **Datum:** 2026-02-26 20:11:43 +0000
- **Autor:** e2kk2e
- **Dateien:**


 backend/app/main.py | 22 +++++++++++++++++-
 frontend/src/App.js | 67 +++++++++++++++++++++++++++++++++++++++++++++++++++--
 frontend/src/api.js |  1 +
 3 files changed, 87 insertions(+), 3 deletions(-)
## b11ec80 — fix: restore REACT_APP_API_BASE for frontend (Tailscale IP)
- **Datum:** 2026-02-26 15:32:09 +0000
- **Autor:** e2kk2e
- **Dateien:**


 docker-compose.yml | 1 +
 1 file changed, 1 insertion(+)
## 44cf075 — fix: harden docker-compose security (remove public postgres/redis ports)
- **Datum:** 2026-02-26 15:20:23 +0000
- **Autor:** e2kk2e
- **Dateien:**


 docker-compose.yml | 24 ++++++++++++++++--------
 1 file changed, 16 insertions(+), 8 deletions(-)
## 75266ae — feat: collector pipeline fixes + dashboard controls + source module
- **Datum:** 2026-02-26 15:11:26 +0000
- **Autor:** e2kk2e
- **Dateien:**


 .gitignore                                         |  11 +
 backend/app/main.py                                |  79 ++++++
 backend/requirements.txt                           |   1 +
 docker-compose.yml                                 |   4 +-
 dsgvo_package/src/ausschreibungen/__init__.py      |   2 +
 .../src/ausschreibungen/collectors/__init__.py     |   0
 .../src/ausschreibungen/collectors/ted.py          |   2 +-
 dsgvo_package/src/ausschreibungen/config.py        |  41 +++
 dsgvo_package/src/ausschreibungen/dedupe.py        |  23 ++
 dsgvo_package/src/ausschreibungen/digest.py        |  21 ++
 dsgvo_package/src/ausschreibungen/http_client.py   |  40 +++
 dsgvo_package/src/ausschreibungen/logging_utils.py |  24 ++
 dsgvo_package/src/ausschreibungen/main.py          |  29 +++
 dsgvo_package/src/ausschreibungen/models.py        |  27 ++
 dsgvo_package/src/ausschreibungen/normalize.py     |  56 ++++
 dsgvo_package/src/ausschreibungen/orchestrator.py  |  84 ++++++
 .../src/ausschreibungen/privacy_housekeeping.py    |  56 ++++
 dsgvo_package/src/ausschreibungen/scoring.py       |  58 +++++
 .../src/ausschreibungen/storage/__init__.py        |   0
 .../src/ausschreibungen/storage/postgres.py        | 148 +++++++++++
 dsgvo_package/src/ausschreibungen/utils_dates.py   |  23 ++
 dsgvo_package/src/ausschreibungen/utils_text.py    |  14 +
 .../tests/fixtures/ted_response_example.json       |  14 +
 .../fixtures/vergabe_nrw_homepage_snippet.html     |  13 +
 dsgvo_package/tests/test_dedupe.py                 |  18 ++
 dsgvo_package/tests/test_scoring.py                |  28 ++
 dsgvo_package/tests/test_ted_parser.py             |  23 ++
 dsgvo_package/tests/test_utils_dates.py            |  17 ++
 dsgvo_package/tests/test_vergabe_nrw_parser.py     |  21 ++
 frontend/nginx.conf                                |  72 ++++++
 frontend/src/App.css                               | 282 +++++++++++++++++++++
 frontend/src/App.js                                |  55 +++-
 frontend/src/api.js                                |   3 +
 33 files changed, 1284 insertions(+), 5 deletions(-)
## 044a792 — Add files via upload
- **Datum:** 2026-02-25 21:27:42 +0100
- **Autor:** e2kk2e
- **Dateien:**


 README.md                                      |  79 +++++++-
 docker-compose.vps.yml                         |  37 ++++
 docker-compose.yml                             | 112 ++++++++++++
 frontend/Dockerfile                            |  12 ++
 frontend/package.json                          |  34 ++++
 frontend/public/index.html                     |  20 ++
 frontend/src/App.js                            | 243 +++++++++++++++++++++++++
 frontend/src/api.js                            |  39 ++++
 frontend/src/index.js                          |   6 +
 ops/scripts/tailscale_serve_https.sh           |  27 +++
 ops/scripts/ufw_allow_tailscale_ports.sh       |  13 ++
 ops/systemd/openclaw-daas-collector.service    |  10 +
 ops/systemd/openclaw-daas-collector.timer      |  10 +
 ops/systemd/openclaw-daas-housekeeping.service |  10 +
 ops/systemd/openclaw-daas-housekeeping.timer   |  10 +
 ops/systemd/openclaw-daas.service              |  16 ++
 16 files changed, 676 insertions(+), 2 deletions(-)
## ba5b1f7 — Add files via upload
- **Datum:** 2026-02-25 21:26:45 +0100
- **Autor:** e2kk2e
- **Dateien:**


 backend/Dockerfile                                 |  14 +
 backend/app/__init__.py                            |   0
 backend/app/audit.py                               |  12 +
 backend/app/auth.py                                |  42 +++
 backend/app/cli.py                                 |  42 +++
 backend/app/db.py                                  |  56 ++++
 backend/app/integrations/__init__.py               |   0
 backend/app/integrations/openclaw_client.py        |  93 ++++++
 backend/app/main.py                                | 190 +++++++++++
 backend/app/rate_limit.py                          |  46 +++
 backend/app/security.py                            |  36 +++
 backend/app/settings.py                            |  37 +++
 backend/app/stripe_billing_skill.py                | 298 +++++++++++++++++
 backend/pytest.ini                                 |   2 +
 backend/requirements-dev.txt                       |   2 +
 backend/requirements.txt                           |   6 +
 backend/tests/conftest.py                          |   7 +
 backend/tests/test_openclaw_client.py              |  33 ++
 backend/tests/test_security.py                     |   8 +
 dashboard_1_reference/ARCHITEKTUR.md               |  32 ++
 dashboard_1_reference/App.tsx                      |  46 +++
 ..._Startpaket_OpenClaw_DSGVO_v2_CollectorPlus.zip | Bin 0 -> 71250 bytes
 dashboard_1_reference/DEPLOYMENT.md                | 356 +++++++++++++++++++++
 dashboard_1_reference/Dashboard.tsx                | 222 +++++++++++++
 dashboard_1_reference/Dockerfile                   |  10 +
 dashboard_1_reference/Logs.tsx                     | 203 ++++++++++++
 dashboard_1_reference/README.md                    |  53 +++
 dashboard_1_reference/README_PLATFORM.md           | 323 +++++++++++++++++++
 dashboard_1_reference/daily_full_run.yaml          |  45 +++
 dashboard_1_reference/db.ts                        | 254 +++++++++++++++
 dashboard_1_reference/deploy-vps.sh                | 170 ++++++++++
 dashboard_1_reference/docker-compose.openclaw.yml  |  81 +++++
 dashboard_1_reference/docker-compose.yml           |  33 ++
 dashboard_1_reference/dockerManager.ts             | 233 ++++++++++++++
 dashboard_1_reference/requirements.txt             |   9 +
 dashboard_1_reference/routers.ts                   | 130 ++++++++
 dashboard_1_reference/schema.ts                    | 163 ++++++++++
 dashboard_1_reference/telegramBot.test.ts          |  59 ++++
 dashboard_1_reference/telegramBot.ts               | 248 ++++++++++++++
 dashboard_1_reference/todo.md                      |  63 ++++
 dashboard_1_reference/workflowScheduler.ts         | 185 +++++++++++
 db/schema.sql                                      | 168 ++++++++++
 docs/ARCHITEKTUR.md                                |  33 ++
 ...itable OpenClaw Business-Ideen (VPS-basiert).md |  85 +++++
 docs/DaaS_Entwicklungsplan_Protokoll.md            | 209 ++++++++++++
 ...s-a-Service (DaaS) in Nischenm\303\244rkten.md" |  81 +++++
 docs/ENTWICKLUNGSPLAN.md                           |  69 ++++
 docs/ENTWICKLUNGSPLAN_UND_PROTOKOLL.md             | 301 +++++++++++++++++
 docs/INSTALLATION.md                               | 161 ++++++++++
 docs/PROTOKOLL.md                                  |  65 ++++
 docs/README.md                                     |  53 +++
 ...ata-as-a-Service (DaaS) mit OpenClaw auf VPS.md | 197 ++++++++++++
 docs/VPS_INTAKE_SUMMARY.md                         |  29 ++
 ...lver.com_blog_web-scraping_data-as-a-service.md | 192 +++++++++++
 dsgvo_package/Dockerfile                           |  10 +
 dsgvo_package/Makefile                             |  16 +
 dsgvo_package/README.md                            |  53 +++
 dsgvo_package/config/lead_profile.elektro_nrw.yaml |  44 +++
 .../config/providers_register.template.yaml        |  27 ++
 dsgvo_package/config/retention_policy.yaml         |  13 +
 dsgvo_package/config/scoring_weights.yaml          |  15 +
 dsgvo_package/config/source_urls.yaml              |  10 +
 dsgvo_package/config/ted_search_config.json        |  20 ++
 dsgvo_package/db/README.md                         |   3 +
 dsgvo_package/db/kpi_views.sql                     |  20 ++
 dsgvo_package/db/schema.sql                        | 119 +++++++
 dsgvo_package/docker-compose.yml                   |  33 ++
 dsgvo_package/docs/ARCHITEKTUR.md                  |  33 ++
 dsgvo_package/docs/GEWINN_AUTOMATION_FLOW.md       |  23 ++
 dsgvo_package/docs/OPENCLAW_IMPORT_MAPPING.md      |  26 ++
 dsgvo_package/docs/OPENCLAW_WORKFLOW_MAP.md        |  28 ++
 dsgvo_package/docs/PARSER_WARTUNG_CHECKLISTE.md    |  18 ++
 dsgvo_package/docs/SETUP_VPS_EU.md                 |  25 ++
 dsgvo_package/docs/SOURCES_UND_LIMITS.md           |  39 +++
 dsgvo_package/openclaw/README.md                   |  26 ++
 dsgvo_package/openclaw/prompts/digest_compose.md   |  10 +
 .../openclaw/prompts/enrichment_lead_summary.md    |  25 ++
 .../openclaw/workflows/daily_full_run.yaml         |  45 +++
 .../openclaw/workflows/digest_dispatch.yaml        |  22 ++
 .../openclaw/workflows/healthcheck_run.yaml        |  31 ++
 .../openclaw/workflows/high_priority_fastlane.yaml |  26 ++
 .../openclaw/workflows/privacy_housekeeping.yaml   |  30 ++
 .../openclaw/workflows/retry_failed_source.yaml    |  35 ++
 dsgvo_package/pyproject.toml                       |   2 +
 dsgvo_package/requirements.txt                     |   9 +
 dsgvo_package/scripts/bootstrap_project.ps1        |   5 +
 dsgvo_package/scripts/bootstrap_project.sh         |   6 +
 dsgvo_package/scripts/db_backup.sh                 |   7 +
 dsgvo_package/scripts/export_top_leads.py          |  23 ++
 dsgvo_package/scripts/healthcheck.py               |  18 ++
 dsgvo_package/scripts/profit_projection.py         |  27 ++
 dsgvo_package/scripts/restore_check.py             |  17 +
 dsgvo_package/scripts/run_once.py                  |   8 +
 dsgvo_package/scripts/run_source.py                |  23 ++
 dsgvo_package/scripts/send_digest.py               |  35 ++
 dsgvo_package/src/ausschreibungen/channels.py      |  36 +++
 .../src/ausschreibungen/collectors/base.py         |  19 ++
 .../ausschreibungen/collectors/service_bund_rss.py |  51 +++
 .../src/ausschreibungen/collectors/ted.py          | 119 +++++++
 .../src/ausschreibungen/collectors/vergabe_nrw.py  | 128 ++++++++
 100 files changed, 6843 insertions(+)
## 83d9449 — Add files via upload
- **Datum:** 2026-02-25 20:00:48 +0100
- **Autor:** e2kk2e
- **Dateien:**


 openclaw_daas_vps_prototype_windows.zip | Bin 0 -> 202370 bytes
 1 file changed, 0 insertions(+), 0 deletions(-)
## fd345e8 — Initial commit
- **Datum:** 2026-02-25 06:24:43 +0100
- **Autor:** e2kk2e
- **Dateien:**


 README.md | 2 ++
 1 file changed, 2 insertions(+)
