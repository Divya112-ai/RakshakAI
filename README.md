<div align="center">

# 🚨 Rakshak AI

### Intelligent Emergency Response & Resource Coordination Platform

**Turning fragmented emergency reports into coordinated, real-time action.**

<br/>

![React](https://img.shields.io/badge/React_19-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express_4-000000?style=for-the-badge&logo=express&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB_Atlas-47A248?style=for-the-badge&logo=mongodb&logoColor=white)
![Socket.IO](https://img.shields.io/badge/Socket.IO-010101?style=for-the-badge&logo=socketdotio&logoColor=white)
![Gemini](https://img.shields.io/badge/Google_Gemini-8E75B2?style=for-the-badge&logo=googlegemini&logoColor=white)
![Leaflet](https://img.shields.io/badge/Leaflet-199900?style=for-the-badge&logo=leaflet&logoColor=white)

![Status](https://img.shields.io/badge/Core_modules-12%2F12_working-brightgreen?style=flat-square)
![Endpoints](https://img.shields.io/badge/REST_endpoints-29-blue?style=flat-square)
![Realtime](https://img.shields.io/badge/Socket.IO_events-9-orange?style=flat-square)
![Type](https://img.shields.io/badge/Hackathon_MVP-fully_working%2C_not_a_mockup-critical?style=flat-square)

<br/>

[**Overview**](#-at-a-glance) ·
[**Features**](#-key-features) ·
[**How it works**](#-how-it-works) ·
[**Architecture**](#-system-architecture) ·
[**AI & engines**](#-intelligence-engines) ·
[**Run it**](#-quick-start) ·
[**Demo script**](#-recommended-demo-flow)

</div>

---

## 🧭 At a Glance

> **Rakshak AI is a web-based emergency command platform.** It unifies citizen reports, classifies them with AI, detects duplicates, recommends the best responders, dispatches them, tracks progress live, and turns it all into analytics, end to end.

<table>
<tr>
<td width="50%" valign="top">

### ❌ The problem
Emergency information arrives from disconnected sources, so responders lose time:

- No single source of truth
- Duplicate reports of the same event
- Incorrect or delayed prioritisation
- Slow resource allocation
- Poor operator visibility
- Late escalation of life-critical incidents

</td>
<td width="50%" valign="top">

### ✅ What Rakshak AI does
One pipeline from first report to final analytics:

- **Citizens** report in seconds, with geolocation
- **AI** classifies type, severity, priority and actions
- **Scoring engine** flags duplicate reports
- **Ranking engine** recommends the best-fit responders
- **Operators** dispatch from one live command center
- **Responders** progress incidents from a mobile view
- **Cron** escalates unassigned P1 incidents automatically

</td>
</tr>
</table>

### 📊 The project in numbers

| 🧩 Core modules | 🌐 REST endpoints | ⚡ Live events | 🗄️ Collections | 🤖 AI fallback depth | 🚒 Seeded resources |
|:---:|:---:|:---:|:---:|:---:|:---:|
| **12 / 12** working | **29** | **9** Socket.IO types | **7** with `2dsphere` geo indexes | **4 models + rules** | **19** |

### 🏆 Where to look, by judging criterion

| Criterion | What to look at | Section |
|---|---|---|
| **Innovation** | Multi-signal duplicate detection, explainable ranking, AI with guaranteed fallback | [Intelligence engines](#-intelligence-engines) |
| **Technical depth** | Geospatial queries, server-enforced state machine, real-time event bus, cron escalation | [Architecture](#-system-architecture) |
| **Completeness** | Every stage from report to analytics runs on real services, not mock data | [Implementation status](#-implementation-status) |
| **User experience** | Three purpose-built views (citizen, operator, responder) with live updates | [How it works](#-how-it-works) |
| **Real-world impact** | Faster triage, fewer duplicate dispatches, guaranteed escalation | [Problem](#-at-a-glance) |
| **Reliability** | Classification never fails: AI falls back through 4 models, then rules | [AI pipeline](#1--ai-classification-pipeline) |
| **Honesty and scope** | Explicit list of limitations and roadmap | [Limitations](#-limitations) |

---

## 📑 Table of Contents

<details>
<summary><b>Click to expand</b></summary>

1. [At a Glance](#-at-a-glance)
2. [Our Solution](#-our-solution)
3. [Key Features](#-key-features)
4. [How It Works](#-how-it-works)
5. [System Architecture](#-system-architecture)
6. [Intelligence Engines](#-intelligence-engines)
7. [Tech Stack](#-tech-stack)
8. [API Reference](#-api-reference)
9. [Database Design](#-database-design)
10. [Security and Access Control](#-security-and-access-control)
11. [Project Structure](#-project-structure)
12. [Quick Start](#-quick-start)
13. [Recommended Demo Flow](#-recommended-demo-flow)
14. [What Makes It Technically Strong](#-what-makes-it-technically-strong)
15. [Implementation Status](#-implementation-status)
16. [Limitations](#-limitations)
17. [Roadmap](#-roadmap)
18. [Team and Links](#-team-and-links)

</details>

---

## 💡 Our Solution

Every incoming report travels through one unified pipeline. Each stage is implemented and demonstrable.

```mermaid
flowchart LR
    A["📝 Report"] --> B["🧹 Normalize"]
    B --> C["🤖 Classify<br/>Gemini + rules"]
    C --> D["🔍 Detect<br/>duplicates"]
    D --> E["🔗 Merge"]
    E --> F["🎯 Recommend<br/>resources"]
    F --> G["📡 Dispatch"]
    G --> H["📍 Track<br/>live"]
    H --> I["✅ Resolve"]
    I --> J["📊 Analyze"]

    classDef intake fill:#1e3a5f,stroke:#4a90d9,color:#fff
    classDef brain fill:#4a2c6b,stroke:#a86fdf,color:#fff
    classDef action fill:#7a3b12,stroke:#f0913a,color:#fff
    classDef done fill:#14532d,stroke:#4ade80,color:#fff

    class A,B intake
    class C,D,E,F brain
    class G,H action
    class I,J done
```

<div align="center">

🔵 **Intake** → 🟣 **Intelligence** → 🟠 **Action** → 🟢 **Outcome and insight**

</div>

---

## ✨ Key Features

```mermaid
mindmap
  root((PS-9))
    Intake
      Public citizen form
      One-click geolocation
      Tracking ID
    Intelligence
      Gemini classification
      Rule based fallback
      Duplicate detection
      Resource ranking
    Coordination
      Manual dispatch
      Lifecycle state machine
      Responder mobile view
    Real time
      9 Socket.IO events
      Escalation cron
      Live map
    Insight
      KPIs
      Response time trends
      Hotspot clustering
    Platform
      JWT and roles
      Demo control panel
      Toasts and connection status
```

| Feature | What it does | How it works | Status |
|---|---|---|:---:|
| **Citizen Emergency Reporting** | Public form for description, geolocation, optional address | React form → `POST /api/v1/incidents` → returns tracking ID | ✅ |
| **AI Incident Classification** | Detects type, severity, priority, summary, recommended actions | Google Gemini with schema-enforced JSON output | ✅ |
| **Rule-Based Fallback** | Guarantees classification when AI is unavailable | Keyword-weighted classifier in `classification.service.js` | ✅ |
| **Duplicate Detection** | Flags reports that likely describe the same event | `$near` geo query + time window + Jaccard text similarity (40/20/40) | ✅ |
| **Operator Dashboard** | Live command center: map, incident list, resource panel, alerts | React + Leaflet + Socket.IO | ✅ |
| **Resource Recommendation** | Ranks best-fit responders for an incident | Capability 50% + availability 25% + distance 25% | ✅ |
| **Manual Dispatch** | Operator assigns a resource in one click | `POST /incidents/:id/assign` | ✅ |
| **Incident Lifecycle** | Enforced state machine from classified to closed | Server-side transition validation | ✅ |
| **Real-Time Updates** | Every client updates without a refresh | 9 Socket.IO event types | ✅ |
| **Escalation Alerts** | Auto-alerts when P1 incidents stay unassigned | `node-cron` every minute, configurable thresholds | ✅ |
| **Interactive Map** | Live incident and resource markers | Leaflet + OpenStreetMap + custom coloured markers | ✅ |
| **Analytics Dashboard** | KPIs, distributions, response-time trends, hotspots | MongoDB aggregation pipelines + Recharts | ✅ |
| **Responder View** | Mobile-friendly assignment progression | React route `/responder`, role-gated | ✅ |
| **Demo Control Panel** | One-click Market Fire simulation and reset | `POST /demo/market-fire` runs a scripted scenario | ✅ |
| **JWT Authentication** | Role-based access for 5 roles | JWT + bcrypt + role middleware | ✅ |
| **Image Upload** | Citizen photo attachments | Cloudinary integration | 🔵 Planned |
| **OSRM Routing** | Draw the dispatch path on the map | Route overlay | 🔵 Planned |
| **Multi-language AI** | Hindi, Marathi, Gujarati classification | Gemini multilingual prompts | 🔵 Planned |

### 🖥️ Command center layout (conceptual)

```text
┌──────────────────────────────────────────────────────────────────────────┐
│ 🚨 PS-9 Command Center                        🟢 Live     👤 Operator    │
├──────────────────────────────────────────────────────────────────────────┤
│  [ Active ]     [ P1 Critical ]     [ Avg Response ]     [ Available ]   │  ← KPI cards
├───────────────────────────────────────────────┬──────────────────────────┤
│                                               │  📋 Incident list        │
│                                               │  ┌────────────────────┐  │
│              🗺️  LIVE MAP                     │  │ INC-10024  🔴 P1   │  │
│        🔥 incidents   🚒 🚑 🚓 resources       │  │ Fire · Market Rd   │  │
│                                               │  └────────────────────┘  │
│                                               │  ┌────────────────────┐  │
│                                               │  │ INC-10023  🟠 P2   │  │
├───────────────────────────┬───────────────────┤  └────────────────────┘  │
│  🚒 Resource panel        │  🔔 Alert feed    │  🎬 Demo control panel   │
│  FT-01 available          │  P1 unassigned 5m │  [ Run Market Fire ]     │
└───────────────────────────┴───────────────────┴──────────────────────────┘
        Click any incident → detail drawer: AI summary · timeline · ranked resources · Dispatch
```

<!--
📸 SCREENSHOTS (uncomment after adding images to docs/screenshots/)

| Command Center | Citizen Report | Responder View |
|:---:|:---:|:---:|
| ![Dashboard](docs/screenshots/dashboard.png) | ![Report](docs/screenshots/report.png) | ![Responder](docs/screenshots/responder.png) |

| Analytics | Incident Drawer | Market Fire Demo |
|:---:|:---:|:---:|
| ![Analytics](docs/screenshots/analytics.png) | ![Drawer](docs/screenshots/drawer.png) | ![Demo](docs/screenshots/demo.png) |
-->

---

## 🔄 How It Works

### 1. Full lifecycle, one sequence

From a citizen's tap to a resolved incident. Every arrow into **Socket.IO** is a live broadcast.

```mermaid
sequenceDiagram
    autonumber
    actor Cit as 👤 Citizen
    participant API as ⚙️ Express API
    participant AI as 🤖 Gemini / Rules
    participant DB as 🗄️ MongoDB
    participant WS as ⚡ Socket.IO
    actor Op as 🎛️ Operator
    actor Res as 🚑 Responder

    rect rgb(30, 58, 95)
    Note over Cit,WS: Phase 1 — Report and classify
    Cit->>API: POST /incidents (description + location)
    API->>AI: classifyWithAI(description)
    AI-->>API: type, severity, priority, summary, actions
    API->>DB: find duplicates (300 m, 10 min, text similarity)
    API->>DB: save Incident + SourceReport + AnalyticsEvent
    API->>WS: emit incident:created
    API-->>Cit: tracking ID + classification
    WS-->>Op: incident appears instantly
    end

    rect rgb(74, 44, 107)
    Note over Op,WS: Phase 2 — Recommend and dispatch
    Op->>API: GET /incidents/:id/recommendations
    API-->>Op: top 3 ranked resources with ETA
    Op->>API: POST /incidents/:id/assign
    API->>DB: incident = assigned, resource = assigned
    API->>WS: emit incident:assigned + resource:updated
    WS-->>Res: new assignment
    end

    rect rgb(20, 83, 45)
    Note over Res,WS: Phase 3 — Progress and resolve
    Res->>API: POST /incidents/:id/status (en_route, on_scene, resolved)
    API->>API: validate state machine transition
    API->>DB: set milestone timestamps, release resources on resolve
    API->>WS: emit incident:updated + incident:resolved
    WS-->>Op: dashboard updates without refresh
    end
```

### 2. Three personas, one platform

```mermaid
journey
    title One incident, three points of view
    section Citizen
      Open the report form: 5: Citizen
      Tap Use my current location: 5: Citizen
      Submit and receive tracking ID: 5: Citizen
    section Operator
      See the incident appear live: 5: Operator
      Read AI summary and priority: 5: Operator
      Dispatch top ranked resource: 5: Operator
    section Responder
      Accept the assignment: 4: Responder
      Move to en route and on scene: 4: Responder
      Resolve the incident: 5: Responder
```

### 3. Incident lifecycle (server-enforced state machine)

Invalid transitions are rejected with HTTP 400, so an operator or client can never skip a step.

```mermaid
stateDiagram-v2
    direction LR
    [*] --> reported
    reported --> classified: AI or rules
    classified --> assigned: operator dispatch
    assigned --> en_route: responder starts
    en_route --> on_scene: responder arrives
    on_scene --> resolved: incident handled
    resolved --> closed: archived
    classified --> merged: duplicate merged into parent
    closed --> [*]
    merged --> [*]

    note right of assigned
        Resource marked assigned
        assignedAt recorded
    end note
    note right of resolved
        Resources auto released
        resolvedAt recorded
    end note
```

### 4. Startup sequence

```mermaid
flowchart TD
    S["server.js"] --> E["Load .env via dotenv"]
    E --> M["Connect MongoDB Atlas<br/>Mongoose"]
    M --> H["Create http.Server<br/>wrapping Express"]
    H --> W["Attach Socket.IO"]
    W --> C["Start escalation cron<br/>node-cron"]
    C --> L["Listen on PORT 5000"]

    V["Vite dev server :5173"] --> P["main.jsx providers"]
    P --> P1["BrowserRouter"] --> P2["AuthProvider"] --> P3["ToastProvider"] --> R["App.jsx routes"]

    classDef be fill:#14532d,stroke:#4ade80,color:#fff
    classDef fe fill:#1e3a5f,stroke:#4a90d9,color:#fff
    class S,E,M,H,W,C,L be
    class V,P,P1,P2,P3,R fe
```

---

## 🏗️ System Architecture

### Layered overview

```mermaid
flowchart TB
    subgraph CLIENTS["🖥️ CLIENTS — React 19 + Vite"]
        direction LR
        C1["👤 Citizen<br/>/report"]
        C2["🎛️ Operator Command Center<br/>/dashboard"]
        C3["🚑 Responder<br/>/responder"]
    end

    subgraph SERVER["⚙️ SERVER — Node.js + Express 4"]
        direction TB
        MW["🛡️ Helmet · CORS · JWT · RBAC · Error handler"]

        subgraph SVC["Service layer"]
            direction LR
            INC["Incident<br/>service"]
            RES["Resource<br/>service"]
            ALR["Alert<br/>service"]
            ANA["Analytics<br/>service"]
            DEMO["Demo<br/>controller"]
        end

        subgraph ENG["Intelligence engines"]
            direction LR
            AIS["🤖 AI service"]
            DUP["🔍 Duplicate<br/>detection"]
            REC["🎯 Recommendation<br/>engine"]
            ESC["⏰ Escalation<br/>cron"]
        end

        SIO["⚡ Socket.IO<br/>safeEmit"]
    end

    subgraph DATA["💾 DATA AND EXTERNAL"]
        direction LR
        DB[("🍃 MongoDB Atlas<br/>2dsphere indexes")]
        GEM["✨ Google Gemini"]
        RULES["📏 Rule classifier"]
        OSM["🗺️ OpenStreetMap tiles"]
    end

    CLIENTS -- "REST /api/v1" --> MW
    MW --> SVC
    INC --> AIS
    INC --> DUP
    INC --> REC
    ESC --> ALR
    AIS --> GEM
    AIS -. "fallback" .-> RULES
    SVC --> DB
    ENG --> DB
    SVC --> SIO
    ESC --> SIO
    SIO == "9 live event types" ==> CLIENTS
    C2 -. "map tiles" .-> OSM

    classDef client fill:#1e3a5f,stroke:#4a90d9,color:#fff
    classDef svc fill:#14532d,stroke:#4ade80,color:#fff
    classDef eng fill:#4a2c6b,stroke:#a86fdf,color:#fff
    classDef data fill:#7a3b12,stroke:#f0913a,color:#fff
    class C1,C2,C3 client
    class INC,RES,ALR,ANA,DEMO,MW,SIO svc
    class AIS,DUP,REC,ESC eng
    class DB,GEM,RULES,OSM data
```

### Backend request pattern

```mermaid
flowchart LR
    R["HTTP request"] --> RT["Route"]
    RT --> A["requireAuth<br/>JWT verify"]
    A --> RO["requireRole<br/>role gate"]
    RO --> CT["Controller<br/>thin handler"]
    CT --> SV["Service<br/>business logic"]
    SV --> MD["Mongoose model"]
    MD --> DB[("MongoDB")]
    SV -. "safeEmit" .-> IO["Socket.IO"]
    CT --> ER["errorHandler<br/>consistent JSON"]

    classDef a fill:#1e3a5f,stroke:#4a90d9,color:#fff
    classDef b fill:#14532d,stroke:#4ade80,color:#fff
    classDef c fill:#7a3b12,stroke:#f0913a,color:#fff
    class R,RT,A,RO a
    class CT,SV,ER b
    class MD,DB,IO c
```

`route → controller → service → model`. Services call `safeEmit` and never import socket internals directly, so business logic stays decoupled from transport.

### ⚡ Real-time event bus

| Event | Fired when | Consumed by |
|---|---|---|
| `incident:created` | A new report is saved | Dashboard list and map |
| `incident:duplicate_candidates` | Similar existing incidents are found | Operator merge prompt |
| `incident:assigned` | A resource is dispatched | Dashboard, responder view |
| `incident:updated` | Status change or escalation level change | Dashboard, responder view |
| `incident:resolved` | Incident reaches resolved | Dashboard, analytics |
| `resource:updated` | Resource status changes | Resource panel, map |
| `alert:created` | Escalation raises an alert | Alert feed, toasts |
| `alert:acknowledged` | Operator acknowledges an alert | Alert feed |
| `demo:reset` | Demo data is wiped | All connected clients |

Clients use `useSocket` (connects once authenticated) and `useSocketEvent(name, handler)`, which subscribes and cleans up on unmount.

---

## 🧠 Intelligence Engines

Four deterministic, explainable engines sit between "report received" and "responder dispatched".

### 1. 🤖 AI classification pipeline

**Model:** Google Gemini via `@google/generative-ai`, with `responseSchema` enum constraints on type, severity and priority. **The app never fails classification.**

```mermaid
flowchart TD
    IN["📝 Incident description<br/>+ optional coordinates"] --> P["Build strict prompt<br/>no markdown · no invented IDs"]
    P --> M1["Try gemini-3.6-flash<br/>2 retries on 503 / 429 / timeout"]
    M1 -- "ok" --> V
    M1 -- "fail" --> M2["Try gemini-flash-latest<br/>2 retries"]
    M2 -- "ok" --> V
    M2 -- "fail" --> M3["Try gemini-3.5-flash<br/>2 retries"]
    M3 -- "ok" --> V
    M3 -- "fail" --> M4["Try gemini-3.7-flash<br/>2 retries"]
    M4 -- "ok" --> V
    M4 -- "fail" --> RB["📏 Rule-based classifier<br/>keyword weighted"]
    V{"Validate every field<br/>against allowed enums"}
    V -- "valid" --> OUT["✅ Structured result<br/>source: ai"]
    V -- "invalid, auto-correct or reject" --> RB
    RB --> OUT2["✅ Structured result<br/>source: rules_fallback"]

    classDef ok fill:#14532d,stroke:#4ade80,color:#fff
    classDef ai fill:#4a2c6b,stroke:#a86fdf,color:#fff
    classDef fb fill:#7a3b12,stroke:#f0913a,color:#fff
    class OUT,OUT2 ok
    class M1,M2,M3,M4,P ai
    class RB fb
```

<details>
<summary><b>📤 Example AI output</b></summary>

```json
{
  "type": "fire",
  "severity": "critical",
  "priority": "P1",
  "confidence": 0.98,
  "summary": "Large fast-spreading fire near central market with trapped individuals.",
  "recommendedActions": [
    "Dispatch fire suppression units immediately",
    "Evacuate central market and surrounding area",
    "Deploy search and rescue teams",
    "Establish a secure perimeter"
  ],
  "source": "ai",
  "model": "gemini-3.6-flash",
  "elapsedMs": 3507
}
```

</details>

> **Design rule:** AI output is advisory. It is stored separately from operator actions and the system **never auto-dispatches**.

### 2. 🔍 Duplicate detection

Three signals are combined into one explainable score, with a per-candidate breakdown shown to the operator.

```mermaid
flowchart LR
    N["🆕 New report"] --> G["📍 Geo filter<br/>MongoDB $near within 300 m"]
    G --> T["🕒 Time window<br/>last 10 minutes"]
    T --> S["Score each candidate"]
    S --> J["Location 40%<br/>Time 20%<br/>Text similarity 40%"]
    J --> C["📋 duplicateCandidates[]<br/>with score breakdown"]
    C --> O["🎛️ Operator reviews<br/>and can merge"]

    classDef a fill:#1e3a5f,stroke:#4a90d9,color:#fff
    classDef b fill:#4a2c6b,stroke:#a86fdf,color:#fff
    classDef c fill:#14532d,stroke:#4ade80,color:#fff
    class N,G,T a
    class S,J b
    class C,O c
```

```mermaid
pie showData title Duplicate score weights
    "Location proximity" : 40
    "Time proximity" : 20
    "Text similarity (Jaccard)" : 40
```

### 3. 🎯 Resource recommendation

A deterministic ranking, so every suggestion can be debugged and defended.

```mermaid
flowchart LR
    I["🚨 Incident<br/>type"] --> RC["Required capabilities<br/>e.g. fire_suppression"]
    RC --> F["Fetch available<br/>resources"]
    F --> SC["Score each"]
    SC --> W["Capability 50%<br/>Availability 25%<br/>Distance 25%"]
    W --> TOP["🥇 Top 3<br/>with distance and ETA"]
    TOP --> D["📡 Operator dispatches"]

    classDef a fill:#1e3a5f,stroke:#4a90d9,color:#fff
    classDef b fill:#4a2c6b,stroke:#a86fdf,color:#fff
    classDef c fill:#14532d,stroke:#4ade80,color:#fff
    class I,RC,F a
    class SC,W b
    class TOP,D c
```

```mermaid
pie showData title Recommendation score weights
    "Capability match" : 50
    "Availability" : 25
    "Distance (Haversine)" : 25
```

### 4. ⏰ Escalation engine

A cron job runs **every minute** and raises an alert when an incident has waited too long without a responder.

```mermaid
flowchart TD
    TICK["⏱️ node-cron tick<br/>every minute"] --> FETCH["Fetch active incidents"]
    FETCH --> LOOP{"For each incident"}
    LOOP --> HAS{"Resource<br/>already assigned?"}
    HAS -- "yes" --> SKIP["⏭️ Skip"]
    HAS -- "no" --> AGE["Compute age vs<br/>priority thresholds"]
    AGE --> PAST{"Past threshold and<br/>not yet escalated<br/>at that level?"}
    PAST -- "no" --> SKIP
    PAST -- "yes" --> LVL["Set escalationLevel<br/>1 warning or 2 critical"]
    LVL --> AL["🔔 alertService.createAlert"]
    AL --> EM["⚡ emit alert:created<br/>+ incident:updated"]

    classDef a fill:#1e3a5f,stroke:#4a90d9,color:#fff
    classDef b fill:#7a3b12,stroke:#f0913a,color:#fff
    classDef c fill:#7f1d1d,stroke:#f87171,color:#fff
    class TICK,FETCH,LOOP,HAS,PAST a
    class AGE,SKIP b
    class LVL,AL,EM c
```

**Default thresholds** (minutes an incident may wait unassigned, configurable via `.env`):

| Priority | ⚠️ Warning (level 1) | 🔴 Critical (level 2) |
|:---:|:---:|:---:|
| **P1** | 2 | 5 |
| **P2** | 5 | 10 |
| **P3** | 15 | 30 |
| **P4** | 30 | 60 |

The engine is **idempotent**: it never fires the same level twice for the same incident.

---

## 🧰 Tech Stack

| Layer | Technology | Purpose |
|---|---|---|
| **Frontend** | ![React](https://img.shields.io/badge/React_19-61DAFB?logo=react&logoColor=black&style=flat-square) ![Vite](https://img.shields.io/badge/Vite-646CFF?logo=vite&logoColor=white&style=flat-square) | SPA UI and dev server |
| **Routing and HTTP** | React Router v6 · Axios | Client routing, REST calls with JWT interceptor |
| **Real time (client)** | Socket.IO Client | Live updates |
| **Maps** | Leaflet · React-Leaflet · OpenStreetMap | Interactive incident and resource map (no API key) |
| **Charts and icons** | Recharts · Lucide React | Analytics and iconography |
| **Styling** | CSS3 variables + inline styles | Dark command-center theme |
| **Backend** | ![Node](https://img.shields.io/badge/Node.js-339933?logo=nodedotjs&logoColor=white&style=flat-square) ![Express](https://img.shields.io/badge/Express_4-000000?logo=express&logoColor=white&style=flat-square) | REST API |
| **Database** | ![MongoDB](https://img.shields.io/badge/MongoDB_Atlas-47A248?logo=mongodb&logoColor=white&style=flat-square) Mongoose ODM | Primary store with `2dsphere` geo support |
| **Real time (server)** | Socket.IO | WebSocket broadcasting |
| **AI** | ![Gemini](https://img.shields.io/badge/Gemini-8E75B2?logo=googlegemini&logoColor=white&style=flat-square) `@google/generative-ai` | Incident classification |
| **Auth** | `jsonwebtoken` · `bcryptjs` | Stateless auth and password hashing |
| **Scheduler** | `node-cron` | Escalation checks every minute |
| **Security** | Helmet · CORS · `express-rate-limit` | HTTP hardening |
| **Dev tooling** | Nodemon · Git · Postman / Thunder Client | Developer experience |
| **Deploy targets** | Vercel (frontend) · Render (backend) · MongoDB Atlas (DB) | Cloud-ready |

### 🔌 External integrations

| Service | Purpose | Where | Key needed |
|---|---|---|:---:|
| **Google Gemini** | Classify incident text | `server/src/services/ai.service.js` | ✅ `GEMINI_API_KEY` (server only) |
| **MongoDB Atlas** | Data and geospatial queries | `server/src/config/db.js` | ✅ `MONGODB_URI` |
| **OpenStreetMap tiles** | Map tiles | `client/src/components/map/MapView.jsx` | ❌ none |
| **Socket.IO** | Bidirectional events | client and server | ❌ none |

---

## 📡 API Reference

**Base URL:** `/api/v1` · **29 endpoints** across 6 route groups plus health

```mermaid
flowchart LR
    API["/api/v1"] --> AU["/auth<br/>3"]
    API --> IN["/incidents<br/>7"]
    API --> RE["/resources<br/>4"]
    API --> AL["/alerts<br/>3"]
    API --> AN["/analytics<br/>8"]
    API --> DE["/demo<br/>2"]
    API --> HE["/health and /<br/>2"]

    classDef g fill:#1e3a5f,stroke:#4a90d9,color:#fff
    class API,AU,IN,RE,AL,AN,DE,HE g
```

<details>
<summary><b>🔐 Authentication (3)</b></summary>

| Method | Endpoint | Purpose | Auth | Request | Response |
|---|---|---|---|---|---|
| POST | `/auth/register` | Register new user | Public | `{name, email, password, role?}` | `{token, user}` |
| POST | `/auth/login` | Log in | Public | `{email, password}` | `{token, user}` |
| GET | `/auth/me` | Current user | Bearer | none | `user` |

</details>

<details open>
<summary><b>🚨 Incidents (7)</b></summary>

| Method | Endpoint | Purpose | Auth | Roles |
|---|---|---|---|---|
| POST | `/incidents` | Citizen submits report | Public | none |
| GET | `/incidents` | List with filters (`status`, `severity`, `priority`, `type`, `active`) | Bearer | operator, admin |
| GET | `/incidents/:id` | Single incident (ObjectId or `INC-xxxxx`) | Bearer | any |
| POST | `/incidents/:id/assign` | Dispatch a resource | Bearer | operator, admin |
| POST | `/incidents/:id/status` | Transition status | Bearer | operator, admin, responder |
| POST | `/incidents/:id/merge` | Merge a duplicate into this incident | Bearer | operator, admin |
| GET | `/incidents/:id/recommendations` | Ranked resource suggestions | Bearer | any |

</details>

<details>
<summary><b>🚒 Resources (4)</b></summary>

| Method | Endpoint | Purpose | Auth | Roles |
|---|---|---|---|---|
| GET | `/resources` | List with filters | Bearer | any |
| GET | `/resources/:id` | Single resource | Bearer | any |
| PATCH | `/resources/:id/status` | Change status | Bearer | operator, admin, responder |
| POST | `/resources/seed` | Seed 19 demo resources | Bearer | admin |

</details>

<details>
<summary><b>🔔 Alerts (3)</b></summary>

| Method | Endpoint | Purpose | Auth | Roles |
|---|---|---|---|---|
| GET | `/alerts` | List alerts | Bearer | any |
| GET | `/alerts/:id` | Single alert | Bearer | any |
| PATCH | `/alerts/:id/acknowledge` | Acknowledge | Bearer | operator, admin |

</details>

<details>
<summary><b>📊 Analytics (8)</b> — operator and admin only</summary>

| Method | Endpoint | Purpose |
|---|---|---|
| GET | `/analytics/overview` | KPI summary |
| GET | `/analytics/types` | Incidents grouped by type |
| GET | `/analytics/severity` | Grouped by severity |
| GET | `/analytics/priority` | Grouped by priority |
| GET | `/analytics/response-time?days=7` | Daily average response time |
| GET | `/analytics/resources` | Utilisation stats |
| GET | `/analytics/hotspots` | Geographic clustering (rounded grid coordinates) |
| GET | `/analytics/events?limit=50` | Recent event log |

</details>

<details>
<summary><b>🎬 Demo (2) and ❤️ Health (2)</b></summary>

| Method | Endpoint | Purpose | Auth | Roles |
|---|---|---|---|---|
| POST | `/demo/reset` | Wipe incidents, alerts and events; release resources | Bearer | admin, operator |
| POST | `/demo/market-fire` | Trigger the scripted scenario | Bearer | admin, operator |
| GET | `/health` | Server and DB status | Public | none |
| GET | `/` | API version info | Public | none |

</details>

---

## 🗄️ Database Design

**MongoDB Atlas** · **Mongoose ODM** · **`2dsphere` geospatial indexes** on incident and resource locations.

```mermaid
erDiagram
    USER ||--o{ ANALYTICS_EVENT : "acts in"
    INCIDENT ||--o{ SOURCE_REPORT : "has many"
    INCIDENT }o--o{ RESOURCE : "dispatched to"
    INCIDENT ||--o{ ANALYTICS_EVENT : logs
    INCIDENT ||--o{ ALERT : triggers
    RESOURCE ||--o{ ALERT : notifies
    COUNTER ||--o{ INCIDENT : "generates IDs"
    COUNTER ||--o{ SOURCE_REPORT : "generates IDs"

    USER {
        ObjectId _id PK
        string email
        string passwordHash
        string role
        string responderType
    }
    INCIDENT {
        string publicId "INC-10024"
        string type
        string severity
        string priority
        string status
        Point location "2dsphere"
        object ai
        array duplicateCandidates
        int escalationLevel
    }
    SOURCE_REPORT {
        string publicId "REP-10001"
        ObjectId incidentId FK
        string description
        Point location
    }
    RESOURCE {
        string publicId "FT-01"
        string subtype
        string status
        array capabilities
        Point location "2dsphere"
        ObjectId assignedIncidentId FK
    }
    ALERT {
        ObjectId incidentId FK
        string severity
        string message
        bool acknowledged
    }
    ANALYTICS_EVENT {
        ObjectId incidentId FK
        string eventType
        ObjectId actorId FK
    }
    COUNTER {
        string _id
        number seq
    }
```

<details>
<summary><b>📚 Collections and key fields</b></summary>

| Collection | Purpose |
|---|---|
| `users` | Auth accounts and roles |
| `incidents` | Central entity with AI metadata and lifecycle |
| `sourcereports` | Immutable raw reports (many per incident) |
| `resources` | Fire teams, ambulances, police, rescue, hospitals |
| `alerts` | Escalation and info alerts |
| `analyticsevents` | Event log powering KPIs |
| `counters` | Sequential ID generator (`INC-10001`, `REP-10001`) |

**Incident**

| Field | Values / notes |
|---|---|
| `type` | fire · flood · medical · accident · industrial · structural · other |
| `severity` | low · medium · high · critical |
| `priority` | P1 · P2 · P3 · P4 |
| `status` | reported → classified → assigned → en_route → on_scene → resolved → closed, or merged |
| `ai` | classified, confidence, summary, recommendedActions, source |
| Timeline | `assignedAt`, `onSceneAt`, `resolvedAt`, `closedAt` |

**Resource**

| Field | Values / notes |
|---|---|
| `publicId` | `FT-01`, `AMB-02`, `PU-03`, `RS-01`, `HOSP-01` |
| `subtype` | fire_team · ambulance · police · rescue · hospital · shelter |
| `status` | available · assigned · en_route · on_scene · unavailable |
| `capabilities[]` | `fire_suppression`, `medical`, `hazmat`, and more |

**User:** `passwordHash` is never returned by the API. Roles: citizen · responder · operator · admin · hospital.

</details>

---

## 🔐 Security and Access Control

### Role permissions

| Capability | 🌐 Public | 👤 Citizen | 🚑 Responder | 🎛️ Operator | 🛠️ Admin |
|---|:---:|:---:|:---:|:---:|:---:|
| Submit an incident report | ✅ | ✅ | ✅ | ✅ | ✅ |
| View a single incident, resources, alerts | ❌ | ✅ | ✅ | ✅ | ✅ |
| Progress incident status, update resource status | ❌ | ❌ | ✅ | ✅ | ✅ |
| List all incidents, dispatch, merge, acknowledge alerts | ❌ | ❌ | ❌ | ✅ | ✅ |
| View analytics, run and reset demo | ❌ | ❌ | ❌ | ✅ | ✅ |
| Seed resources | ❌ | ❌ | ❌ | ❌ | ✅ |

### Safeguards

| Mechanism | Detail |
|---|---|
| **Password hashing** | `bcryptjs`, 10 rounds |
| **JWT authentication** | HS256, 7-day expiry, signed with `JWT_SECRET` |
| **Role-based access control** | `requireRole(...)` middleware on every protected route |
| **Privilege escalation blocked** | Public registration is forced to `citizen` or `responder`, so nobody can self-register as admin or operator |
| **Secret hygiene** | `passwordHash` stripped by `User.toJSON()`; all secrets in gitignored `.env`; Gemini key never reaches the browser |
| **CORS** | Restricted to `CLIENT_URL` |
| **HTTP hardening** | Helmet (CSP relaxed only for the dev socket-test page) |
| **Error handling** | Global handler maps Mongoose and API errors to consistent JSON; stack traces never leak in production |
| **Validation** | Mongoose schema level plus controller level |
| **Rate limiting** | `express-rate-limit` installed, enabled when configured |

---

## 📁 Project Structure

<details>
<summary><b>🖧 server/ — Node.js + Express + Socket.IO</b></summary>

```text
server/
├── server.js                      # Entry: env → DB → http → Socket.IO → cron
├── scripts/createAdmin.js
├── public/socket-test.html        # Debug page for Socket.IO
└── src/
    ├── app.js                     # Express app + middleware + routes
    ├── config/db.js               # MongoDB connection
    ├── controllers/               # Thin HTTP handlers
    │   ├── auth · incident · resource · alert · analytics · demo
    ├── middleware/
    │   ├── auth.js                # JWT verify + requireRole
    │   └── errorHandler.js        # Global error mapper
    ├── models/                    # Mongoose schemas (2dsphere indexes)
    │   ├── User · Incident · SourceReport · Resource
    │   └── Alert · AnalyticsEvent · Counter
    ├── routes/                    # 6 route groups
    ├── services/                  # ★ All business logic
    │   ├── ai.service.js              # Gemini + 4-model fallback
    │   ├── classification.service.js  # Rule engine
    │   ├── duplicate.service.js       # Geo + time + text scoring
    │   ├── resource.service.js        # Ranking + CRUD
    │   ├── incident.service.js        # Orchestration
    │   ├── alert.service.js
    │   ├── escalation.service.js      # node-cron
    │   └── analytics.service.js       # Aggregation pipelines
    ├── sockets/socket.js          # initSocket + safeEmit
    ├── seed/seedData.js           # Users, resources, incidents, alerts
    └── utils/                     # logger · generateId · distance · ApiError · asyncHandler · apiResponse
```

</details>

<details>
<summary><b>🖥️ client/ — React 19 + Vite</b></summary>

```text
client/
├── index.html · vite.config.js · package.json
└── src/
    ├── main.jsx · App.jsx
    ├── pages/                     # Route-level components
    │   ├── Login · CitizenReport · Dashboard · Incidents
    │   └── IncidentDetails · Resources · Alerts · Analytics · Responder
    ├── components/                # Grouped by domain
    │   ├── alerts/                # AlertFeed
    │   ├── analytics/             # ChartCard + Type / Severity / ResponseTime / ResourceUtil charts
    │   ├── common/                # Badge · Button · Card · Input · Layout · Toast
    │   │                          # ConnectionStatus · ProtectedRoute
    │   ├── dashboard/             # DemoControlPanel · KPICards
    │   ├── incidents/             # IncidentCard · IncidentDetailPanel
    │   ├── map/                   # MapView (Leaflet)
    │   ├── resources/             # RecommendationCard · ResourcePanel
    │   └── responder/             # AssignmentCard
    ├── context/AuthContext.jsx
    ├── hooks/useSocket.js
    ├── services/                  # api.js (Axios + JWT) · socket.js
    ├── styles/                    # variables · global · responsive
    └── utils/                     # formatters · leafletSetup
```

</details>

### 🌐 Frontend routes

| Route | Page | Roles |
|---|---|---|
| `/login` | Login (with demo-account quick-fill) | Public |
| `/report` | Citizen Report | Public |
| `/dashboard` | Command Center | operator, admin |
| `/incidents` | Incidents list | operator, admin |
| `/incidents/:id` | Incident details (stub, drawer covers most use) | operator, admin, responder |
| `/resources` | Resource fleet | operator, admin |
| `/alerts` | Alert feed | operator, admin |
| `/analytics` | Charts and KPIs | operator, admin |
| `/responder` | My assignments (mobile-friendly) | responder |

**State:** React Context for auth, local state elsewhere. No Redux, because the scale does not justify it. Axios injects the JWT and auto-logs-out on `401`.

---

## 🚀 Quick Start

**Prerequisites:** Node.js v18+ · npm v9+ · a free MongoDB Atlas cluster · a Gemini API key from [Google AI Studio](https://aistudio.google.com/app/apikey)

```mermaid
flowchart LR
    A["1️⃣ Clone"] --> B["2️⃣ server/.env"]
    B --> C["3️⃣ npm run seed"]
    C --> D["4️⃣ npm run dev<br/>server :5000"]
    D --> E["5️⃣ client/.env"]
    E --> F["6️⃣ npm run dev<br/>client :5173"]
    F --> G["🎉 Open localhost:5173"]

    classDef s fill:#1e3a5f,stroke:#4a90d9,color:#fff
    classDef ok fill:#14532d,stroke:#4ade80,color:#fff
    class A,B,C,D,E,F s
    class G ok
```

### 1. Clone

```bash
git clone https://github.com/<your-username>/PS-9.git
cd PS-9
```

### 2. Backend

```bash
cd server
npm install
```

Create `server/.env`:

```env
PORT=5000
MONGODB_URI=            # MongoDB Atlas connection string
JWT_SECRET=             # any long random string
GEMINI_API_KEY=         # from aistudio.google.com/app/apikey
CLIENT_URL=http://localhost:5173
NODE_ENV=development

# Escalation thresholds (minutes)
ESCALATION_ENABLED=true
ESCALATION_P1_WARNING=2
ESCALATION_P1_CRITICAL=5
ESCALATION_P2_WARNING=5
ESCALATION_P2_CRITICAL=10
ESCALATION_P3_WARNING=15
ESCALATION_P3_CRITICAL=30
ESCALATION_P4_WARNING=30
ESCALATION_P4_CRITICAL=60
```

```bash
npm run seed     # 6 users · 19 resources · sample incidents and alerts
npm run dev      # → http://localhost:5000
```

### 3. Frontend

In a new terminal:

```bash
cd client
npm install
```

Create `client/.env`:

```env
VITE_API_URL=http://localhost:5000/api/v1
VITE_SOCKET_URL=http://localhost:5000
```

```bash
npm run dev      # → http://localhost:5173
```

### 🔑 Demo accounts

Open the login page and use the **quick-fill demo account buttons** (Operator, Responder, and more). Seeded responder: `responder1@ps9.local` / `password123`.

> All demo data (incidents, resources, users) is synthetic. Coordinates are centred on Ahmedabad.

---

## 🎯 Recommended Demo Flow

**Duration: 2 to 3 minutes · only working features.** Use three browser tabs: operator, citizen and responder.

```mermaid
gantt
    title 2 minute 50 second judge demo
    dateFormat mm:ss
    axisFormat %M:%S
    section Setup
    Frame the problem               :done, a1, 00:00, 15s
    Log in as operator              :done, a2, after a1, 10s
    Tour the live dashboard         :done, a3, after a2, 10s
    section Report to dispatch
    Citizen submits fire report     :crit, b1, after a3, 20s
    Show Gemini classification      :b2, after b1, 10s
    Ranked recommendations          :b3, after b2, 15s
    One-click dispatch              :crit, b4, after b3, 10s
    section Field to analytics
    Responder tab shows assignment  :c1, after b4, 15s
    Accept - En route - On scene - Resolve :c2, after c1, 15s
    Dashboard updates live          :c3, after c2, 10s
    Run Market Fire scenario        :c4, after c3, 20s
    Show analytics                  :c5, after c4, 20s
    Closing line                    :done, c6, after c5, 10s
```

| Time | Step | What to say |
|---|---|---|
| 0:00 | Show the problem | "During emergencies, reports come from everywhere, but they never get coordinated." |
| 0:15 | Log in as operator | "This is our command center." |
| 0:25 | Show dashboard | "Live map, incidents, resources, alerts, all updating in real time." |
| 0:35 | Submit a citizen report | "Let me have a citizen report a fire." |
| 0:55 | Show AI classification | "Gemini classified it as P1 critical, with confidence and recommended actions." |
| 1:05 | Click the incident | "Recommended resources, ranked by capability, availability and distance." |
| 1:20 | Dispatch | "One click dispatches the top fire team." |
| 1:30 | Switch to responder tab | "In the field, the responder sees the assignment live." |
| 1:45 | Progress through statuses | "Accept, En Route, On Scene, Resolve. Every change broadcasts." |
| 2:00 | Back to dashboard | "The operator view updated without a refresh." |
| 2:10 | Run Market Fire | "We built a one-click demo of the entire lifecycle." |
| 2:30 | Show analytics | "All of this feeds real-time analytics." |
| 2:50 | Close | "PS-9 turns fragmented reports into coordinated response." |

### 🔥 The one-click "Market Fire" scenario

`POST /api/v1/demo/market-fire` responds immediately, then runs a scripted lifecycle **through the real services and real Socket.IO broadcasts**. Nothing is faked on the front end.

```mermaid
timeline
    title Market Fire scripted scenario
    T+0s : Report 1 created and AI classified
    T+5s : Report 2 arrives from the same area
         : Duplicate detected
    T+15s : Best fire team auto assigned
    T+30s : Status moves to en route
    T+45s : Status moves to on scene
    T+60s : Resolved
          : Resources auto released
```

---

## 💪 What Makes It Technically Strong

Implementation details, not marketing:

| # | Highlight | Detail |
|:---:|---|---|
| 1 | **Multi-signal duplicate detection** | `$near` (300 m) + time window + Jaccard text similarity, weighted 40/20/40, with explainable breakdown per candidate |
| 2 | **Resilient AI pipeline** | 4-model fallback chain plus rule classifier. Classification works whether Gemini is up, slow or down |
| 3 | **Deterministic recommendation** | Capability 50% + availability 25% + distance 25%, with ETA estimation. Explainable and debuggable |
| 4 | **State machine with validation** | Lifecycle enforced server-side. Invalid transitions return HTTP 400 |
| 5 | **Real-time event bus** | 9 Socket.IO event types drive every live view |
| 6 | **Database-level geospatial indexing** | `2dsphere` on incidents and resources, so `$near` scales with MongoDB |
| 7 | **Idempotent cron escalation** | Priority-based thresholds, never fires the same level twice, skips incidents with assigned resources |
| 8 | **Aggregation-pipeline analytics** | 8 endpoints, including hotspot clustering on rounded grid coordinates |
| 9 | **Sequential public IDs** | Counter collection gives restart-safe `INC-10001` and `REP-10001` |
| 10 | **Role-based access control** | 5 roles with route-level and controller-level enforcement |
| 11 | **Configuration by environment** | AI model, escalation thresholds and secrets, with nothing hardcoded |
| 12 | **Demo through real services** | Market Fire uses production code paths end to end |

---

## ✅ Implementation Status

```mermaid
pie showData title Feature status
    "Implemented and working" : 12
    "Partial" : 1
    "Planned" : 4
```

| Module | Status | Details |
|---|:---:|---|
| **Frontend** | ✅ Done | 9 routes, live map, detail drawer, charts |
| **Backend** | ✅ Done | Express with 6 route groups and health endpoints |
| **Database** | ✅ Done | MongoDB Atlas, 7 models, geo indexes |
| **Authentication** | ✅ Done | JWT + bcrypt + roles |
| **AI Classification** | ✅ Done | Gemini + 4-model fallback + rules |
| **Duplicate Detection** | ✅ Done | Geo + time + text scoring |
| **Resource Recommendation** | ✅ Done | Weighted scoring with ETA |
| **Real-Time (Socket.IO)** | ✅ Done | 9 event types, live dashboard |
| **Escalation** | ✅ Done | node-cron, priority thresholds, dedup |
| **Analytics** | ✅ Done | 8 aggregation endpoints + Recharts |
| **Seed Data** | ✅ Done | 6 users, 19 resources, incidents, alerts |
| **Demo Mode** | ✅ Done | One-click Market Fire + Reset |
| **Incident Details Page** | 🟡 Partial | Route exists, drawer covers most use |
| **Image Upload** | 🔵 Planned | Cloudinary integration |
| **OSRM Routing** | 🔵 Planned | Route overlay on map |
| **Multilingual AI** | 🔵 Planned | Hindi, Marathi, Gujarati |
| **SMS / Email notifications** | 🔵 Planned | In-app alerts only today |

---

## ⚠️ Limitations

Being upfront about what is not production-ready:

| Area | Limitation |
|---|---|
| **Free-tier services** | Render may spin down; Atlas free tier has caps; Gemini free tier has rate limits |
| **Notifications** | In-app only, with no SMS or email |
| **Attachments** | Schema field exists, but there is no upload flow yet |
| **Routing** | Distance and ETA are estimated, not routed (no OSRM overlay yet) |
| **Scale** | Tuned for 5 to 20 concurrent users, not thousands |
| **AI role** | Advisory only. The system never auto-dispatches from AI output |
| **Data** | Fully synthetic, with Ahmedabad as a fictional centre |
| **Fallback classifier** | Heuristic, not a replacement for real emergency triage |
| **Config** | `.env` files are created manually |
| **Sessions** | No refresh-token flow. JWTs last 7 days and logout is client-side |
| **Scheduler** | Escalation cron uses UTC |

---

## 🗺️ Roadmap

```mermaid
flowchart LR
    subgraph NOW["✅ SHIPPED — MVP"]
        direction TB
        N1["Report to resolve pipeline"]
        N2["AI + rule fallback"]
        N3["Live command center"]
        N4["Escalation + analytics"]
    end
    subgraph NEXT["🔜 NEXT"]
        direction TB
        X1["Image upload via Cloudinary"]
        X2["OSRM routing overlay"]
        X3["Multilingual AI"]
        X4["SMS / email / push via Twilio and SendGrid"]
    end
    subgraph LATER["🔭 LATER"]
        direction TB
        L1["Kafka / Redis Pub-Sub event streaming"]
        L2["Vector search on incident history"]
        L3["Computer vision on photos"]
        L4["Multi-district tenancy"]
        L5["Offline-first responder app"]
    end
    NOW --> NEXT --> LATER

    classDef n fill:#14532d,stroke:#4ade80,color:#fff
    classDef x fill:#7a3b12,stroke:#f0913a,color:#fff
    classDef l fill:#4a2c6b,stroke:#a86fdf,color:#fff
    class N1,N2,N3,N4 n
    class X1,X2,X3,X4 x
    class L1,L2,L3,L4,L5 l
```

<details>
<summary><b>Full enhancement list</b></summary>

- **Event streaming** (Kafka or Redis Pub-Sub) to decouple services beyond Socket.IO
- **Vector search** on incident history to find similar past incidents via embeddings
- **Image and video attachments** via Cloudinary
- **OSRM / HERE routing** for real routes and traffic-aware ETA
- **Multi-district tenancy** with separate operator teams by zone
- **Custom ML model** trained on real incidents, replacing the rule fallback
- **Computer vision** to classify from uploaded photos
- **Voice-to-incident** using the Web Speech API
- **Multilingual AI** (Gemini is already multilingual-capable)
- **Native mobile app** for responders, with **offline-first** sync on reconnect
- **SMS, email and push** via Twilio and SendGrid
- **High-availability deployment** on Kubernetes with managed PostgreSQL/PostGIS for hot data

</details>

---

## 👥 Team and Links

| Role | Name |
|---|---|
| *Backend And API* | *Divya Prajapati* |
| *Frontend & UI/UX Testing* |*Manpreet Kaur Sandhu* |
| *Databases and AI Engine* | *Krisha Mewada* |
| Team | *Solution Sprints 🌟* |

| 🔗 Link | URL |
|---|---|
| **GitHub** | `https://github.com/Divya112-ai/RakshakAI` |
| **Live Demo** | *Will Be Added after deploying to Vercel + Render* |
| **Video Demo** | *Will Add recording link* |
| **Documentation** | This README |

### 📄 License

No license file is currently present, so treat this as a **hackathon submission with all rights reserved** unless a license is added. To open-source it, add an `MIT` `LICENSE` file.

---

<div align="center">

**Built with care for the PS-9 hackathon**

`Report` → `Classify` → `Detect` → `Dispatch` → `Track` → `Resolve` → `Analyze`

⭐ If this project helped you understand the problem, consider giving it a star.

</div>
