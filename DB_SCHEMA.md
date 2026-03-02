# OpenClaw DaaS — Datenbank-Schema (Auto-generiert)
> Letzte Aktualisierung: 2026-03-02 18:04 UTC

## alerts_sent
```
id | uuid | NO | gen_random_uuid()
lead_id | uuid | YES | 
alert_type | text | NO | 
recipient | text | YES | 
channel | text | NO | 
sent_at | timestamp with time zone | NO | now()
status | text | NO | 'sent'::text
payload | jsonb | YES | '{}'::jsonb
```

## api_keys
```
id | uuid | NO | gen_random_uuid()
api_key_hash | bytea | NO | 
api_key_prefix | text | NO | 
api_key_last4 | text | NO | 
customer_id | text | NO | 
customer_email | text | NO | 
subscription_id | text | YES | 
plan | text | YES | 
active | boolean | YES | true
expires_at | timestamp with time zone | YES | 
last_used_at | timestamp with time zone | YES | 
created_at | timestamp with time zone | YES | now()
updated_at | timestamp with time zone | YES | now()
```

## api_keys_masked
```
id | uuid | YES | 
customer_id | text | YES | 
customer_email | text | YES | 
subscription_id | text | YES | 
plan | text | YES | 
active | boolean | YES | 
expires_at | timestamp with time zone | YES | 
last_used_at | timestamp with time zone | YES | 
created_at | timestamp with time zone | YES | 
updated_at | timestamp with time zone | YES | 
api_key_masked | text | YES | 
```

## audit_log
```
id | uuid | NO | gen_random_uuid()
event_type | text | NO | 
actor | text | YES | 
target_type | text | YES | 
target_id | text | YES | 
details | jsonb | YES | '{}'::jsonb
created_at | timestamp with time zone | NO | now()
```

## catalog_templates
```
id | integer | NO | nextval('catalog_templates_id_seq'::regclass)
slug | character varying | NO | 
name | character varying | NO | 
category | character varying | NO | 
keywords | jsonb | NO | '[]'::jsonb
regions | jsonb | NO | '[]'::jsonb
cpv_filters | jsonb | NO | '[]'::jsonb
weights | jsonb | NO | '{"cpv": 15, "value": 5, "region": 20, "urgency": 15, "keywords": 45}'::jsonb
synonyms | jsonb | NO | '{}'::jsonb
min_score | integer | NO | 45
description | text | YES | 
is_active | boolean | NO | true
created_at | timestamp with time zone | NO | now()
```

## crm_push_log
```
id | integer | NO | nextval('crm_push_log_id_seq'::regclass)
customer_id | integer | NO | 
lead_id | uuid | NO | 
crm_type | character varying | NO | 
crm_deal_id | text | YES | 
status | character varying | NO | 'pending'::character varying
request_payload | jsonb | YES | 
response_payload | jsonb | YES | 
error_message | text | YES | 
retry_count | integer | NO | 0
pushed_at | timestamp with time zone | NO | now()
```

## customer_crm_settings
```
id | integer | NO | nextval('customer_crm_settings_id_seq'::regclass)
customer_id | integer | NO | 
crm_type | character varying | NO | 
encrypted_secrets | bytea | YES | 
base_url | text | YES | 
pipeline_id | text | YES | 
stage_id | text | YES | 
owner_id | text | YES | 
push_rules | jsonb | NO | '{"min_score": 45, "min_value": 0, "only_class": null}'::jsonb
push_next_actions | boolean | NO | true
active | boolean | NO | true
last_sync_at | timestamp with time zone | YES | 
sync_count | integer | NO | 0
error_count | integer | NO | 0
last_error | text | YES | 
created_at | timestamp with time zone | NO | now()
updated_at | timestamp with time zone | NO | now()
```

## customer_lead_scores
```
id | integer | NO | nextval('customer_lead_scores_id_seq'::regclass)
customer_id | text | NO | 
lead_id | uuid | NO | 
score | integer | NO | 0
score_class | character | NO | 'C'::bpchar
explanation | jsonb | YES | 
scored_at | timestamp with time zone | NO | now()
```

## customer_notifications
```
id | uuid | NO | gen_random_uuid()
customer_id | text | NO | 
notification_email | text | NO | 
webhook_url | text | YES | 
send_daily_digest | boolean | NO | false
plan_tier | text | NO | 'radar'::text
created_at | timestamp with time zone | NO | now()
updated_at | timestamp with time zone | NO | now()
```

## dsar_requests
```
id | uuid | NO | gen_random_uuid()
requester_email | text | YES | 
requester_name | text | YES | 
request_type | text | NO | 
status | text | NO | 'open'::text
received_at | timestamp with time zone | NO | now()
due_at | timestamp with time zone | YES | 
completed_at | timestamp with time zone | YES | 
notes | text | YES | 
meta | jsonb | YES | '{}'::jsonb
```

## incidents
```
id | uuid | NO | gen_random_uuid()
severity | text | NO | 
title | text | NO | 
status | text | NO | 'open'::text
detected_at | timestamp with time zone | NO | now()
contained_at | timestamp with time zone | YES | 
closed_at | timestamp with time zone | YES | 
privacy_risk | boolean | YES | 
authority_notified | boolean | YES | false
authority_notified_at | timestamp with time zone | YES | 
affected_count_estimate | integer | YES | 
summary | text | YES | 
details | jsonb | YES | '{}'::jsonb
```

## ki_knowledge
```
id | uuid | NO | gen_random_uuid()
category | text | NO | 
entity_name | text | NO | 
key | text | NO | 
value | jsonb | NO | '{}'::jsonb
confidence | double precision | YES | 0.5
source_leads | ARRAY | YES | '{}'::uuid[]
first_seen_at | timestamp with time zone | YES | now()
updated_at | timestamp with time zone | YES | now()
```

## lead_analyses
```
id | uuid | NO | gen_random_uuid()
lead_id | uuid | YES | 
analysis_type | text | NO | 'single'::text
model | text | NO | 'deepseek-chat'::text
prompt_tokens | integer | YES | 
completion_tokens | integer | YES | 
result_text | text | NO | 
created_at | timestamp with time zone | NO | now()
structured_data | jsonb | YES | 
win_probability | integer | YES | 
estimated_value | numeric | YES | 
buyer_type | text | YES | 
next_actions_summary | jsonb | YES | 
complexity | text | YES | 
version | integer | NO | 2
crm_pushed_at | timestamp with time zone | YES | 
crm_deal_id | text | YES | 
```

## leads
```
id | uuid | NO | gen_random_uuid()
source | text | NO | 
source_notice_id | text | NO | 
source_hash | text | YES | 
title | text | NO | 
description | text | YES | 
publication_date | date | YES | 
deadline | timestamp with time zone | YES | 
cpv_codes | ARRAY | YES | ARRAY[]::text[]
buyer_name | text | YES | 
buyer_location | text | YES | 
region_norm | text | YES | 
country_code | text | YES | 
language_code | text | YES | 
url | text | NO | 
attachments | jsonb | YES | '[]'::jsonb
score | integer | YES | 0
score_class | text | YES | 'C'::text
score_explanation | jsonb | YES | '{}'::jsonb
tags | ARRAY | YES | ARRAY[]::text[]
is_active | boolean | YES | true
is_deleted | boolean | YES | false
first_seen_at | timestamp with time zone | NO | now()
last_seen_at | timestamp with time zone | NO | now()
collected_at | timestamp with time zone | NO | now()
normalized_at | timestamp with time zone | YES | 
raw_payload | jsonb | YES | '{}'::jsonb
created_by_run_id | uuid | YES | 
updated_by_run_id | uuid | YES | 
status | text | NO | 'new'::text
is_duplicate | boolean | NO | false
customer_id | text | YES | 
buyer_register_number | text | YES | 
buyer_register_court | text | YES | 
buyer_status | text | YES | 
buyer_enriched_at | timestamp with time zone | YES | 
is_favorite | boolean | NO | false
```

## notification_logs
```
id | uuid | NO | gen_random_uuid()
customer_id | text | NO | 
sent_at | timestamp with time zone | NO | now()
leads_count | integer | NO | 0
a_leads | integer | NO | 0
delivery_method | text | NO | 'email'::text
status | text | NO | 'sent'::text
error_message | text | YES | 
digest_date | date | NO | CURRENT_DATE
```

## runs
```
id | uuid | NO | gen_random_uuid()
run_type | text | NO | 
started_at | timestamp with time zone | NO | now()
finished_at | timestamp with time zone | YES | 
status | text | NO | 'running'::text
total_fetched | integer | YES | 0
total_normalized | integer | YES | 0
total_inserted | integer | YES | 0
total_updated | integer | YES | 0
total_duplicates | integer | YES | 0
total_errors | integer | YES | 0
notes | text | YES | 
meta | jsonb | YES | '{}'::jsonb
```

## score_config
```
id | integer | NO | nextval('score_config_id_seq'::regclass)
keywords | jsonb | NO | '[]'::jsonb
regions | jsonb | NO | '[]'::jsonb
cpv_filters | jsonb | NO | '[]'::jsonb
min_score | double precision | NO | 40.0
version | integer | NO | 1
created_at | timestamp with time zone | NO | now()
customer_id | text | YES | 
negative_keywords | jsonb | NO | '[]'::jsonb
urgency_enabled | boolean | NO | true
keyword_weights | jsonb | NO | '[]'::jsonb
buyer_bonuses | jsonb | YES | '[]'::jsonb
profile_name | character varying | YES | 'Standard'::character varying
template_id | integer | YES | 
weights | jsonb | YES | '{"cpv": 15, "value": 5, "region": 20, "urgency": 15, "keywords": 45}'::jsonb
synonyms | jsonb | YES | '{}'::jsonb
active | boolean | YES | true
```

## source_errors
```
id | uuid | NO | gen_random_uuid()
run_id | uuid | YES | 
source | text | NO | 
error_class | text | NO | 
error_message | text | NO | 
retryable | boolean | YES | false
retry_count | integer | YES | 0
payload | jsonb | YES | '{}'::jsonb
created_at | timestamp with time zone | NO | now()
```

## stripe_events
```
id | text | NO | 
type | text | NO | 
received_at | timestamp with time zone | NO | now()
payload | jsonb | YES | '{}'::jsonb
```

