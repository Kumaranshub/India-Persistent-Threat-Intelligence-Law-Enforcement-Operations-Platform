```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                                                                                 │
│   ██████╗ ████████╗██╗██╗      ██████╗ ██████╗                                  │
│   ██╔══██╗╚══██╔══╝██║██║     ██╔═══██╗██╔══██╗                                 │
│   ██████╔╝   ██║   ██║██║     ██║   ██║██████╔╝                                 │
│   ██╔═══╝    ██║   ██║██║     ██║   ██║██╔═══╝                                  │
│   ██║        ██║   ██║███████╗╚██████╔╝██║                                      │
│   ╚═╝        ╚═╝   ╚═╝╚══════╝ ╚═════╝ ╚═╝                                      │
│                                                                                 │
│        INDIA PERSISTENT THREAT INTELLIGENCE &                                   │
│        LAW ENFORCEMENT OPERATIONS PLATFORM                                      │
│                                                                                 │
│                                                                                 │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

```
  SECTION 01 — MISSION BRIEF
```

Multi-source, real-time criminal intelligence fusion platform for Indian law enforcement.
Integrates **CCTNS, NATGRID, VAHAN, Aadhaar, CDR, and FIU** data into a live entity graph
with ML-powered risk scoring, geospatial tracking, and automated threat alerting.

Built entirely on-premise. Zero external cloud dependency. Deployable on a single server
or a hardened air-gapped rack. Designed to outperform commercial alternatives at a
fraction of the cost — purpose-built for India's data sources and legal framework.

---

```
  SECTION 02 — SYSTEM STATUS
```

![Build](https://img.shields.io/github/actions/workflow/status/your-org/ptilop/ci.yml?style=flat-square&label=BUILD&color=355e3b)
![Python](https://img.shields.io/badge/PYTHON-3.11+-355e3b?style=flat-square)
![FastAPI](https://img.shields.io/badge/FASTAPI-0.110-355e3b?style=flat-square)
![React](https://img.shields.io/badge/REACT-18-355e3b?style=flat-square)
![Neo4j](https://img.shields.io/badge/NEO4J-5.x-355e3b?style=flat-square)
![Kafka](https://img.shields.io/badge/KAFKA-3.6-355e3b?style=flat-square)
![License](https://img.shields.io/badge/LICENSE-RESTRICTED-8b0000?style=flat-square)
![Clearance](https://img.shields.io/badge/CLEARANCE-SECRET%2B-8b0000?style=flat-square)

---

```
  SECTION 03 — OPERATIONAL CAPABILITIES
```

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  CAPABILITY                        DESCRIPTION                              │
├─────────────────────────────────────────────────────────────────────────────┤
│  ► LIVE ENTITY GRAPH               Dynamic criminal network in real time.   │
│                                    Person — Phone — Vehicle — Location      │
│                                    linked via Neo4j graph engine.           │
├─────────────────────────────────────────────────────────────────────────────┤
│  ► PATTERN-OF-LIFE ANALYSIS        Full activity timeline per entity.       │
│                                    Movement, communications, finance,       │
│                                    associations — all reconstructed.        │
├─────────────────────────────────────────────────────────────────────────────┤
│  ► ML RISK SCORING ENGINE          0–100 threat score per entity.           │
│                                    Gradient-boosted model on 34 features.   │
│                                    Updates automatically on new data.       │
├─────────────────────────────────────────────────────────────────────────────┤
│  ► ENTITY RESOLUTION               Same person. Different spellings.        │
│                                    Matches across CCTNS, VAHAN, FIU, CDR   │
│                                    using Jaro-Winkler + phonetic keys.      │
├─────────────────────────────────────────────────────────────────────────────┤
│  ► GEOINT LAYER                    Real-time geospatial heatmaps.           │
│                                    ANPR feeds, border crossings,            │
│                                    movement anomaly detection.              │
├─────────────────────────────────────────────────────────────────────────────┤
│  ► SIGINT PROCESSING               CDR call graph analysis.                 │
│                                    Encrypted channel metadata.              │
│                                    Communication burst detection.           │
├─────────────────────────────────────────────────────────────────────────────┤
│  ► AUTOMATED ALERT ENGINE          Rule-based + ML anomaly alerts.          │
│                                    Priority queue with severity triage.     │
│                                    WebSocket delivery — sub-second.         │
├─────────────────────────────────────────────────────────────────────────────┤
│  ► CASE MANAGEMENT                 Templated investigation workflows.       │
│                                    Evidence chain, prosecution export.      │
│                                    Multi-officer collaboration.             │
├─────────────────────────────────────────────────────────────────────────────┤
│  ► IMMUTABLE AUDIT TRAIL           Every query. Every view. Every action.   │
│                                    SHA-256 hash-chained log entries.        │
│                                    7-year retention. DPDP Act 2023.         │
├─────────────────────────────────────────────────────────────────────────────┤
│  ► COMPARTMENTALIZED ACCESS        Clearance-level + operation-specific     │
│                                    data isolation. Officer sees only        │
│                                    what their mission requires.             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

```
  SECTION 04 — SYSTEMS ARCHITECTURE
```

```
  ╔══════════════════════════════════════════════════════════════════════════╗
  ║                        [ DATA SOURCES — LAYER 0 ]                       ║
  ║  CCTNS │ NATGRID │ VAHAN/SARATHI │ UIDAI │ FIU-IND │ CDR │ ANPR │ OSINT ║
  ╚═══════════════════════════════╤══════════════════════════════════════════╝
                                  │ Lawful intercept / API / batch ingest
  ╔═══════════════════════════════▼══════════════════════════════════════════╗
  ║                     [ INGESTION SERVICE — LAYER 1 ]                     ║
  ║          Source connectors · Normalisation · Deduplication              ║
  ║                        Apache Kafka producers                           ║
  ╚═══╤═══════════════════════════╤═══════════════════════════╤═════════════╝
      │                           │                           │
  ╔═══▼═══════╗           ╔═══════▼═══════╗           ╔══════▼══════════╗
  ║  INTEL    ║           ║   GRAPH       ║           ║  ALERT          ║
  ║  ENGINE   ║           ║   SERVICE     ║           ║  ENGINE         ║
  ║           ║           ║               ║           ║                 ║
  ║ Risk Score║           ║ Neo4j 5.x     ║           ║ Rule + ML       ║
  ║ Entity Res║           ║ GDS Algorithms║           ║ Flink CEP       ║
  ║ NLP / OCR ║           ║ Ontology Mgmt ║           ║ WebSocket Push  ║
  ╚═══╤═══════╝           ╚═══════╤═══════╝           ╚══════╤══════════╝
      │                           │                           │
  ╔═══▼═══════════════════════════▼═══════════════════════════▼═════════════╗
  ║                       [ CORE API — LAYER 3 ]                            ║
  ║     FastAPI · PostgreSQL 16 · Redis 7 · Elasticsearch 8 · MinIO        ║
  ╚═══════════════════════════════╤══════════════════════════════════════════╝
                                  │
  ╔═══════════════════════════════▼══════════════════════════════════════════╗
  ║                   [ API GATEWAY + AUTH — LAYER 4 ]                      ║
  ║              Traefik · Keycloak · RBAC · MFA · Rate Limiting            ║
  ╚═══════════════════════════════╤══════════════════════════════════════════╝
                                  │
  ╔═══════════════════════════════▼══════════════════════════════════════════╗
  ║                    [ OPERATIONS UI — LAYER 5 ]                          ║
  ║      React 18 · D3.js Graph · Deck.gl Maps · WebSocket Alerts           ║
  ╚══════════════════════════════════════════════════════════════════════════╝
```

---

```
  SECTION 05 — INTEGRATED DATA SOURCES
```

```
  ┌──────────────────┬──────────────────────────────────────┬─────────────┐
  │  SOURCE          │  DATA PROVIDED                       │  AUTHORITY  │
  ├──────────────────┼──────────────────────────────────────┼─────────────┤
  │  CCTNS           │  FIRs, charge sheets, criminals,     │  NCRB / MHA │
  │                  │  arrests, convictions — all states   │             │
  ├──────────────────┼──────────────────────────────────────┼─────────────┤
  │  NATGRID         │  Cross-agency intelligence fusion,   │  MHA        │
  │                  │  21 source databases in one feed     │             │
  ├──────────────────┼──────────────────────────────────────┼─────────────┤
  │  UIDAI / AADHAAR │  Identity verification, biometric    │  UIDAI      │
  │                  │  match, eKYC resolution              │             │
  ├──────────────────┼──────────────────────────────────────┼─────────────┤
  │  VAHAN / SARATHI │  Vehicle registration, ownership     │  MoRTH      │
  │                  │  history, driving licences           │             │
  ├──────────────────┼──────────────────────────────────────┼─────────────┤
  │  FIU-IND         │  Suspicious transaction reports,     │  FinMin     │
  │                  │  hawala flags, STRs, CTRs            │             │
  ├──────────────────┼──────────────────────────────────────┼─────────────┤
  │  TELECOM CDR     │  Call detail records, tower data,    │  DoT / LEA  │
  │                  │  IMEI tracking (lawful intercept)    │             │
  ├──────────────────┼──────────────────────────────────────┼─────────────┤
  │  ANPR FEEDS      │  Automatic number plate recognition, │  State PD   │
  │                  │  highway toll data, border crossings │             │
  ├──────────────────┼──────────────────────────────────────┼─────────────┤
  │  eCOURTS         │  Case status, warrants, bail orders, │  MoLJ       │
  │                  │  judgements                          │             │
  ├──────────────────┼──────────────────────────────────────┼─────────────┤
  │  MCA21 / GSTN    │  Business entities, directorships,   │  MCA / CBIC │
  │                  │  shell company detection             │             │
  ├──────────────────┼──────────────────────────────────────┼─────────────┤
  │  IB / RAW FEEDS  │  HUMINT reports, signals             │  IB / R&AW  │
  │                  │  intelligence, border intel          │             │
  └──────────────────┴──────────────────────────────────────┴─────────────┘
```

---

```
  SECTION 06 — TECHNOLOGY STACK
```

```
  BACKEND SERVICES
  ├── Core API          FastAPI 0.110 (Python 3.11) · async · OpenAPI docs
  ├── Graph Service     Neo4j 5.x + GDS · Cypher · PageRank · Louvain
  ├── Intel Engine      XGBoost · PyTorch · spaCy · IndicNLP · scikit-learn
  ├── Alert Engine      Apache Flink · custom rule DSL · WebSocket delivery
  ├── Ingestion Service Apache Kafka · 10 source connectors · normalisation
  ├── Audit Service     asyncpg · SHA-256 hash chaining · WORM archival
  └── Auth Service      Keycloak 24 · OAuth2 · RBAC · MFA · clearance levels

  DATA LAYER
  ├── PostgreSQL 16     Relational data · PostGIS · pg_trgm · append-only audit
  ├── Neo4j 5.x         Entity graph · GDS algorithms · Bolt protocol
  ├── Elasticsearch 8   Full-text + vector search · index per source
  ├── Redis 7           Cache · pub/sub · session · rate limiting
  ├── Apache Kafka      Event streaming · 20+ topics · 7-day retention
  └── MinIO             Evidence files · reports · WORM buckets

  FRONTEND
  ├── React 18          TypeScript · Redux Toolkit · React Router
  ├── D3.js             Force-directed entity graph · custom physics
  ├── Deck.gl           WebGL geospatial layer · heatmaps · ANPR tracks
  ├── MapLibre GL       Base map tiles · offline-capable
  └── WebSocket         Real-time alert feed · sub-second delivery

  INFRASTRUCTURE
  ├── Docker Compose    Full local dev stack in one command
  ├── Kubernetes        Helm chart · production deployment
  ├── Terraform         IaC for NIC/MeitY cloud · on-premise bare metal
  ├── GitHub Actions    CI/CD · SAST · container scanning · auto-deploy
  ├── Prometheus        Metrics · custom dashboards
  ├── Grafana           Operations dashboards · SLA tracking
  └── HashiCorp Vault   Secrets management · no keys in git. Ever.
```

---

```
  SECTION 07 — FIELD DEPLOYMENT
```

```
  MINIMUM FIELD HARDWARE (development / staging)
  ┌──────────────────────────────────────────────────────┐
  │  RAM      8 GB minimum · 16 GB recommended           │
  │  STORAGE  50 GB free minimum                         │
  │  OS       Ubuntu 22.04 LTS / WSL2 / macOS 13+        │
  │  TOOLS    Docker 24.x · Docker Compose 2.x           │
  │           Python 3.11+ · Node.js 20+                 │
  └──────────────────────────────────────────────────────┘

  PRODUCTION DEPLOYMENT OPTIONS
  ┌──────────────────────────────────────────────────────┐
  │  [A] NIC CLOUD (MeitY empanelled)                    │
  │      Standard cloud deployment via Kubernetes +      │
  │      Helm. Meets data residency requirements.        │
  │                                                      │
  │  [B] ON-PREMISE SERVER RACK                          │
  │      Air-gap capable. Full offline operation.        │
  │      No external network dependency.                 │
  │                                                      │
  │  [C] STATE DATA CENTRE                               │
  │      Per-state deployment with central federation.   │
  │      Compartmentalized by state + clearance.         │
  └──────────────────────────────────────────────────────┘
```

---

```
  SECTION 08 — QUICK START — FIELD SETUP
```

```bash
# ── STEP 01 · ACQUIRE ────────────────────────────────────────────────────────
git clone https://github.com/your-org/ptilop.git
cd ptilop

# ── STEP 02 · CONFIGURE ──────────────────────────────────────────────────────
cp config/secrets-template/.env.example .env
# Edit .env — set database passwords, API keys, secret key

# ── STEP 03 · DEPLOY FULL STACK ──────────────────────────────────────────────
docker compose -f infra/docker/docker-compose.dev.yml up -d

# ── STEP 04 · INITIALISE DATABASE ────────────────────────────────────────────
python scripts/migration/run_migrations.py

# ── STEP 05 · LOAD DEMO DATA ─────────────────────────────────────────────────
python scripts/seed/seed_demo.py

# ── STEP 06 · LAUNCH UI ──────────────────────────────────────────────────────
cd frontend && npm install && npm run dev

# ── STEP 07 · ACCESS ─────────────────────────────────────────────────────────
# Operations UI  →  http://localhost:3000
# API Docs       →  http://localhost:8000/docs
# Neo4j Browser  →  http://localhost:7474
# Kafka Monitor  →  http://localhost:8080
# Grafana        →  http://localhost:3001
# Keycloak Admin →  http://localhost:8180
```

---

```
  SECTION 09 — REPOSITORY STRUCTURE
```

```
  ptilop/
  │
  ├── .github/
  │   └── workflows/          CI/CD pipelines — build, test, scan, deploy
  │
  ├── docs/
  │   ├── architecture/       System design documents, ADRs
  │   ├── api/                API reference, Postman collections
  │   ├── deployment/         Runbooks, hardening guides
  │   └── threat-model/       STRIDE threat model, security review
  │
  ├── infra/
  │   ├── docker/             Docker Compose — dev, staging, production
  │   ├── k8s/                Kubernetes manifests + Helm chart
  │   └── terraform/          IaC — NIC cloud, on-premise
  │
  ├── services/
  │   ├── api-gateway/        Traefik config, rate limiting, TLS
  │   ├── core-api/           FastAPI — entities, cases, alerts, search
  │   ├── ingestion-service/  Source connectors — CCTNS, NATGRID, CDR...
  │   ├── intel-engine/       ML — risk scoring, entity resolution, NLP
  │   ├── alert-engine/       Rule + anomaly alerting, Flink CEP
  │   ├── graph-service/      Neo4j ontology, graph algorithms
  │   ├── audit-service/      Immutable audit trail, hash chain
  │   └── auth-service/       Keycloak integration, RBAC, clearances
  │
  ├── frontend/
  │   └── src/
  │       ├── components/     Graph, Map, Cases, Entities, Alerts, Intercepts
  │       ├── pages/          Route-level page components
  │       ├── store/          Redux slices — auth, entities, cases, alerts
  │       ├── services/       Typed API client layer
  │       ├── hooks/          WebSocket, real-time subscriptions
  │       └── types/          TypeScript interfaces
  │
  ├── scripts/
  │   ├── setup/              Database init, schema creation
  │   ├── migration/          Alembic migration runner
  │   ├── seed/               Demo data seeder
  │   └── deploy/             Deployment automation
  │
  └── config/
      ├── environments/       Per-environment config files
      └── secrets-template/   .env templates — never commit real values
```

---

```
  SECTION 10 — OPERATIONAL ROADMAP
```

```
  PHASE I   — FOUNDATION                                    
  ──────────────────────────────────────────────────────────────────────
  [✓] Core API — entities, cases, alerts, intercepts
  [✓] Neo4j graph service + ontology
  [✓] PostgreSQL schema + audit trail
  [✓] Docker Compose dev stack
  [✓] GitHub Actions CI/CD pipeline
  [ ] Keycloak RBAC + clearance levels
  [ ] Elasticsearch full-text search

  PHASE II  — DATA CONNECTORS                               
  ──────────────────────────────────────────────────────────────────────
  [ ] CCTNS connector (FIRs, persons, arrests)
  [ ] VAHAN/SARATHI connector (vehicles, licences)
  [ ] CDR ingestor (telecom call records)
  [ ] FIU-IND transaction feed
  [ ] ANPR feed processor

  PHASE III — INTELLIGENCE ENGINE                           
  ──────────────────────────────────────────────────────────────────────
  [ ] ML risk scoring model (XGBoost, 34 features)
  [ ] Entity resolution engine (Jaro-Winkler + ML)
  [ ] Community detection (Louvain algorithm)
  [ ] Anomaly detection (isolation forest)
  [ ] Hindi/Urdu/Tamil NLP (IndicNLP + spaCy)

  PHASE IV  — ADVANCED OPERATIONS                           
  ──────────────────────────────────────────────────────────────────────
  [ ] GEOINT layer (Deck.gl + PostGIS)
  [ ] Pattern-of-life reconstruction UI
  [ ] Real-time alert engine (Apache Flink)
  [ ] Biometric photo search
  [ ] Air-gap hardened deployment package

  PHASE V   — SCALE & FEDERATION                           
  ──────────────────────────────────────────────────────────────────────
  [ ] Multi-state federated deployment
  [ ] Cross-state intelligence sharing (compartmentalized)
  [ ] Mobile operations app (React Native)
  [ ] Predictive threat modelling
```

---

```
  SECTION 11 — COMPLIANCE & LEGAL FRAMEWORK
```

```
  ┌──────────────────────────────────────────────────────────────────────┐
  │  DPDP ACT 2023       Digital Personal Data Protection Act.          │
  │                      Purpose limitation, consent framework,          │
  │                      data fiduciary obligations enforced.            │
  ├──────────────────────────────────────────────────────────────────────┤
  │  IT ACT 2000         Section 69 lawful interception provisions.     │
  │  (AMENDED)           Authorised agency access only.                 │
  ├──────────────────────────────────────────────────────────────────────┤
  │  CrPC S.91/92        Document and record seizure framework.         │
  │                      Evidence chain maintained in audit trail.      │
  ├──────────────────────────────────────────────────────────────────────┤
  │  AUDIT RETENTION     7 years — immutable, hash-chained log.        │
  │                      Cannot be deleted or modified via any API.     │
  ├──────────────────────────────────────────────────────────────────────┤
  │  ENCRYPTION          AES-256 at rest. TLS 1.3 in transit.          │
  │                      Aadhaar stored as SHA-256 hash only.           │
  ├──────────────────────────────────────────────────────────────────────┤
  │  AIR-GAP SUPPORT     Fully operational with zero external network.  │
  │                      No telemetry. No cloud callbacks.              │
  └──────────────────────────────────────────────────────────────────────┘
```

---

```
  SECTION 12 — SECURITY DIRECTIVES
```

> **DIRECTIVE 01** — Do not commit credentials, API keys, or real operational data to this repository under any circumstances.

> **DIRECTIVE 02** — MFA is mandatory for all operator accounts. No exceptions. No bypass.

> **DIRECTIVE 03** — All production deployments require a penetration test report before go-live.

> **DIRECTIVE 04** — Secrets are managed via HashiCorp Vault. `.env` files are for local development only.

> **DIRECTIVE 05** — All data handling must comply with the DPDP Act 2023 and applicable MHA operational guidelines.

> **DIRECTIVE 06** — This system processes intelligence-grade data. Access is restricted to authorised law enforcement and government agency personnel only.

---

```
  SECTION 13 — CONTRIBUTING
```

All contributions require:

1. Passing CI — all tests green, no lint errors, no secrets detected
2. Code review by at least one other authorised contributor
3. Security review for any changes touching auth, audit, or data access layers
4. ADR (Architecture Decision Record) for any significant architectural change
5. No breaking changes to the audit trail schema without migration path

Branch strategy: `main` → production · `develop` → staging · `feature/*` → development

---

```
  SECTION 14 — LICENCE
```

```
  RESTRICTED — NOT FOR PUBLIC DISTRIBUTION

  This software and all associated documentation is the property of the
  India Persistent Threat Intelligence & Law Enforcement Operations Platform
  project. Access, use, reproduction, or distribution is strictly limited
  to authorised Indian government and law enforcement agencies.

  Unauthorised access or distribution is a criminal offence under the
  Information Technology Act 2000 and applicable Indian law.

  © 2026 — All Rights Reserved
```
