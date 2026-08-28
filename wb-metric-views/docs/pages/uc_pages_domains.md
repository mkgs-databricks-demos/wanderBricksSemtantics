# WanderBricks — UC Pages Domain & Sub-Domain Candidates

Organizational taxonomy for the WanderBricks semantic layer. Domains represent top-level business areas; sub-domains group related metric views, tables, and KPIs within each area. Based on hospitality industry standards (STR, USALI, AHLA) and vacation-rental operational patterns.

---

## Domain Architecture Overview

```
wanderbricks/
├── revenue_management/        ← Pricing, demand, yield
├── operations/                ← Property ops, housekeeping, maintenance
├── guest_experience/          ← Satisfaction, loyalty, reviews
├── distribution/              ← Channels, partnerships, marketing
├── finance/                   ← P&L, cost control, asset value
└── portfolio/                 ← Inventory, market positioning, growth
```

---

## 1. Revenue Management

The commercial engine — how WanderBricks prices, fills, and maximizes yield from available inventory.

### Sub-Domains

| Sub-Domain | Scope | Key Metric Views | Industry Basis |
| --- | --- | --- | --- |
| **Demand & Occupancy** | Room nights sold, occupancy trends, demand forecasting | `mv_bookings_revenue` | STR core metrics (Occupancy, Demand, Supply) |
| **Pricing & Rate Strategy** | ADR, rate plans, dynamic pricing, discounting | `mv_bookings_revenue` | STR ADR, RevPAR; revenue management discipline |
| **Yield Optimization** | RevPAR, TRevPAR, revenue per available night, displacement | `mv_bookings_revenue` | STR RevPAR; yield management as practiced by Marriott, Hilton, Airbnb |
| **Booking Behavior** | Lead time, LOS, pace, cancellations, booking curves | `mv_booking_patterns` | AirDNA/Hostaway demand analytics; STR pickup reports |
| **Ancillary Revenue** | Upsells, fees, experiences, add-ons beyond nightly rate | `mv_bookings_revenue` | TRevPAR concept from USALI; vacation rental fee structures |

### Why This Domain Matters

Revenue management is the single highest-leverage function for vacation rentals. A 1% improvement in RevPAR typically drops straight to the bottom line. Industry leaders (STR, Duetto, Beyond Pricing) all organize their analytics around this domain first.

---

## 2. Operations

The physical execution layer — turning over properties, maintaining assets, and delivering the guest-ready experience.

### Sub-Domains

| Sub-Domain | Scope | Key Metric Views | Industry Basis |
| --- | --- | --- | --- |
| **Housekeeping & Turnover** | Cleaning time, turnover scheduling, quality inspection | `mv_operations` | USALI rooms department; MinPOR industry benchmarks |
| **Maintenance & Asset Care** | Preventive maintenance, repairs, ticket resolution, capex | `mv_operations` | Hotel engineering standards; property preservation metrics |
| **Staffing & Labor** | Labor hours, productivity, scheduling, cost allocation | `mv_operations`, `mv_financial_performance` | STR LPAR/HPOR; hospitality workforce management |
| **Guest Services** | Concierge, communication, issue response, check-in/out | `mv_operations` | Hospitality service delivery standards |
| **Supply & Procurement** | Linens, amenities, consumables, vendor management | `mv_operations` | USALI undistributed operating expenses |

### Why This Domain Matters

Operations is the largest cost center and the primary driver of guest experience quality. In vacation rentals, turnover cost per stay is materially higher than hotels (no permanent staff on-site). Benchmarking MinPOR and HPOR against industry standards reveals staffing inefficiencies immediately.

---

## 3. Guest Experience

The relationship layer — how guests perceive WanderBricks before, during, and after their stay.

### Sub-Domains

| Sub-Domain | Scope | Key Metric Views | Industry Basis |
| --- | --- | --- | --- |
| **Satisfaction & Reviews** | Review scores, GRI, NPS, sentiment analysis | `mv_guest_experience` | Shiji GRI benchmarks; TripAdvisor/Airbnb review ecosystems |
| **Loyalty & Retention** | Repeat guest rate, CLV, membership engagement | `mv_guest_experience` | Hotel loyalty programs (Marriott Bonvoy, Hilton Honors); direct booking strategies |
| **Communication & Responsiveness** | Response time, response rate, pre-arrival engagement | `mv_guest_experience` | Vrbo host standards; Airbnb Superhost criteria |
| **Complaint & Recovery** | Issue taxonomy, resolution time, service recovery effectiveness | `mv_guest_experience` | Service recovery paradox; hospitality service guarantee programs |
| **Guest Segmentation** | Personas, trip purpose, party composition, origin markets | `mv_guest_experience` | Hotel CRM segmentation; STR traveler profiles |

### Why This Domain Matters

Review scores directly impact search ranking and conversion on OTAs. Vrbo research shows 68% of travelers consider reviews "very important" and 56% expect host response within 1 hour. For a brand like WanderBricks, guest experience IS the product — unlike hotels with physical lobbies and staff, the digital experience and communication quality define the brand.

---

## 4. Distribution

The go-to-market layer — where and how WanderBricks reaches travelers and converts demand.

### Sub-Domains

| Sub-Domain | Scope | Key Metric Views | Industry Basis |
| --- | --- | --- | --- |
| **Channel Performance** | Channel mix, revenue share, conversion by channel | `mv_channel_performance` | OTA/direct distribution strategy; Phocuswright channel research |
| **Acquisition Cost** | Commission rates, CPA, marketing spend per booking | `mv_channel_performance` | Hotel distribution cost analysis; net RevPAR concepts |
| **Direct Booking** | Website conversion, email marketing, brand search | `mv_channel_performance` | Direct booking movement; Marriott/Hilton best-price guarantees |
| **Listing & Content** | Listing quality, photo scores, description completeness | `mv_channel_performance` | Airbnb/Vrbo listing optimization; content-to-conversion analytics |
| **Market Positioning** | Comp set analysis, rate parity, market share | `mv_channel_performance` | STR competitive benchmarking (MPI, ARI, RGI) |

### Why This Domain Matters

Distribution cost is the silent margin killer in vacation rentals. OTA commissions (15-20%) vs. direct bookings (3-5% payment processing) create a 10-15% profit swing on identical stays. Understanding channel economics is essential for sustainable growth.

---

## 5. Finance

The profitability layer — translating revenue and operations into owner returns and business health.

### Sub-Domains

| Sub-Domain | Scope | Key Metric Views | Industry Basis |
| --- | --- | --- | --- |
| **Profitability** | GOPPAR, GOP margin, EBITDA, net operating income | `mv_financial_performance` | USALI (Uniform System of Accounts for the Lodging Industry); STR P&L benchmarks |
| **Cost Control** | CPOR, labor %, maintenance %, utility costs | `mv_financial_performance` | USALI departmental accounting; hotel cost benchmarking |
| **Owner Economics** | Owner statements, management fees, net distributions | `mv_financial_performance` | Property management fee structures; owner reporting standards |
| **Budgeting & Forecasting** | Budget vs. actual, forecast accuracy, variance analysis | `mv_financial_performance` | Hotel budgeting cycle (USALI chart of accounts) |
| **Tax & Compliance** | Occupancy tax, tourism levies, regulatory fees | `mv_financial_performance` | Jurisdiction-specific STR tax requirements |

### Why This Domain Matters

GOPPAR is increasingly recognized as the most complete single metric for hospitality profitability (CoStar/STR). Revenue growth without cost discipline is a common trap — this domain ensures WanderBricks measures what actually matters: profit per available room, not just revenue.

---

## 6. Portfolio

The strategic layer — what WanderBricks owns/manages, where it operates, and how the portfolio evolves.

### Sub-Domains

| Sub-Domain | Scope | Key Metric Views | Industry Basis |
| --- | --- | --- | --- |
| **Inventory & Capacity** | Property count, unit types, bed count, capacity, availability | `mv_properties` | STR supply metrics; property management system (PMS) standards |
| **Market & Geography** | Markets served, submarkets, density, expansion targets | `mv_properties` | STR market classification; AirDNA market analytics |
| **Property Quality** | Amenity tiers, condition scoring, guest-ready standards | `mv_properties` | Star rating systems; Airbnb Plus / Vrbo Premier standards |
| **Growth & Pipeline** | New listings, onboarding velocity, churn/attrition | `mv_properties` | Portfolio management; property acquisition pipeline |
| **Competitive Intelligence** | Comp set definition, market share, supply growth | `mv_properties` | STR competitive indices (MPI, ARI, RGI) |

### Why This Domain Matters

The portfolio domain is the foundation — every other metric is denominated against available inventory. Understanding property mix, geographic concentration, and quality distribution is prerequisite to meaningful RevPAR, GOPPAR, or occupancy analysis. Already partially implemented via `mv_properties`.

---

## Cross-Domain Relationships

Domains don't operate in isolation. Key linkages:

```
Portfolio ──defines inventory──► Revenue Management
    │                                   │
    │                                   ▼
    └──────────────────────► Finance (profitability per unit)
                                        ▲
                                        │
Operations ──drives cost──────────────────┘
    │
    └──drives quality──► Guest Experience ──drives conversion──► Distribution
                                                                      │
                                                                      ▼
                                                              Revenue Management
```

| Relationship | Example |
| --- | --- |
| Portfolio → Revenue | Available rooms is the denominator for RevPAR, GOPPAR, TRevPAR |
| Revenue → Finance | Revenue minus costs = GOPPAR; ADR minus CPOR = unit margin |
| Operations → Finance | Labor hours and turnover costs flow into CPOR and labor % |
| Operations → Guest Experience | Cleaning quality and response time drive review scores |
| Guest Experience → Distribution | Higher reviews = better OTA ranking = more organic demand |
| Distribution → Revenue | Channel mix affects realized ADR (commission-adjusted net rate) |
| Finance → Portfolio | Profitability by market informs expansion/contraction decisions |

---

## Domain-to-Metric-View Mapping

| Domain | Primary Metric View(s) | Status |
| --- | --- | --- |
| Revenue Management | `mv_bookings_revenue`, `mv_booking_patterns` | Planned (P1) |
| Operations | `mv_operations` | Planned (P3) |
| Guest Experience | `mv_guest_experience` | Planned (P3) |
| Distribution | `mv_channel_performance` | Planned (P2) |
| Finance | `mv_financial_performance` | Planned (P2) |
| Portfolio | `mv_properties` | Done |

---

## Industry Frameworks Referenced

| Framework | Org | Relevance |
| --- | --- | --- |
| **USALI** (Uniform System of Accounts for the Lodging Industry) | AHLA / HFTP | Standard chart of accounts and departmental P&L structure for hospitality |
| **STR Benchmarking** | CoStar Group (STR) | Industry-standard performance metrics (ADR, RevPAR, Occupancy) and competitive indices |
| **Competitive Indices** (MPI, ARI, RGI) | STR | Market Penetration Index, Average Rate Index, Revenue Generation Index for comp set analysis |
| **GOPPAR Framework** | IDeaS / STR | Profitability-per-room framework going beyond revenue-only metrics |
| **Airbnb/Vrbo Host Standards** | Airbnb, Expedia Group | Platform-specific quality tiers (Superhost, Premier Host) that drive visibility |
| **AirDNA Market Intelligence** | AirDNA | Short-term rental demand, supply, and revenue analytics at market level |
| **Oracle OPERA PMS** | Oracle Hospitality | Property management system data model — guest, reservation, rate, room type |

---

## Naming Conventions

| Layer | Pattern | Example |
| --- | --- | --- |
| Domain | `snake_case`, business area | `revenue_management` |
| Sub-Domain | `snake_case`, specific focus | `pricing_rate_strategy` |
| Metric View | `mv_<subject>` | `mv_bookings_revenue` |
| Source Table | `<schema>.<table>` | `wanderbricks.bookings` |
| Conformed Dimension | `dim_<entity>` | `dim_property`, `dim_date` |
| Fact Table | `fct_<event>` | `fct_reservation`, `fct_transaction` |

---

## Next Steps

1. Validate domain boundaries against actual WanderBricks data sources
2. Map existing `samples.wanderbricks.*` tables to domains/sub-domains
3. Identify data gaps — which sub-domains have no backing tables yet
4. Prioritize metric view creation by domain (Portfolio done → Revenue next)
5. Define conformed dimension tables that span domains
