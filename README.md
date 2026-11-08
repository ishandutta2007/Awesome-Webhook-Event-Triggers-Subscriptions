# Awesome-Webhook-Event-Triggers-Subscriptions

# Awesome Webhook Event Triggers & Subscriptions

> A curated list of top Webhook Event Triggers and Subscriptions platforms — both SaaS/Hosted commercial solutions and open-source alternatives for reliable event delivery, subscription management, and webhook infrastructure.  
> 🌟 Star this repo if you find it useful! 🌟

---

## 📋 Table of Contents

- [SaaS / Hosted Platforms](#-saas--hosted-platforms)
  - [Chargebee Webhooks](#chargebee-webhooks)
  - [Svix](#svix)
  - [Hookdeck](#hookdeck)
  - [Zapier Webhooks](#zapier-webhooks)
  - [Make Webhooks](#make-webhooks)
  - [Pipedream](#pipedream)
  - [Courier](#courier)
  - [Webhook.site](#webhooksite)
  - [RequestBin](#requestbin)
- [Open-Source Software](#-open-source-software)
  - [Hook0](#hook0)
  - [Outpost (Hookdeck)](#outpost-hookdeck)
  - [Convoy](#convoy)
  - [WebhookX](#webhookx)
  - [Webhook Tester (tarampampam)](#webhook-tester-tarampampam)
  - [inhooks](#inhooks)
  - [dhook](#dhook)
- [Comparison at a Glance](#-comparison-at-a-glance)
- [Contributing](#-contributing)

---

## 🟦 SaaS / Hosted Platforms

Commercial, cloud-hosted Webhook Event Trigger and Subscription platforms. These are not open-source but are included as reference points for feature comparison.

### Chargebee Webhooks
**Type:** Billing event triggers from Chargebee  
Chargebee webhooks notify your application about subscription and billing activity — subscription creation, cancellation, payment success/failure, invoice generation. **Critical security note:** Chargebee does **not** support HMAC signing. There is no signature header, no timestamp, and no replay window. Authenticity rests on optional HTTP Basic Auth (off by default), a secret-in-URL pattern, and region-specific IP allowlisting [citation:3]. Payload shape varies by `api_version` (v1/v2), so defensive parsing is essential. Retries follow 7 attempts over roughly two days; the endpoint must return 2xx. Dedupe on the event `id` [citation:3].  
**Best for:** Existing Chargebee customers needing to react to billing events, with awareness that signature verification is unavailable and Basic Auth must be manually enabled.

### Svix
**Type:** Webhooks-as-a-service with open-core server  
Svix is the leading commercial webhooks platform, offering endpoint management, event type catalogs with dot-notation hierarchy, HMAC signing, automatic retries, dead letter queues, delivery logs, and manual replay [citation:1][citation:9]. The core server is MIT-licensed, but the self-hosted version lacks some features of the hosted service; supported on-prem deployment is an Enterprise-plan feature [citation:1]. Funding: $17M raised [citation:1][citation:9].  
**Best for:** SaaS companies wanting a mature webhooks platform with a larger ecosystem, accepting open-core trade-offs if self-hosting.

### Hookdeck
**Type:** Event gateway with webhook proxy and Outpost  
Hookdeck provides an inbound Event Gateway (webhook proxy, queueing, retries, replay) and a separate outbound product, Outpost, for sending webhooks to customers [citation:9][citation:14]. Outpost is Apache-2.0 and self-hostable; the Event Gateway is closed-source [citation:9]. The CLI offers free permanent URLs for local development. Funding: $5.5M raised [citation:9].  
**Best for:** Teams wanting a managed gateway for inbound webhook reliability, with an open-source option for outbound delivery.

### Zapier Webhooks
**Type:** Webhook triggers within automation  
Zapier provides "Webhooks by Zapier" with Catch Hook and POST/GET/PUT actions. Connects webhook-emitting services to 7,000+ apps without code. Lacks dedicated webhook infrastructure features (retries, signing, observability) — it is a lightweight glue layer.

### Make Webhooks
**Type:** Webhook modules within visual automation  
Make offers Custom Webhook and Webhook Response modules within its scenario builder. Supports payload parsing, branching, and synchronous responses. More flexible than Zapier for processing logic but still not a dedicated delivery platform.

### Pipedream
**Type:** Developer event source platform  
Pipedream provides HTTP webhook triggers and event sources with code-first Node.js/Python steps, built-in auth handling, and event history. Suited for developers wanting programmatic control.

### Courier
**Type:** Notification infrastructure with webhook channel  
Courier handles multi-channel notifications (email, SMS, push, chat) and includes webhook as a delivery channel. Provides templating, routing, and delivery tracking across channels. Not a pure webhook platform.

### Webhook.site
**Type:** Instant webhook inspection  
Generates a unique URL for inspecting incoming requests. Free, browser-based, no setup. Limited persistence; no production delivery features. Good for quick debugging.

### RequestBin
**Type:** Request inspection (now Pipedream)  
Creates a unique endpoint for collecting and inspecting HTTP requests. Focused on debugging rather than production delivery.

---

## 🟩 Open-Source Software

Self-hosted, community-driven Webhook Event Trigger and Subscription tools. All listed projects offer source code you can deploy on your own infrastructure.

### Hook0
**Stack:** (Check repository) | **License:** SSPL-1.0  
An open-source webhooks-as-a-service platform with **full feature parity between cloud and self-hosted** [citation:1][citation:8]. Supports outbound webhook delivery with dot-notation event type hierarchy, HMAC signatures, automatic retries with escalating backoff, dead letter handling, delivery logs, manual replay, REST API, and **label-based multi-tenant filtering** for SaaS platforms routing different events to different tenants [citation:1]. SDKs cover JS, Rust, Python, Go, Ruby, PHP, C#, Java, Kotlin, Lua, and Zig. Default deployment uses PostgreSQL for both queueing and storage; high-throughput setups can switch to Apache Pulsar and S3-compatible storage [citation:1]. EU data plane available on every plan [citation:8].  
**Best for:** Teams wanting genuinely open-source (SSPL) webhooks infrastructure with no feature gates, strong multi-tenant routing, and EU data residency.

### Outpost (Hookdeck)
**Stack:** Go | **License:** Apache-2.0  
Open-source outbound event delivery infrastructure for sending webhooks and events to customer-preferred destinations [citation:6][citation:14]. Supports **webhooks (HTTP), AWS SQS, RabbitMQ, GCP Pub/Sub, Amazon EventBridge, and Kafka** as destination types. Features topic-based subscriptions, publish via API or queue, at-least-once delivery, automatic and manual retries, multi-tenant support, a user portal for customers, delivery failure alerts, and OpenTelemetry integration [citation:6]. Managed by Hookdeck with usage-based pricing from $10 per million events [citation:14].  
**Best for:** SaaS platforms wanting to deliver events not just to webhooks but also directly to customer queues, brokers, and event gateways.

### Convoy
**Stack:** Go | **License:** Elastic License v2.0 (ELv2)  
An open-source high-performance webhooks gateway for managing millions of webhooks end-to-end [citation:5][citation:13]. Supports both **incoming projects** (receive webhooks from providers with a unique URL per provider) and **outgoing projects** (publish events from your systems to customers via API) [citation:13]. Features retries, filtering, transformations, portal links, and observability. Uses its own `X-Convoy-Signature` header rather than Standard Webhooks [citation:12]. **License note:** ELv2 is not OSI-approved open source; paid features are gated behind a license key [citation:12].  
**Best for:** Teams needing a unified gateway for both receiving provider webhooks and sending outbound webhooks to customers, with awareness of the ELv2 license.

### WebhookX
**Stack:** Go | **License:** Apache-2.0 (production license required for commercial use)  
An open-source webhook gateway for receiving, validating, transforming, and delivering events at scale [citation:7][citation:15]. Features include Admin API, reliable delivery with automatic retries, fanout to multiple endpoints by event type, rate limiting, **declarative GitOps-oriented configuration**, plugins (WASM transforms, signature verification, event validation, function plugins), OpenTelemetry observability, and HMAC signing via built-in plugin [citation:7]. **Multi-tenancy and secret management require a license**; free production licenses are available for eligible non-commercial use [citation:7]. Requires PostgreSQL and Redis.  
**Best for:** Teams wanting a Go-based, plugin-extensible webhook gateway with declarative configuration and GitOps workflows.

### Webhook Tester (tarampampam)
**Stack:** Go / React | **License:** Open Source (per repository)  
A free, self-hosted alternative to webhook.site and RequestBin. Generates unique URLs for capturing and inspecting HTTP requests. Features customizable response codes/headers/body, WebSocket real-time UI updates, optional ngrok tunneling, three storage drivers (memory, Redis, filesystem), and a lightweight Docker image. Supports pre-defined static webhook URLs via UUID prefixes.  
**Best for:** Developers and teams wanting a self-hosted, privacy-respecting webhook inspector for debugging and testing.

### inhooks
**Stack:** Go | **License:** Open Source (per Go package)  
A lightweight webhook ingestion and forwarding service with configurable flows. Listens for HTTP POST requests on source URLs, saves messages to Redis, then forwards to configured sink URLs with per-sink delay, retry interval, exponential backoff multiplier, and max attempts [citation:2]. Supports JavaScript transforms with configurable timeout. Queue cleanup for done and dead messages is available (disabled by default). Configuration is file-based (`inhooks.yml`); server restart required for config changes [citation:2].  
**Best for:** Teams wanting a simple, config-driven webhook forwarder with per-destination retry control and Redis-backed durability.

### dhook
**Stack:** Dart | **License:** MIT  
A lightweight webhook relay service for forwarding cloud webhooks to local development environments in real-time — a self-hosted alternative to smee.io [citation:10]. Deploy the relay server on any host (Docker Compose provided), then run the CLI agent locally to forward requests to `localhost`. Generates channel IDs for isolated tunnels. Useful for local development when you need a stable public URL without ngrok.  
**Best for:** Developers needing a self-hosted webhook relay for local development with full control over the relay server.

---

## 📊 Comparison at a Glance

| Software | License | Type | Inbound | Outbound | Self-Hosted | Best For |
|----------|---------|------|---------|----------|-------------|----------|
| **Chargebee** | Proprietary | Billing events | ❌ | ✅ | ❌ | Chargebee billing events |
| **Svix** | Proprietary (MIT core) | Webhooks platform | ❌ | ✅ | ⚠️ Open-core | Mature ecosystem + SLA |
| **Hookdeck** | Proprietary | Event gateway | ✅ | ✅ (Outpost) | ⚠️ Outpost only | Managed inbound reliability |
| **Zapier** | Proprietary | Automation glue | ✅ | ✅ | ❌ | No-code app connections |
| **Make** | Proprietary | Automation glue | ✅ | ✅ | ❌ | Visual webhook scenarios |
| **Hook0** | SSPL-1.0 | Webhooks platform | ❌ | ✅ | ✅ Full parity | Open-source + multi-tenant |
| **Outpost** | Apache-2.0 | Event destinations | ❌ | ✅ | ✅ | Multi-destination delivery |
| **Convoy** | ELv2 | Webhook gateway | ✅ | ✅ | ✅ | Unified inbound + outbound |
| **WebhookX** | Apache-2.0 (licensed) | Webhook gateway | ✅ | ✅ | ✅ | Plugin-extensible gateway |
| **Webhook Tester** | Open Source | Testing/inspection | ✅ | ❌ | ✅ | Self-hosted inspector |
| **inhooks** | Open Source | Forwarder | ✅ | ✅ | ✅ | Config-driven forwarding |
| **dhook** | MIT | Local relay | ✅ | ❌ | ✅ (relay) | Local development relay |

---

## 🤝 Contributing

Contributions are welcome! If you know of an open-source Webhook Event Trigger or Subscription tool that should be listed here, please open a pull request with:

- Project name and URL
- Brief description (1–2 sentences)
- Stack and license
- Why it stands out

Please ensure the project is actively maintained (releases within the last 12 months) and genuinely open-source (or clearly note the license if source-available but not OSI-approved, as with Hook0's SSPL and Convoy's ELv2).

---

## 📄 License

This list is released under CC0 1.0 Universal (Public Domain). The software projects listed retain their respective licenses.

---

⭐ **If this list helped you discover a useful tool, please star the repo!** ⭐
