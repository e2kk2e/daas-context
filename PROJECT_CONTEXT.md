# OpenClaw DaaS — Projekt-Kontext (Auto-generiert)

> **HINWEIS FÜR KI-ASSISTENTEN:** Diese Datei wird automatisch alle 30 Minuten generiert.
> Sie enthält den aktuellen Zustand des Projekts, der Datenbank und der Infrastruktur.
> Nutze diese Datei als primäre Wissensquelle für das OpenClaw DaaS Projekt.

**Letzte Aktualisierung:** 2026-03-02 18:04 UTC
**VPS:** claw-vps | 6.8.0-101-generic | Ubuntu 24.04.4 LTS
**Branch:** main
**Letzter Commit:** de4adc2 feat: Admin Reset + KI-Wissensdatenbank (selbstlernendes System) (10 hours ago)
**Git Tag:** v2.0-grok-enhancements

---

## 1. Projektbeschreibung

OpenClaw DaaS ist eine Data-as-a-Service-Plattform für deutsche öffentliche Vergabedaten.
Das System scraped automatisch Ausschreibungen von service.bund.de, TED und VergabeNRW,
bewertet sie mit einem 5-Faktoren-Scoring-Algorithmus, analysiert sie per KI (DeepSeek)
und pusht relevante Deals automatisch ins CRM des Kunden.

**Tech-Stack:** FastAPI (Python) + React + PostgreSQL + Redis + Docker + Nginx
**Version:** 2.0 (Grok-Erweiterungen integriert)

---

## 2. Docker-Container Status

```
NAMES                         STATUS                  PORTS
daas-project-collector-1      Up 9 hours              
daas-project-backend-1        Up 10 hours             0.0.0.0:8000->8000/tcp, [::]:8000->8000/tcp
daas-project-frontend-1       Up 10 hours (healthy)   100.115.2.40:3000->80/tcp, 127.0.0.1:3000->80/tcp
daas-project-postgres-1       Up 2 days (healthy)     5432/tcp
daas-project-redis-1          Up 2 days (healthy)     6379/tcp
openclaw-openclaw-node-1      Up 3 days               
openclaw-openclaw-gateway-1   Up 3 days (healthy)     100.115.2.40:18789-18790->18789-18790/tcp, 127.0.0.1:18789-18790->18789-18790/tcp
openclaw-openclaw-db-1        Up 3 days (healthy)     5432/tcp
```

---

## 3. Projektstruktur

```
./backend/app/audit.py
./backend/app/auth.py
./backend/app/cli.py
./backend/app/crm_service.py
./backend/app/db.py
./backend/app/deepseek_v2_2.py
./backend/app/__init__.py
./backend/app/ki_learner.py
./backend/app/logging_config.py
./backend/app/main.py
./backend/app/rate_limit.py
./backend/app/scoring_v3.py
./backend/app/security.py
./backend/app/settings.py
./backend/app/stripe_billing_skill.py
./backend/migrations/003_score_config.sql
./backend/migrations/004_leads_status.sql
./backend/migrations/005_lead_analyses.sql
./backend/migrations/006_score_v2.sql
./backend/migrations/007_bulk_score_apply_optimized.sql
./backend/migrations/008_notification_tables.sql
./backend/migrations/009_leads_customer_id.sql
./backend/migrations/010_buyer_bonuses.sql
./backend/migrations/011_buyer_enrichment.sql
./backend/migrations/012_favorites.sql
./backend/migrations/013_scoring_v3_and_catalog.sql
./backend/migrations/014_analyse_v2_2.sql
./backend/migrations/015_crm_automation.sql
./backend/migrations/016_ki_knowledge.sql
./backend/.pytest_cache/README.md
./backend/tasks/crm_retry.py
./backend/tasks/daily_digest_v2.py
./backend/tasks/daily_scoring.py
./backend/tasks/__init__.py
./backend/tasks/run_tasks.py
./backend/tests/conftest.py
./backend/tests/test_openclaw_client.py
./backend/tests/test_security.py
./backup_db.sql
./BENUTZERANLEITUNG.md
./CLAUDE.md
./DAAS_OPTIMIZATION_SUMMARY.md
./daas_smoke.sh
./dashboard_1_reference/ARCHITEKTUR.md
./dashboard_1_reference/daily_full_run.yaml
./dashboard_1_reference/DEPLOYMENT.md
./dashboard_1_reference/deploy-vps.sh
./dashboard_1_reference/docker-compose.openclaw.yml
./dashboard_1_reference/docker-compose.yml
./dashboard_1_reference/README.md
./dashboard_1_reference/README_PLATFORM.md
./dashboard_1_reference/todo.md
./db/schema.sql
./docker-compose.vps.yml
./docker-compose.yml
./docs/ai-context/PROJECT_CONTEXT.md
./docs/ARCHITEKTUR.md
./docs/Brainstorming - Hochprofitable OpenClaw Business-Ideen (VPS-basiert).md
./docs/DaaS_Entwicklungsplan_Protokoll.md
./docs/Dossier - Data-as-a-Service (DaaS) in Nischenmärkten.md
./docs/ENTWICKLUNGSPLAN.md
./docs/ENTWICKLUNGSPLAN_UND_PROTOKOLL.md
./docs/GROK_HANDOFF_LOG.md
./docs/INSTALLATION.md
./docs/PROJEKT_DOKUMENTATION.md
./docs/PROTOKOLL.md
./docs/README.md
./docs/SOLL_IST_VERGLEICH.md
./docs/Technischer Entwicklungsplan - Data-as-a-Service (DaaS) mit OpenClaw auf VPS.md
./docs/VPS_INTAKE_SUMMARY.md
./docs/www.capsolver.com_blog_web-scraping_data-as-a-service.md
./dsgvo_package/config/lead_profile.elektro_nrw.yaml
./dsgvo_package/config/providers_register.template.yaml
./dsgvo_package/config/retention_policy.yaml
./dsgvo_package/config/scoring_weights.yaml
./dsgvo_package/config/source_urls.yaml
./dsgvo_package/db/kpi_views.sql
./dsgvo_package/db/README.md
./dsgvo_package/db/schema.sql
./dsgvo_package/docker-compose.yml
57 Dateien total
```

---

## 4. Datenbank-Übersicht

### Tabellen
```
alerts_sent | 16 kB
api_keys | 144 kB
api_keys_masked | 0 bytes
audit_log | 64 kB
catalog_templates | 48 kB
crm_push_log | 80 kB
customer_crm_settings | 48 kB
customer_lead_scores | 192 kB
customer_notifications | 48 kB
dsar_requests | 16 kB
incidents | 16 kB
ki_knowledge | 96 kB
lead_analyses | 168 kB
leads | 6024 kB
notification_logs | 48 kB
runs | 72 kB
score_config | 64 kB
source_errors | 32 kB
stripe_events | 24 kB
```

### Leads-Statistik
```
Gesamt:     2472
Aktiv:      2472
Letzte 24h: N/A
Quellen:    dtvp: 979
service_bund_rss: 820
vergabe_nrw: 416
ted: 245
db_bieterportal: 10
webhook: 2
```

### Score-Verteilung
```

```

### Catalog Templates
```
beratung-umwelt — Umwelt- & Energieberatung
catering-events — Catering & Eventservice
elektro-berlin — Elektroinstallation Berlin/Brandenburg
facility-bayern — Reinigung & Facility Management
gruenpflege-nrw — Gartenbau & Grünpflege NRW
ingenieur-bau — Ingenieurbüro Bau & Planung
it-nrw — IT-Systemhaus NRW
medizintechnik — Medizintechnik & Labor
security-de — Security & Wachschutz
transport-logistik — Transport & Logistik
```

### CRM-Verbindungen
```

```

---

## 5. Backend API-Endpoints

```
delete("/admin/ki/knowledge")
delete("/api/v1/leads/duplicates")
get("/admin/api-keys")
get("/admin/dashboard")
get("/api/v1/analyse/lead/{lead_id}/history")
get("/api/v1/analyse/trends")
get("/api/v1/backup/status")
get("/api/v1/catalog/templates")
get("/api/v1/collector/logs")
get("/api/v1/collector/status")
get("/api/v1/crm/status/{customer_id}")
get("/api/v1/digest/preview")
get("/api/v1/errors")
get("/api/v1/errors/summary")
get("/api/v1/ki/knowledge")
get("/api/v1/ki/knowledge/stats")
get("/api/v1/leads")
get("/api/v1/leads/export.csv")
get("/api/v1/leads/{lead_id}")
get("/api/v1/me")
get("/api/v1/notifications/settings")
get("/api/v1/openclaw/health")
get("/api/v1/runs")
get("/api/v1/score-config")
get("/api/v1/sources/health")
get("/api/v1/stats")
get("/api/v1/stats/kpis")
get("/api/v1/stats/usage")
get("/healthz")
patch("/api/v1/leads/{lead_id}/favorite")
patch("/api/v1/leads/{lead_id}/status")
post("/admin/api-keys/{customer_id}/deactivate")
post("/admin/ki/learn")
post("/admin/reset-all")
post("/api/v1/analyse/lead/{lead_id}")
post("/api/v1/analyse/portfolio")
post("/api/v1/analyse/v2/{lead_id}")
post("/api/v1/collector/start")
post("/api/v1/collector/stop")
post("/api/v1/crm/connect")
post("/api/v1/crm/test-push")
post("/api/v1/errors/{error_id}/resolve")
post("/api/v1/keys/revoke")
post("/api/v1/keys/rotate")
post("/api/v1/leads/deduplicate")
post("/api/v1/leads/{lead_id}/enrich")
post("/api/v1/onboarding/complete")
post("/api/v1/score-config")
post("/api/v1/score-config/apply")
post("/api/v1/score-config/preview")
post("/api/v1/scoring/apply/{customer_id}")
post("/api/v1/webhook/leads")
post("/webhooks/stripe")
put("/api/v1/notifications/settings")
```

---

## 6. Aktuelle Migrationen

```
003_score_config.sql
004_leads_status.sql
005_lead_analyses.sql
006_score_v2.sql
007_bulk_score_apply_optimized.sql
008_notification_tables.sql
009_leads_customer_id.sql
010_buyer_bonuses.sql
011_buyer_enrichment.sql
012_favorites.sql
013_scoring_v3_and_catalog.sql
014_analyse_v2_2.sql
015_crm_automation.sql
016_ki_knowledge.sql
```

---

## 7. Umgebungsvariablen (Keys maskiert)

```
API_KEY_PEPPER=...
CRM_ENCRYPTION_KEY=***MASKED***
CRM_SECRET_KEY=***MASKED***
DEEPSEEK_API_KEY=***MASKED***
HANDELSREGISTER_API_KEY=***MASKED***
NOTIFICATION_EMAIL=
POSTGRES_PASSWORD=***MASKED***
R2_ACCESS_KEY_ID=813e392b467706d66993365bf0ec2ba8
R2_ACCOUNT_ID=1b035cc55832bf45c24a0aa49b05c254
R2_BUCKET=daas
R2_SECRET_ACCESS_KEY=***MASKED***
RESEND_API_KEY=***MASKED***
```

---

## 8. Cron-Jobs / Timer

```
0 * * * * /home/etk/openclaw/scripts/memory-sync.sh >> /home/etk/openclaw/logs/memory-sync.log 2>&1
*/5 * * * * /home/etk/openclaw/scripts/health-monitor.sh >> /home/etk/openclaw/logs/health-monitor.log 2>&1
0 7 * * * /home/etk/openclaw/scripts/daily-report.sh >> /home/etk/openclaw/logs/health-monitor.log 2>&1
# DaaS: Daily Scoring v3 (05:00)
0 5 * * * /home/etk/daas-project/ops/scripts/run_scoring.sh >> /home/etk/daas-project/logs/scoring.log 2>&1
# DaaS: Daily Digest v2.2 (07:00 Mo-Fr)
0 7 * * 1-5 /home/etk/daas-project/ops/scripts/run_digest_v2.sh >> /home/etk/daas-project/logs/digest.log 2>&1
# DaaS: CRM-Push-Retry (alle 15min)
*/15 * * * * /home/etk/daas-project/ops/scripts/run_crm_retry.sh >> /home/etk/daas-project/logs/crm_retry.log 2>&1
# DaaS: R2 Backup (00:30)
30 0 * * * /home/etk/daas-project/ops/scripts/backup_to_r2.sh >> /home/etk/daas-project/logs/backup.log 2>&1

Keine systemd Timer für DaaS
```

---

## 9. Letzte 15 Git-Commits

```
de4adc2 feat: Admin Reset + KI-Wissensdatenbank (selbstlernendes System)
f49ee61 feat: DTVP-Collector (Deutsches Vergabeportal) + OpenClaw→DaaS Branding
60c6e3a v2.1: Favoriten-Kanban, Design-Optimierung, Playwright Web-Scraper
2006d3c Phase 6: Dokumentation aktualisiert (PROGRESS, README, ZUSAMMENFASSUNG, SOLL_IST)
4c46d41 Phase 5: Testing bestanden — Fixes für DeepSeek Token-Limit + CRM memoryview
934faec Phase 4: Automatisierung — Scoring, Digest v2.2, CRM-Retry, Cron-Jobs
ab3317a Phase 3: Frontend Wizard + CRM + Lead-Detail v2.2 + Sidebar
fac6b89 Phase 2: Backend Scoring v3 + Analyse v2.2 + CRM-Service + Endpoints
a6029a5 Phase 1: DB-Migrationen 013-015 (Scoring v3, Analyse v2.2, CRM)
3fd771a fix: Cronjob-Fixes + System-Status Snapshot
be6ced4 fix: TED API v3 Felder, nicht erreichbare Quellen deaktiviert
00eff7a feat: Favoriten, Duplikate löschen, Parser-Fix, Score-Optimierung
e217e2b feat: Prio-5 komplett – Kanban, Notifications, Enrichment, Auto-Analyse, Trends
7e331f3 fix: R2 Backup-Script nutzt korrekten Bucket-Namen aus .env
29acae0 feat: 100% Soll-Zustand – Buyer Bonus, 4 Parser, API-Version, Backup-Status, rclone
```

---

## 10. Letzte Änderungen (Dateien der letzten 48h)

```
Mär 2 08:33 ./dsgvo_package/src/ausschreibungen/collectors/dtvp.py
Mär 2 08:12 ./backend/app/ki_learner.py
Mär 2 08:11 ./backend/app/auth.py
Mär 2 07:59 ./frontend/src/App.js
Mär 2 07:57 ./frontend/src/api.js
Mär 2 07:57 ./backend/app/main.py
Mär 2 07:53 ./backend/migrations/016_ki_knowledge.sql
Mär 2 07:45 ./dsgvo_package/src/ausschreibungen/orchestrator.py
Mär 2 07:45 ./dsgvo_package/src/ausschreibungen/config.py
Mär 2 07:22 ./dsgvo_package/src/ausschreibungen/collectors/db_bieterportal.py
Mär 2 07:00 ./dsgvo_package/src/ausschreibungen/collectors/web_scraper.py
Mär 2 07:00 ./dsgvo_package/src/ausschreibungen/collectors/evergabe_rss.py
Mär 2 06:59 ./dsgvo_package/src/ausschreibungen/playwright_browser.py
Mär 2 05:51 ./backend/tasks/daily_digest_v2.py
Mär 2 05:51 ./backend/tasks/daily_scoring.py
Mär 2 05:51 ./backend/tasks/run_tasks.py
Mär 2 05:51 ./backend/migrations/015_crm_automation.sql
Mär 2 05:51 ./backend/tasks/crm_retry.py
Mär 2 05:51 ./backend/tasks/__init__.py
Mär 2 05:51 ./backend/app/settings.py
```

---

## 11. Bekannte Issues / TODOs

Keine TODOs gefunden

---

## 12. Disk & System

```
Disk:   37G/117G (34% used)
Memory: 3,2Gi/19Gi
Load:    0,29, 0,24, 0,20
Docker: TYPE            TOTAL     ACTIVE    SIZE      RECLAIMABLE
Images          10        6         18.17GB   15.84GB (87%)
Containers      8         8         24.19MB   0B (0%)
Local Volumes   5         3         188.9MB   67.94MB (35%)
Build Cache     150       0         13.67GB   7.837GB
```

---

## 13. Anweisungen für KI-Assistenten

Wenn du Code für dieses Projekt schreibst, beachte:
- **DB-Typen:** customer_id = TEXT, lead_id = UUID (nicht INTEGER!)
- **Framework:** FastAPI + asyncpg
- **Auth:** API-Key via X-API-Key Header (SHA-256 + Pepper)
- **Projektverzeichnis:** /home/etk/daas-project
- **Docker:** docker compose (v2, NICHT docker-compose)
- **Branch:** Arbeite auf feature-Branches, merge nach main
- **Stil:** Deutsche Kommentare, englische Variablennamen
- **Tests:** pytest im dsgvo_package, manuelle curl-Tests für API

