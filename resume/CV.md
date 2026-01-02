# ABDALLAH ABD-EL-FATTAH

**Senior Software Engineer | Full-Stack & Data Engineering | System Design**

+201282849136 | <abdallah.a.elfatah@gmail.com> | [LinkedIn](https://linkedin.com/in/abdallahabdelfatah) | [GitHub](https://github.com/abdallahAbdElFattah13) | [abdallah-abdelfattah.me](https://abdallah-abdelfattah.me)

## PROFESSIONAL SUMMARY

Software Engineer with 8+ years building scalable systems across full-stack web, mobile, and data engineering. Track record of end-to-end ownership—from architecture through deployment—with measurable impact: 96% cost reduction through platform optimization, 75% faster development cycles via reusable frameworks, and zero-downtime migrations of production data pipelines.

Experienced in designing systems that enable team autonomy and eliminate cross-team dependencies. Strong background in both individual contributor and engineering management roles, with expertise in stakeholder management, technical research, and building frameworks that lower barriers for team contributions.


## TECHNICAL SKILLS

**Languages:** Java 17, Python, Kotlin, JavaScript, TypeScript, SQL, Rego (OPA), HCL (Terraform)

**Backend & Data:** Spring Boot, Django, REST APIs, Snowflake, Snowpark, DynamoDB, PostgreSQL

**Frontend:** React, Context API, MUI (Material-UI), Looker (Embedded Analytics), Angular

**Mobile:** Android (Kotlin/Java), React Native, Cordova

**Infrastructure:** Terraform, AWS, Datadog, Docker, CI/CD, GitHub Actions, Firebase Distribution

**Architecture:** Clean Architecture, Micro-Frontend, Event-Driven, Single-Table NoSQL Design

**Patterns:** Factory, Facade, Repository, Template Method, Strategy, Provider, Mapper

**Testing:** JUnit, pytest, Testcontainers, REST Assured, Unit/Integration/E2E

**Security:** RBAC, Open Policy Agent (OPA), JWT, Fail-Safe Authorization Design


## WORK EXPERIENCE

### Senior Full Stack Engineer | c3s Software (Single Digits)

**Aug 2024 - Present | Remote**

Full-stack web and data engineering across React frontend, Spring Boot/Python backend, and Snowflake data platform. End-to-end ownership from architecture through deployment.

- Delivered 6 major initiatives spanning frontend architecture, data engineering, infrastructure, monitoring, and authorization systems
- Technologies: React, Java 17, Spring Boot, Python, Snowflake, DynamoDB, Terraform, Datadog, OPA

### Engineering Manager | Dubizzle Egypt

**Jun 2022 - Aug 2023 | Remote**

Reported to country manager. Owned product roadmaps impacting Egypt, Lebanon, Oman, and Bahrain markets. Managed cross-departmental stakeholder relationships.

- Led engineering delivery for Pro-Agency Portal, Telesales Tool, and Drop-offs System
- Established communication lines with Sector Labs engineering leadership for cross-market alignment
- Contributed to codebases as full-stack engineer (Django/React)

### ReactNative Engineer | Dubizzle Egypt

**Jan 2022 - Jun 2022 | Remote**

Squad lead for Real-estate verticals epic across web and mobile platforms.

- Led migration of user base from native Android to cross-platform ReactNative app
- Collaborated with sister company Sector Labs on shared codebases
- Coached junior engineers; conducted candidate interviews

### Senior Android Engineer | Dubizzle Egypt

**Oct 2020 - Dec 2021 | Cairo**

Android development for OLX Arabia app (10M+ installs, 260M MAU globally).

- Delivered features serving customer and business needs including Pay-and-Ship integration
- Designed cross-platform analytics module adopted across all disciplines
- Led release planning and cross-team coordination; coached juniors via pair programming

### Software Engineer II | Amazon

**Jun 2020 - Aug 2020 | Remote, Spain**

Full-stack engineer in Amazon Business organization.

- Worked on large-scale international projects in Agile environment
- Participated in complete software lifecycle

### Senior Android Engineer | The D. GmbH

**May 2018 - May 2020 | Cairo**

Android development for consumer apps including CUJU (football training) and white-label event platforms.

- Designed and built advanced Android applications
- Collaborated with cross-functional international team
- Recruited and trained junior team members

### Solutions Engineer | Vision Valley

**Jan 2016 - Apr 2018 | Cairo**

Single solutions engineer creating apps across Android, cross-platform, and backend.

- Built PoCs and presented to management for approval
- Partnered with product management on roadmaps
- Recruited new team members

## PROJECTS

### c3s Software / Single Digits (2024-2025)

**MUI Version Migration Facade Architecture**
Feb 2025 | React, JavaScript, Context API, Factory Pattern, Facade Pattern, Micro-Frontend

Business Problem:
5+ micro-apps needed different MUI versions, but shared reporting libraries forced version coupling. Frontend team blocked by Reporting team for any MUI migration.

Solution:
Designed version-aware Facade architecture with MuiVersionProvider context propagating version through component tree. Built createVersionedComponent factory dynamically selecting correct implementation at runtime.

Technical Implementation:

- Unified reporting-components-library and reporting-dashboards-library as single source of truth
- Mirrored directory structure (mui-v4/, mui-v5/, mui-v6/) ensuring feature parity
- Graceful degradation with console warnings for invalid configurations
- React.memo optimization preventing unnecessary re-renders

Business Impact:

- 5+ micro-apps unified under single library system
- 20 dashboards work across any MUI version
- Eliminated duplicate implementations and cross-team blocking
- Authored ADR gaining approval from manager and frontend lead

**Snowflake ETL Testing & Integration Platform**
Apr 2025 | Python, Snowflake, Pandas, pytest, Git Integration, Template Method Pattern

Business Problem:
Vendor integration took 2+ weeks per vendor due to no local testing capability, duplicate validation logic, and risk of production data corruption during testing.

Solution:
Built reusable test harness with CSV-based testing, abstract validation framework, and git-connected Snowflake integration enabling code reuse across stored procedures.

Technical Implementation:

- CSV-based test harness with pytest fixtures and automatic cleanup
- Abstract Rule class with Template Method pattern (IsRequiredRule, IsNumberRule, IsDateRule)
- Vectorized pandas operations (359x faster than row-by-row)
- Fixture Factory pattern for consistent test data generation
- Self-researched git-connected Snowflake approach

Business Impact:

- 75% reduction in integration time: 2+ weeks to 2-3 days per vendor
- 5+ vendors integrated using framework
- Zero production impact through local testing
- Serves ops, finance, and product teams with unified shipment visibility

**Snowflake Terraform Provider Migration**
May-Aug 2025 | Terraform, Snowflake, Infrastructure as Code, State Management

Business Problem:
13 repositories running pre-stable Snowflake Terraform provider versions, accumulating 2 years of technical debt. Direct upgrades would fail due to breaking changes.

Solution:
Identified version breakpoints (0.37 → 0.73 → 0.86 → 0.99 → 0.100.0 → 1.0.0 → 2.4.0) and executed phased migration with state management strategy.

Technical Implementation:

- Namespace migration from Snowflake-Labs/snowflake to snowflakedb/snowflake
- Resource type evolution (snowflake_procedure → snowflake_procedure_python)
- Attribute schema updates across all resources
- Guided DevOps through state file modifications

Business Impact:

- 13 repositories migrated to stable release
- Zero downtime with 10+ GB/day pipeline throughput
- 2-year technical debt eliminated
- Unlocked external API integration and in-procedure alerting

**Snowflake-Datadog Monitoring Integration**
Jun-Jul 2025 | Snowflake, Datadog, Terraform, Monitoring

Business Problem:
Default Datadog integration cost $5/day. Legacy monitoring (custom logs + tasks + Looker alerts) cost $1/day and required manual daily review.

Solution:
Analyzed default integration queries, disabled unnecessary features, created cost-optimized warehouse with minimal privilege model.

Technical Implementation:

- Dedicated DATADOG_WH (X-Small, 30-sec auto-suspend, 120-sec statement timeout)
- Minimal database roles (USAGE_VIEWER, OBJECT_VIEWER, GOVERNANCE_VIEWER, etc.)
- RSA key-based service user authentication
- Selective feature enablement for actual use cases

Business Impact:

- 96% cost reduction from default: $5/day → $0.20/day
- 80% cost reduction from legacy: $1/day → $0.20/day
- 24x faster alerting: 2-hour vs next-day notification
- Eliminated manual daily report review

**Looker Dashboard Event Interception System**
Sep 2025 | React, Event-Driven Architecture, Factory Pattern, Provider Pattern

Business Problem:
Users lost dashboard context and filters when drilling down to detailed analytics. Complex navigation patterns reduced analytics engagement.

Solution:
Built event interception system displaying detail dashboards in application-controlled modals while preserving parent context.

Technical Implementation:

- createInterceptableEventHandler factory for any dashboard/event combination
- Centralized payload management with Provider pattern
- Pure function architecture enabling comprehensive testing
- URL parameter control for event interception

Business Impact:

- Zero navigation disruption for drill-down operations
- Automatic filter inheritance from parent dashboard
- 200+ lines of duplicate code eliminated
- Single configuration point for new dashboard types

**HubTrack Profiles API & OPA Authorization**
Sep-Dec 2025 | Java 17, Spring Boot 3.5.7, DynamoDB, OPA, Rego, Testcontainers, REST Assured

Business Problem:
Legacy authorization tool lacked enterprise security practices. No gateway-level authorization for incoming requests.

Solution:
Built RBAC API with DynamoDB single-table design integrated with OPA for gateway-level authorization across entire organization.

Technical Implementation:

- Single-table DynamoDB schema (PROFILE#{oktaId}, ROLE#{name}, RESOURCE_CATEGORY#{name})
- O(1) lookups with <50ms latency (2 queries at ~15-20ms each)
- Strong consistency for authorization queries (no eventual consistency windows)
- Fail-safe Rego policy: default deny, explicit allow
- JWT token extraction from claims
- Repository pattern with swappable implementations
- E2E self-cleaning test suite with Testcontainers

Business Impact:

- Gateway-level authorization for entire organization
- <50ms authorization latency meeting p95 target
- ~$0.30/month DynamoDB cost
- Self-service role management without code changes
- 6 documentation files for team onboarding

### Dubizzle Egypt (2020-2024)

**Pro-Agency Portal**
Jun 2022 - Aug 2023 | Django, Python, React, TypeScript

Business Problem:
Large agencies with 1,000+ ad inventories had no visibility on aggregated performance, no way to distribute work among agents, and no leads tracking.

Solution:
Built owner/agent model with distributed quotas, agency onboarding for bulk migration, and self-service agent invitation system.

Technical Implementation:

- Django/Python backend with React/TypeScript frontend
- Bulk migration system for existing users and ads
- Distributed quota management per agent
- Per-agent leads tracking and performance visibility

Business Impact:

- 85% adoption rate in first 3 months
- Served Egypt and Lebanon markets
- Reduced operations and customer support manual effort
- Improved leads tracking and ads performance visibility

**Telesales Automation Tool**
Jun 2022 - Aug 2023 | Django, Python, Payment Gateway Integration

Business Problem:
After payment, users had to call back agents with reference numbers to apply packages—taking 1 hour to 1 full day.

Solution:
Integrated payment gateway webhooks to trigger automatic package application with zero human interaction.

Business Impact:

- Package application time: 1 hour-1 day → instant
- Zero human interaction post-code generation
- Faster payment cycles improving conversion

**Drop-offs Lead System**
Jun 2022 - Aug 2023 | Django, Python, External Dialer Integration

Business Problem:
Telesales relied on hourly BI reports to identify payment drop-offs. By contact time, users were no longer engaged.

Solution:
Built real-time lead push system to external dialer every 5-15 minutes with configurable timing.

Business Impact:

- Contact time: 1 hour → 5-15 minutes (4-12x faster)
- Reached users while still engaged with platform
- Eliminated manual BI report extraction

**OLX Arabia Android App**
Oct 2020 - Dec 2021 | Android, Kotlin, Analytics, Firebase Distribution, CI/CD

Business Problem:
Fragmented analytics across platforms. Manual 20-minute release process. 4-5 minute analytics event testing.

Solution:
Designed cross-platform analytics module. Automated CI/CD to Firebase. Built logging layer for instant event validation.

Technical Implementation:

- Analytics module design presented to and approved by head of engineering
- Firebase Distribution automation with zero human interaction
- Logging layer with mobile notifications and console logs

Business Impact:

- 10M+ Play Store installs, 260M MAU globally
- Release time: 20 min → 2 min (10x faster)
- Analytics testing: 4-5 min → instant
- Delivered Pay-and-Ship within 1 week of joining

### The D. GmbH (2018-2020)

**CUJU Android App**
May 2018 - May 2020 | Android, Kotlin, Clean Architecture, XMPP, Multi-module, JUnit

Business Problem:
Legacy codebase with large APK, frequent crashes (57% crash-free), and architecture preventing feature development.

Solution:
Complete architecture rewrite using Clean Architecture with multi-module design. Reimplemented chat with XMPP.

Technical Implementation:

- Separate modules: UseCase, Data, Remote, Local, UI
- XMPP protocol for real-time messaging
- API level migration from 16 to 21 with user base analysis

Business Impact:

- 50%+ APK size reduction while adding features
- Crash-free sessions: 57% → 90% in 6 months
- 100% unit test coverage (non-UI layers)

**Events White Label Apps (BYF, The Good Summit)**
May 2018 - May 2020 | Android, Kotlin, Clean Architecture, Multi-module

Business Problem:
Each event required custom app, but building separate apps was time-consuming and maintenance-heavy.

Solution:
Built white-label platform with configuration-driven branding and Clean Architecture.

Business Impact:

- Deployed across multiple events: BYF, The Good Summit
- 100% unit test coverage (non-UI layers)
- Single codebase reduced maintenance overhead

### Vision Valley (2016-2018)

**Letuno Platform**
Oct 2016 - Jan 2017 | Android, MVP Architecture, REST APIs, Indoor Navigation

Business Problem:
Venues needed contextual content delivery based on indoor location with custom branding per venue.

Solution:
Built Android app for multi-tenant location-based content platform using Visual Light Communication (VLC).

Technical Implementation:

- MVP pattern for presentation layer
- Dynamic theming system rendering views based on organization config
- All-pairs shortest path algorithm for indoor navigation (backend)
- Observer, Singleton, Factory, Decorator patterns

Business Impact:

- Showcased at GITEX 2016 & 2017
- Won SAP Innovation Awards 2019
- First product shipped by Vision Valley

**GPASSA Internal Staff App**
Jan 2016 - Apr 2016 | Cordova, Framework7, SharePoint 2013 REST APIs

Business Problem:
GPASSA-UAE staff needed mobile access to SharePoint data but mobile experience was limited.

Solution:
Built cross-platform app with full CRUD operations on SharePoint list data.

Business Impact:

- 80%+ SharePoint list type coverage on mobile
- Eliminated desktop dependency for common operations

**EG Live Exchange Rates**
Nov 2016 | Cordova, Angular 1.x, Web Scraping

Business Problem:
During Egypt's currency flotation, exchange rates varied across banks and changed rapidly.

Solution:
Built real-time aggregator with self-healing system for bank availability.

Business Impact:

- Multi-bank rate aggregation during economic uncertainty
- Zero-maintenance through automatic availability detection

## EDUCATION

**Bachelor of Science in Computer Science**
Ain Shams University, Cairo | Class of 2015

## PUBLICATIONS & SPEAKING

- **What They Don't Teach You at School** — School of Tech | [Video](https://youtube.com/watch?v=RrEMClS0LHY)
- **And Then Google Said: "Let There Be Guidance!"** — Medium | [Article](https://medium.com/the-d/google-android-architecture-components-97f11f8a9638)

## LANGUAGES

- **Arabic:** Native
- **English:** Proficient
