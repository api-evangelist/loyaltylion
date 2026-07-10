# LoyaltyLion (loyaltylion)

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
