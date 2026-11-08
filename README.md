# Awesome Webhook Event Triggers & Subscriptions [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of top Webhook Event Triggers and Subscriptions platforms, Webhooks-as-a-Service (WaaS), event gateways, and developer infrastructure — covering commercial SaaS solutions, self-hosted open-source alternatives, specs, and local development proxies for reliable event delivery and subscription management.
> 
> 🌟 **Star this repository if you find it helpful!** 🌟

---

## 📑 Table of Contents

- [Sector Overview & Market Dynamics](#-sector-overview--market-dynamics)
- [SaaS / Hosted Platforms](#-saas--hosted-platforms)
  - [SaaS Platforms Comparison Table](#saas-platforms-comparison-table)
  - [Platform Deep Dives](#platform-deep-dives)
- [Open-Source Software](#-open-source-software)
  - [Open-Source Solutions Ranked by GitHub Stars](#open-source-solutions-ranked-by-github-stars)
  - [Open-Source Project Profiles](#open-source-project-profiles)
- [Comparison at a Glance](#-comparison-at-a-glance)
- [Industry Standards & Protocols](#-industry-standards--protocols)
- [Contributing](#-contributing)
- [License](#-license)

---

## 📈 Sector Overview & Market Dynamics

The global market for event-driven integration and Webhooks-as-a-Service (WaaS)—anchored within the Integration Platform as a Service (iPaaS) and event-driven architecture domain—is valued at approximately **$8.4B to $15.9B in 2026** and projected to surpass **$45B by 2035** at a **~18%–24% CAGR**. The sector exhibits a **moderately fragmented** structure transitioning into a multi-tiered landscape: generalist workflow automation and enterprise iPaaS remain dominated by heavyweights (such as Celonis/Make and Zapier), while specialized, developer-first webhook delivery infrastructure (such as Svix, Hookdeck, and Convoy) represents a high-growth, unbundled niche solving queue persistence, HMAC signing security, fanout, and delivery backpressure.

---

## 🟦 SaaS / Hosted Platforms

Commercial, cloud-hosted Webhook Event Trigger, API orchestration, and Subscription infrastructure platforms.

### SaaS Platforms Comparison Table

*Sorted descending by company size (Valuation / Estimated Revenue).*

| Platform | Company Scale (Valuation / Revenue) | Starting Paid Tier Price | Free Tier Limits | Target Use Case |
|---|---|---|---|---|
| **[Make (Celonis)](https://www.make.com)** | Parent Celonis valued at **$13B** (~$771M–$1B+ ARR) | **$10.59 / month** (or $9/mo billed annually) for Core plan (10,000 ops/mo, unlimited active scenarios) | **Free Forever**: 1,000 ops/month, 2 active scenarios, 15-min interval | Visual scenario automation & complex payload transformations |
| **[Zapier](https://zapier.com)** | Valued at **$5.0B** (~$310M ARR) | **$29.99 / month** (or $19.99/mo billed annually) for Professional plan (750 tasks/mo, unlocks Webhooks by Zapier) | **Free Forever**: 100 tasks/month, 2-step single-trigger Zaps, 15-min interval (*Webhooks app requires paid tier or 14-day Pro trial*) | No-code app connections across 7,000+ third-party tools |
| **[Chargebee](https://www.chargebee.com)** | Valued at **$3.5B** (~$200M–$300M ARR) | **$599 / month** (billed annually at $7,188/yr) for Performance plan (up to $100K/mo billing + 0.75% overage) | **Free Forever (Starter)**: Free for first $250,000 lifetime processed billing (0.75% overage thereafter) | Subscription billing lifecycle events & invoice triggers |
| **[Courier](https://www.courier.com)** | ~$57.6M venture funding (~$100M ARR estimate) | **$45.00 / month** for Growth plan (includes higher volume & multi-channel routing) | **Free Forever**: 10,000 notifications/month, unlimited integrations, test sandbox | Multi-channel notification workflows with webhook endpoints |
| **[Pipedream (Workday)](https://pipedream.com)** | Acquired by Workday Nov 2025; previously valued at **~$80M** ($20M+ raised) | **$29.00 / month** for Basic plan (2,000 credits/mo, 10 active workflows) | **Free Forever**: 100 credits/month, 3 active workflows, 3 connected accounts | Developer serverless event-driven code steps & HTTP ingestion |
| **[Svix](https://www.svix.com)** | $17M funding raised (~$1M–$5M ARR estimate) | **$20.00 / month** for Basic plan (includes pay-as-you-go overage & custom domains) | **Free Forever**: 50,000 messages/month, 50 messages/second throughput limit | Enterprise Webhooks-as-a-Service (HMAC, retries, app portal) |
| **[Hookdeck](https://hookdeck.com)** | $5.5M funding raised (<$1M ARR estimate) | **$39.00 / month** for Event Gateway Team plan (Outpost starts at $10 / million events) | **Free Forever**: 10,000 events/month, 3-day retention (Outpost Starter: 50,000 free events/mo) | Inbound webhook proxy, queueing, retries, and Outpost fanout |
| **[Webhook.site](https://webhook.site)** | Bootstrapped indie profitable (~$450K ARR estimate) | **$9.00 / month** (or $15/mo for Pro plan with custom domains & automated forwarders) | **Free Forever**: Instant disposable webhook URL, live request inspector (session-based) | Instant browser-based webhook payload inspection & debugging |
| **[RequestBin](https://requestbin.com)** | Powered by Pipedream infrastructure | **$29.00 / month** (via Pipedream Basic tier to extend bins and persistent endpoints) | **Free Forever**: Public & private bins with 500 requests per bin inspection history | Quick HTTP payload capturing, debugging, and header analysis |

---

### Platform Deep Dives

#### Make Webhooks
* **Type:** Webhook modules within visual automation  
* Make offers Custom Webhook and Webhook Response modules within its scenario builder. Supports payload parsing, branching, rate limiting, and synchronous HTTP responses. More flexible and cost-effective than Zapier for data processing logic and multi-branch handling.
* **Pricing & Free Limits:** Free Forever plan gives 1,000 ops/month; paid Core tier starts at **$10.59/month** (or $9/month billed annually) with 10,000 ops and 1-minute execution intervals.

#### Zapier Webhooks
* **Type:** Webhook triggers within automation  
* Zapier provides "Webhooks by Zapier" with Catch Hook (GET/POST/PUT) and custom webhook responses. Connects webhook-emitting SaaS services to 7,000+ cloud applications with zero code. Lacks dedicated delivery reliability infrastructure (dead-letter queues, standard HMAC signatures, custom endpoint routing).
* **Pricing & Free Limits:** Free plan gives 100 tasks/month for 2-step Zaps (Webhooks app requires the Professional tier starting at **$29.99/month** or a 14-day free trial).

#### Chargebee Webhooks
* **Type:** Billing event triggers from Chargebee  
* Chargebee webhooks notify your application about customer subscription lifecycle events—creation, churn, upgrades, payment failures, and credit notes. **Security note:** Chargebee relies on optional HTTP Basic Auth, secret-in-URL tokens, and static IP allowlists rather than native HMAC signing. Delivery includes 7 retry attempts over 48 hours.
* **Pricing & Free Limits:** Starter plan is free forever for the first **$250,000 in lifetime billing** (0.75% overage fee applies); paid plans start at **$599/month** (billed annually) for up to $100K/month volume.

#### Courier
* **Type:** Notification infrastructure with webhook delivery channel  
* Courier coordinates notifications across Push, Email, SMS, Slack, and Webhook destinations. Features visual routing rules, payload templating, event deduplication, and cross-channel status tracking.
* **Pricing & Free Limits:** Generous Free tier includes **10,000 notifications/month**; paid Growth tier starts at **$45/month**.

#### Pipedream
* **Type:** Developer event source and serverless compute platform  
* Pipedream provides managed HTTP webhook triggers and event sources with code-level Node.js, Python, Go, and Bash steps, secret management, and automatic event queueing.
* **Pricing & Free Limits:** Free tier includes **100 credits/month** and 3 active workflows; paid Basic plan starts at **$29/month** with 2,000 credits and 10 active workflows.

#### Svix
* **Type:** Webhooks-as-a-service with open-core server  
* Svix is an enterprise webhooks-as-a-service platform offering subscriber endpoint administration, HMAC SHA-256 signing, event type catalog management, exponential backoff retries, dead letter queues (DLQs), and customer-facing portal embedding.
* **Pricing & Free Limits:** Free Forever tier provides **50,000 messages/month** and 50 msg/sec throughput; starting paid Basic tier is **$20/month**.

#### Hookdeck
* **Type:** Inbound Event Gateway & Outbound Outpost platform  
* Hookdeck delivers full-lifecycle webhook infrastructure: an Inbound Gateway that ingests, verifies, buffers, and replays webhooks, alongside Outpost, an open-source engine for dispatching outbound events to webhooks, AWS SQS, GCP Pub/Sub, and Kafka.
* **Pricing & Free Limits:** Developer tier is free for **10,000 events/month**; Team Gateway begins at **$39/month**; Outpost includes 50,000 free events/month, then starts at **$10 per million events**.

#### Webhook.site
* **Type:** Instant webhook inspector & automated router  
* Webhook.site generates real-time HTTP endpoints to inspect headers, payloads, query parameters, and multipart files instantly in the browser. Supports custom JavaScript scripting, automatic forwarding, and webhook tunneling.
* **Pricing & Free Limits:** Free indefinitely for basic testing; Pro plans start at **$9/month** (or $15/month for advanced forwarding rules and permanent custom aliases).

#### RequestBin
* **Type:** Request inspection & payload capture (Pipedream-backed)  
* Collects and previews incoming HTTP requests with real-time UI logging and zero configuration. Allows developers to test third-party webhooks before pointing them to production systems.
* **Pricing & Free Limits:** Free forever for up to 500 requests per bin; advanced persistence and workflow automation available through Pipedream starting at **$29/month**.

---

## 🟩 Open-Source Software

Self-hosted, community-driven Webhook Event Trigger, gateway, listener, and relay repositories. All listed software can be deployed directly on your own infrastructure (Docker, Kubernetes, Bare Metal).

### Open-Source Solutions Ranked by GitHub Stars

*Sorted descending by repository star counts.*

1. **[localtunnel](https://github.com/localtunnel/localtunnel)** [![GitHub stars](https://img.shields.io/github/stars/localtunnel/localtunnel?style=social&color=white)](https://github.com/localtunnel/localtunnel/stargazers) — Expose localhost endpoints to public internet URLs for rapid webhook testing and integration development.
2. **[adnanh/webhook](https://github.com/adnanh/webhook)** [![GitHub stars](https://img.shields.io/github/stars/adnanh/webhook?style=social&color=white)](https://github.com/adnanh/webhook/stargazers) — Lightweight, configurable Go server that accepts incoming HTTP webhooks and executes arbitrary shell commands or scripts.
3. **[webhooksite/webhook.site](https://github.com/webhooksite/webhook.site)** [![GitHub stars](https://img.shields.io/github/stars/webhooksite/webhook.site)](https://github.com/webhooksite/webhook.site/stargazers) — Open-source core of Webhook.site; self-hosted web UI and API for capturing, inspecting, and debugging incoming HTTP requests.
4. **[inngest](https://github.com/inngest/inngest)** [![GitHub stars](https://img.shields.io/github/stars/inngest/inngest?style=social&color=white)](https://github.com/inngest/inngest/stargazers) — Event-driven workflow orchestration engine; triggers serverless and background jobs on webhook events with built-in step retries and state management.
5. **[svix-webhooks](https://github.com/svix/svix-webhooks)** [![GitHub stars](https://img.shields.io/github/stars/svix/svix-webhooks?style=social&color=white)](https://github.com/svix/svix-webhooks/stargazers) — High-throughput open-source webhooks service written in Rust with HMAC signing, retries, and customer management APIs.
6. **[convoy](https://github.com/frain-dev/convoy)** [![GitHub stars](https://img.shields.io/github/stars/frain-dev/convoy?style=social&color=white)](https://github.com/frain-dev/convoy/stargazers) — Cloud-native webhook gateway for receiving provider events and delivering millions of outbound webhooks reliably.
7. **[hook0](https://github.com/hook0/hook0)** [![GitHub stars](https://img.shields.io/github/stars/hook0/hook0?style=social&color=white)](https://github.com/hook0/hook0/stargazers) — Full-featured open-source Webhooks-as-a-Service (WaaS) platform written in Rust featuring multi-tenant label routing and UI portal.
8. **[outpost](https://github.com/hookdeck/outpost)** [![GitHub stars](https://img.shields.io/github/stars/hookdeck/outpost?style=social&color=white)](https://github.com/hookdeck/outpost/stargazers) — Hookdeck's open-source Go engine to fan out events to HTTP webhooks, AWS SQS, Kafka, RabbitMQ, and GCP Pub/Sub.
9. **[tarampampam/webhook-tester](https://github.com/tarampampam/webhook-tester)** [![GitHub stars](https://img.shields.io/github/stars/tarampampam/webhook-tester?style=social&color=white)](https://github.com/tarampampam/webhook-tester/stargazers) — Self-hosted Go/React webhook receiver and inspector with WebSocket live updates and custom mock response configurations.
10. **[probot/smee.io](https://github.com/probot/smee.io)** [![GitHub stars](https://img.shields.io/github/stars/probot/smee.io?style=social&color=white)](https://github.com/probot/smee.io/stargazers) — Webhook payload delivery client and proxy service that streams public webhook payloads to localhost via Server-Sent Events (SSE).
11. **[hookdeck-cli](https://github.com/hookdeck/hookdeck-cli)** [![GitHub stars](https://img.shields.io/github/stars/hookdeck/hookdeck-cli?style=social&color=white)](https://github.com/hookdeck/hookdeck-cli/stargazers) — Command-line interface to capture, listen to, and replay webhooks locally without setting up tunneling ports.
12. **[webhookx](https://github.com/webhookx-io/webhookx)** [![GitHub stars](https://img.shields.io/github/stars/webhookx-io/webhookx?style=social&color=white)](https://github.com/webhookx-io/webhookx/stargazers) — High-performance Go webhook gateway featuring declarative YAML/GitOps configuration, WASM plugin transformations, and OpenTelemetry tracing.
13. **[inhooks](https://github.com/didil/inhooks)** [![GitHub stars](https://img.shields.io/github/stars/didil/inhooks?style=social&color=white)](https://github.com/didil/inhooks/stargazers) — Lightweight Go webhook ingestion gateway backed by Redis queues with configurable delays, backoff, and JavaScript transforms.
14. **[dhook](https://github.com/alisheraxmedov/dhook)** [![GitHub stars](https://img.shields.io/github/stars/alisheraxmedov/dhook?style=social&color=white)](https://github.com/alisheraxmedov/dhook/stargazers) — Minimalist, self-hostable webhook relay client written in Dart for proxying webhook events to local environments.

---

### Open-Source Project Profiles

#### [localtunnel](https://github.com/localtunnel/localtunnel) [![GitHub stars](https://img.shields.io/github/stars/localtunnel/localtunnel?style=social&color=white)](https://github.com/localtunnel/localtunnel/stargazers)
* **Stack:** Node.js / JavaScript | **License:** MIT
* **Description:** Exposes local development ports to a publicly accessible HTTPS URL without modifying firewall rules or router configurations. Essential for receiving third-party webhook callbacks (Stripe, GitHub, Shopify) directly on `localhost`.
* **Best for:** Developers needing free, instant tunneling to test webhook listeners locally.

#### [adnanh/webhook](https://github.com/adnanh/webhook) [![GitHub stars](https://img.shields.io/github/stars/adnanh/webhook?style=social&color=white)](https://github.com/adnanh/webhook/stargazers)
* **Stack:** Go | **License:** MIT
* **Description:** A battle-tested HTTP webhook server designed to parse incoming payloads (headers, JSON parameters) and trigger shell scripts, deployments, or local processes based on configurable validation rules.
* **Best for:** Lightweight CI/CD triggers, server automation, and automated deployment hooks on self-managed servers.

#### [webhooksite/webhook.site](https://github.com/webhooksite/webhook.site) [![GitHub stars](https://img.shields.io/github/stars/webhooksite/webhook.site?style=social&color=white)](https://github.com/webhooksite/webhook.site/stargazers)
* **Stack:** PHP (Laravel) / Vue.js | **License:** Proprietary open-source core
* **Description:** Self-hostable edition of Webhook.site for organizations that require on-premise webhook payload debugging, request logging, and custom response mocking behind internal enterprise firewalls.
* **Best for:** Internal QA teams and developers debugging API integrations with sensitive data payloads.

#### [inngest](https://github.com/inngest/inngest) [![GitHub stars](https://img.shields.io/github/stars/inngest/inngest?style=social&color=white)](https://github.com/inngest/inngest/stargazers)
* **Stack:** Go / TypeScript | **License:** Elastic License v2.0
* **Description:** Developer platform for executing durable background workflows triggered by HTTP webhooks or internal application events. Provides step-by-step retry logic, throttling, concurrency limits, and state coordination.
* **Best for:** Teams building resilient, multi-step asynchronous business logic triggered by webhook events.

#### [svix/svix-webhooks](https://github.com/svix/svix-webhooks) [![GitHub stars](https://img.shields.io/github/stars/svix/svix-webhooks?style=social&color=white)](https://github.com/svix/svix-webhooks/stargazers)
* **Stack:** Rust | **License:** MIT / Apache-2.0
* **Description:** The open-source engine powering Svix. Provides complete outbound webhook delivery, standard HMAC signing (`Standard Webhooks` specification), dead letter queue handling, and high-performance delivery tracking.
* **Best for:** SaaS engineering teams seeking an open-core, high-throughput delivery server to send webhooks to their customers.

#### [convoy](https://github.com/frain-dev/convoy) [![GitHub stars](https://img.shields.io/github/stars/frain-dev/convoy?style=social&color=white)](https://github.com/frain-dev/convoy/stargazers)
* **Stack:** Go | **License:** Elastic License v2.0 (ELv2)
* **Description:** Fast, cloud-native webhook gateway supporting both **inbound** webhook reception (one URL per external provider) and **outbound** webhook distribution to end customers. Includes built-in analytics, rate limiting, and customer portal links.
* **Best for:** Engineering organizations looking for a unified gateway to handle inbound provider webhooks alongside outbound customer dispatches.

#### [hook0](https://github.com/hook0/hook0) [![GitHub stars](https://img.shields.io/github/stars/hook0/hook0?style=social&color=white)](https://github.com/hook0/hook0/stargazers)
* **Stack:** Rust | **License:** Server Side Public License (SSPL-1.0)
* **Description:** Open-source Webhooks-as-a-Service with complete feature parity between hosted and self-hosted instances. Features multi-tenant label-based event routing, SDK support across 10+ programming languages, and PostgreSQL / Apache Pulsar backing.
* **Best for:** Multi-tenant SaaS products needing strict EU data residency and fine-grained subscriber filtering.

#### [outpost](https://github.com/hookdeck/outpost) [![GitHub stars](https://img.shields.io/github/stars/hookdeck/outpost?style=social&color=white)](https://github.com/hookdeck/outpost/stargazers)
* **Stack:** Go | **License:** Apache-2.0
* **Description:** Hookdeck's open-source outbound event infrastructure that delivers events across diverse destinations: HTTP webhooks, AWS SQS, Apache Kafka, RabbitMQ, and GCP Pub/Sub. Built with OpenTelemetry instrumentation and topic-level subscriptions.
* **Best for:** Platforms that need to route tenant events directly into message brokers and enterprise customer queues in addition to traditional HTTP webhooks.

#### [tarampampam/webhook-tester](https://github.com/tarampampam/webhook-tester) [![GitHub stars](https://img.shields.io/github/stars/tarampampam/webhook-tester?style=social&color=white)](https://github.com/tarampampam/webhook-tester/stargazers)
* **Stack:** Go / React | **License:** MIT
* **Description:** Lightweight, self-contained Docker container for testing and inspecting webhook requests in real-time. Supports customizable HTTP response bodies/headers, WebSocket UI updates, and Redis or in-memory persistence.
* **Best for:** Local developer sandboxes and CI integration testing requiring a lightweight, reproducible webhook inspector.

#### [probot/smee.io](https://github.com/probot/smee.io) [![GitHub stars](https://img.shields.io/github/stars/probot/smee.io?style=social&color=white)](https://github.com/probot/smee.io/stargazers)
* **Stack:** Node.js | **License:** MIT
* **Description:** Webhook payload delivery and proxy service created by GitHub's Probot team. Channels payloads from public webhook sources over Server-Sent Events (SSE) into local development machines without opening public router ports.
* **Best for:** Developing GitHub Apps, GitHub Actions, and bots locally.

#### [hookdeck-cli](https://github.com/hookdeck/hookdeck-cli) [![GitHub stars](https://img.shields.io/github/stars/hookdeck/hookdeck-cli?style=social&color=white)](https://github.com/hookdeck/hookdeck-cli/stargazers)
* **Stack:** Go | **License:** Apache-2.0
* **Description:** Official terminal client for Hookdeck. Captures, logs, and forwards webhooks directly to local servers, providing permanent URLs, interactive terminal inspection, and one-click replay.
* **Best for:** Developers receiving frequent webhooks locally who need permanent tunnel URLs and request replay.

#### [webhookx](https://github.com/webhookx-io/webhookx) [![GitHub stars](https://img.shields.io/github/stars/webhookx-io/webhookx?style=social&color=white)](https://github.com/webhookx-io/webhookx/stargazers)
* **Stack:** Go | **License:** Apache-2.0 (commercial license for proprietary plugins)
* **Description:** Modern, extensible webhook gateway with declarative GitOps-style configuration. Supports WebAssembly (WASM) payload transformations, rate limiting, HMAC validation, and distributed OpenTelemetry tracing.
* **Best for:** Teams embracing GitOps and declarative infrastructure for managing webhooks at scale.

#### [didil/inhooks](https://github.com/didil/inhooks) [![GitHub stars](https://img.shields.io/github/stars/didil/inhooks?style=social&color=white)](https://github.com/didil/inhooks/stargazers)
* **Stack:** Go | **License:** LGPL-3.0
* **Description:** Inbound webhook forwarder and buffer engine backed by Redis. Provides customizable sink retries, exponential backoffs, delivery delays, and embedded JavaScript execution for payload transformations.
* **Best for:** Developers needing a lightweight buffer queue in front of fragile webhook receiver endpoints.

#### [dhook](https://github.com/alisheraxmedov/dhook) [![GitHub stars](https://img.shields.io/github/stars/alisheraxmedov/dhook?style=social&color=white)](https://github.com/alisheraxmedov/dhook/stargazers)
* **Stack:** Dart | **License:** MIT
* **Description:** Fast, cross-platform webhook relay server and CLI client that pipes external webhook triggers into localhost over isolated channels.
* **Best for:** Developers wanting a minimal, self-hosted relay daemon without third-party SaaS dependencies.

---

## 📊 Comparison at a Glance

| Software / Solution | Ecosystem Type | Primary License | Inbound Gateway | Outbound Delivery | Self-Hosted Ready | Signature & Security |
|---|---|---|---|---|---|---|
| **Make (Celonis)** | Cloud SaaS | Proprietary | ✅ | ✅ | ❌ | API Key / Custom Auth |
| **Zapier** | Cloud SaaS | Proprietary | ✅ | ✅ | ❌ | API Key / Basic Auth |
| **Chargebee** | Billing SaaS | Proprietary | ❌ | ✅ | ❌ | Basic Auth / URL Secret |
| **Courier** | Notification API | Proprietary | ❌ | ✅ | ❌ | HMAC SHA-256 |
| **Pipedream** | Serverless SaaS | Proprietary | ✅ | ✅ | ❌ | OAuth / HMAC / Tokens |
| **Svix** | Webhooks-as-a-Service | Proprietary (MIT Core) | ❌ | ✅ | ⚠️ Open-Core | Standard Webhooks (HMAC) |
| **Hookdeck** | Event Gateway | Proprietary (Apache Outpost) | ✅ | ✅ | ⚠️ Partial (Outpost) | HMAC / Header verification |
| **Webhook.site** | Testing Utility | Mixed (SaaS / Open Source) | ✅ | ✅ | ✅ | Token / Custom Headers |
| **RequestBin** | Testing Utility | Proprietary (Pipedream engine) | ✅ | ❌ | ❌ | Private bin keys |
| **localtunnel** | Tunneling Proxy | MIT | ✅ | ❌ | ✅ | Subdomain tokens |
| **adnanh/webhook** | Command Runner | MIT | ✅ | ❌ | ✅ | Secret parameter validation |
| **Inngest** | Workflow Engine | ELv2 | ✅ | ✅ | ✅ | Event Keys / Signing |
| **Convoy** | Webhook Gateway | ELv2 | ✅ | ✅ | ✅ | `X-Convoy-Signature` |
| **Hook0** | Webhook Platform | SSPL-1.0 | ❌ | ✅ | ✅ | HMAC SHA-256 |
| **Outpost (Hookdeck)** | Event Destination | Apache-2.0 | ❌ | ✅ | ✅ | HMAC / Cloud IAM |
| **Webhook Tester** | Debugger & Mock | MIT | ✅ | ❌ | ✅ | Configurable responses |
| **Smee.io** | SSE Local Relay | MIT | ✅ | ❌ | ✅ | Public channel URLs |
| **WebhookX** | Gateway & Router | Apache-2.0 | ✅ | ✅ | ✅ | HMAC / WASM filters |
| **inhooks** | Redis Queue Proxy | LGPL-3.0 | ✅ | ✅ | ✅ | Custom token checks |
| **dhook** | Local Relay | MIT | ✅ | ❌ | ✅ | Channel tokens |

---

## 🌐 Industry Standards & Protocols

Adopting standard protocols simplifies payload verification and prevents vendor lock-in:

* **[Standard Webhooks](https://github.com/standard-webhooks/standard-webhooks)** [![GitHub stars](https://img.shields.io/github/stars/standard-webhooks/standard-webhooks?style=social&color=white)](https://github.com/standard-webhooks/standard-webhooks/stargazers) — Open standard establishing uniform webhook signature headers (`webhook-id`, `webhook-timestamp`, `webhook-signature`), HMAC SHA-256 verification, and asymmetric signing specifications.
* **[CloudEvents (CNCF)](https://github.com/cloudevents/spec)** [![GitHub stars](https://img.shields.io/github/stars/cloudevents/spec?style=social&color=white)](https://github.com/cloudevents/spec/stargazers) — CNCF open specification describing event data in a common, interoperable format across cloud providers and event-driven architectures.

---

## 🤝 Contributing

Contributions are welcome! If you know of an open-source webhook framework, gateway, relay proxy, or WaaS tool that should be listed here:

1. Fork this repository.
2. Ensure the tool is actively maintained with clear documentation.
3. Add the project with its official GitHub link, live stars badge (`style=social&color=white`), license, and core use case.
4. Submit a Pull Request!

---

## 📄 License

This repository and curated list are licensed under [CC0 1.0 Universal (Public Domain)](LICENSE). Individual listed products and repositories retain their respective licenses.
