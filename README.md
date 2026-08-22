# LoyaltyLion (loyaltylion)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

LoyaltyLion is an e-commerce loyalty and rewards platform for Shopify, BigCommerce, and custom storefronts, letting merchants run points, referrals, VIP tiers, and reward programs. Its v2 REST API (base `https://api.loyaltylion.com/v2`) is split into an **Admin API** - for moving data in and out of LoyaltyLion, such as retrieving customers and transactions, tracking orders, and adjusting points - and a **Headless API** for building custom shopper-facing loyalty experiences in web, mobile, and POS applications. All endpoints share a documented rate limit of 20 requests per second.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/loyaltylion/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/loyaltylion/refs/heads/main/apis.yml)

## Access Model

LoyaltyLion is a **commercial SaaS platform** (not open source). The API is a platform capability of a paid LoyaltyLion program rather than a separately metered product:

- **Authentication:** Modern access uses a **Program API key** passed as a `Bearer` token in the `Authorization` header, with scoped permissions (for example `read_customers`). Keys are generated per program in the LoyaltyLion admin and cannot be viewed again after creation. OAuth is also offered. A **deprecated token/secret** pair over HTTP Basic auth (RFC 2617) remains supported only until **2027-01-10**.
- **Customer addressing:** Customers are addressed by the `merchant_id` you use in your own platform or e-commerce store.
- **Pricing / plan-gating:** Billing is tied to average **monthly order volume**, not API calls - a Free tier (up to ~400 orders/month), a published Classic tier from **$199/month** (500 orders), and custom-quoted **Advanced** and **Plus** tiers. Full Admin/Headless API access is generally associated with higher tiers; the exact plan-to-API-scope mapping is not fully published and should be confirmed with LoyaltyLion.
- **Async delivery:** There is **no public WebSocket API**. Event-driven delivery is provided by outbound **webhooks** - merchants register callback URLs and LoyaltyLion POSTs loyalty events to them.

## Tags

- Loyalty
- Rewards
- E-commerce
- Points
- Shopify
- Retention

## Timestamps

- **Created:** 2026-07-10
- **Modified:** 2026-07-10

## APIs

### LoyaltyLion Customers API

List and update loyalty customers, read their points balances, tiers, and referral details, and pull the point transactions for an individual customer. Customers are matched by your platform `merchant_id` and filterable by email and created/updated date ranges with cursor pagination.

- **Human URL:** [https://developers.loyaltylion.com/api-reference/v2/resources/customers/list-customers](https://developers.loyaltylion.com/api-reference/v2/resources/customers/list-customers)
- **Base URL:** `https://api.loyaltylion.com/v2`

#### Tags

- Customers
- Loyalty
- Profiles

#### Properties

- [Documentation](https://developers.loyaltylion.com/api-reference/introduction)
- [API Reference](https://developers.loyaltylion.com/api-reference/v2/resources/customers/list-customers)
- [OpenAPI](openapi/loyaltylion-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/loyaltylion.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/loyaltylion.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### LoyaltyLion Activities API

Record customer activities against built-in or custom loyalty rules - signups, clickthroughs, social actions, reviews, and more - to award points. Create, list, and update activities, attaching customer identity, properties, and referral tracking (IP address and user agent).

- **Human URL:** [https://developers.loyaltylion.com/api-reference/v2/resources/activities/create-activity](https://developers.loyaltylion.com/api-reference/v2/resources/activities/create-activity)
- **Base URL:** `https://api.loyaltylion.com/v2`

#### Tags

- Activities
- Rules
- Engagement

#### Properties

- [API Reference](https://developers.loyaltylion.com/api-reference/v2/resources/activities/create-activity)
- [OpenAPI](openapi/loyaltylion-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/loyaltylion.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/loyaltylion.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### LoyaltyLion Points API

Manually add or remove points from a customer's balance with an optional shopper-visible reason, and list the immutable point transactions that record every addition or removal across the program or for a single customer.

- **Human URL:** [https://developers.loyaltylion.com/api-reference/v2/resources/transactions/list-transactions](https://developers.loyaltylion.com/api-reference/v2/resources/transactions/list-transactions)
- **Base URL:** `https://api.loyaltylion.com/v2`

#### Tags

- Points
- Transactions
- Balances

#### Properties

- [API Reference](https://developers.loyaltylion.com/api-reference/v2/resources/customers/add-points)
- [OpenAPI](openapi/loyaltylion-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/loyaltylion.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/loyaltylion.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### LoyaltyLion Rewards API

List the rewards a given customer can currently claim - filtered by site and country - and enable or disable rewards in the program catalog to control which incentives shoppers can spend their points on.

- **Human URL:** [https://developers.loyaltylion.com/api-reference/v2/resources/customers/rewards/list-available-rewards](https://developers.loyaltylion.com/api-reference/v2/resources/customers/rewards/list-available-rewards)
- **Base URL:** `https://api.loyaltylion.com/v2`

#### Tags

- Rewards
- Catalog
- Incentives

#### Properties

- [API Reference](https://developers.loyaltylion.com/api-reference/v2/resources/customers/rewards/list-available-rewards)
- [OpenAPI](openapi/loyaltylion-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/loyaltylion.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/loyaltylion.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### LoyaltyLion Redemptions API

Redeem a reward on behalf of a customer - spending their points to create a claimed reward - and refund a previously claimed reward to return the points, supporting multipliers, variants, and headless session attribution.

- **Human URL:** [https://developers.loyaltylion.com/api-reference/v2/resources/customers/rewards/redeem-reward](https://developers.loyaltylion.com/api-reference/v2/resources/customers/rewards/redeem-reward)
- **Base URL:** `https://api.loyaltylion.com/v2`

#### Tags

- Redemptions
- Rewards
- Claims

#### Properties

- [API Reference](https://developers.loyaltylion.com/api-reference/v2/resources/customers/rewards/redeem-reward)
- [OpenAPI](openapi/loyaltylion-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/loyaltylion.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/loyaltylion.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/loyaltylion)
- [Website](https://loyaltylion.com)
- [Documentation](https://developers.loyaltylion.com)
- [Plans](plans/loyaltylion-plans-pricing.yml)
- [Rate Limits](rate-limits/loyaltylion-rate-limits.yml)
- [Fin Ops](finops/loyaltylion-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
