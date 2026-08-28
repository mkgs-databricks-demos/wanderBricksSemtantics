# WanderBricks — UC Pages Metric View Candidates

Reference document for building the WanderBricks semantic layer. Each section represents a candidate metric view with its industry-standard KPIs, recommended dimensions, and rationale for inclusion.

---

## 1. Revenue & Demand — `mv_bookings_revenue`

Source: bookings/reservations fact table

### Measures

| Metric | Formula | Rationale |
| --- | --- | --- |
| Occupancy Rate | rooms_sold / rooms_available | Foundational demand signal — every downstream metric depends on it (STR standard) |
| Average Daily Rate (ADR) | room_revenue / rooms_sold | Shows pricing power per sold night; critical for rate strategy |
| RevPAR | room_revenue / rooms_available (or ADR × Occupancy) | Industry gold standard — combines pricing and fill into one productivity metric |
| TRevPAR | total_revenue / rooms_available | Captures cleaning fees, upsells, pet fees, and experiences beyond nightly rate |
| Revenue per Available Night | rental_revenue / available_nights | Vacation-rental adaptation of RevPAR for multi-night stays |
| Room Nights Sold (Demand) | count(occupied room-nights) | Raw demand volume used by STR for market benchmarking |
| Gross Booking Value (GBV) | sum(total_booking_amount) | Portfolio-level topline before refunds/fees — used by PM platforms |

### Dimensions

| Dimension | Why |
| --- | --- |
| stay_date | Revenue attribution by calendar date |
| property_id / property_type | Per-unit and portfolio-level analysis |
| booking_channel | OTA vs. direct margin analysis |
| market_segment | Leisure vs. corporate vs. group demand mix |
| rate_plan | Promo/discount impact on ADR |
| season | High/shoulder/low demand patterns |
| geography | Destination market and submarket comparison |

---

## 2. Booking Patterns — `mv_booking_patterns`

Source: reservations table

### Measures

| Metric | Formula | Rationale |
| --- | --- | --- |
| Average Booking Lead Time | avg(checkin_date - booking_date) | Drives pricing windows and early-bird vs. last-minute strategy |
| Average Length of Stay (ALOS) | sum(nights) / count(stays) | Shapes minimum-stay rules, cleaning schedules, and revenue per booking |
| Booking Pace | cumulative reservations for a future period over time | Forward-looking demand signal for yield management |
| Cancellation Rate | cancelled_bookings / total_bookings | Affects realized occupancy and cash flow forecasting |
| Turnover Rate | check_ins / time_period | More turnovers = more cleaning/inspection labor cost |
| Direct Booking % | direct_bookings / total_bookings | Higher direct = lower commission = better margins |
| Lost/Unrealized Revenue | revenue missed from gaps or pricing decisions | Surfaces yield management improvement opportunities |

### Dimensions

| Dimension | Why |
| --- | --- |
| booking_date | Pace and pickup analysis |
| lead_time_bucket | 0-7d, 8-30d, 31-90d, 90d+ segmentation |
| length_of_stay_bucket | 1-2n, 3-6n, 7n+ patterns |
| booking_channel | Channel-specific booking behavior |
| cancellation_reason | Root-cause analysis for lost demand |
| day_of_week | Weekday vs. weekend demand shape |
| season | Seasonality in booking behavior |

---

## 3. Profitability & Cost — `mv_financial_performance`

Source: P&L / operating cost tables

### Measures

| Metric | Formula | Rationale |
| --- | --- | --- |
| GOPPAR | gross_operating_profit / available_rooms | True profitability per unit — shows if revenue gains become profit |
| GOP Margin | gross_operating_profit / total_revenue | Profitability % — normalizes across property sizes |
| Cost per Occupied Room (CPOR) | operating_costs / rooms_sold | Critical for VRs where cleaning/turnover costs vary wildly |
| Labor Cost % | labor_cost / total_revenue | Largest controllable expense; staffing alignment with demand |
| Labor Cost per Available Room (LPAR) | labor_cost / available_rooms | Labor intensity on an inventory basis (STR P&L standard) |
| Maintenance Cost per Unit | maintenance_expense / available_rooms | Surfaces deferred maintenance risk and seasonal cost spikes |
| Maintenance Cost % | maintenance_expense / total_revenue | Asset preservation relative to revenue generation |
| EBITDA per Available Room | ebitda / available_rooms | Profitability normalized by inventory size |

### Dimensions

| Dimension | Why |
| --- | --- |
| property_id / property_type | Unit-level cost comparison |
| cost_category | Housekeeping, maintenance, labor, utilities, supplies |
| month / quarter | Seasonal cost patterns |
| managed_vs_owner | Self-managed vs. outsourced cost comparison |
| geography | Regional cost variation |

---

## 4. Guest Experience & Loyalty — `mv_guest_experience`

Source: reviews, surveys, guest profiles

### Measures

| Metric | Formula | Rationale |
| --- | --- | --- |
| Net Promoter Score (NPS) | % promoters - % detractors | Industry-standard loyalty predictor; hotel avg \~17, best-in-class \~57 |
| Average Review Score | avg(rating) across platforms | 68% of travelers consider verified reviews "very important" for booking |
| Guest Review Index (GRI) | composite review score (global benchmark: 87.3%) | Standardized satisfaction composite used in industry benchmarking |
| Repeat Guest Rate | returning_guests / total_guests | Core retention signal — best tracked against own historical baseline |
| Response Time | avg(time_to_respond) | 56% of guests expect response within 1 hour if something goes wrong |
| Response Rate | responses_sent / inquiries_received | Conversion driver — faster response = higher booking conversion |
| Complaint Resolution Rate | resolved_complaints / total_complaints | Biggest lever for satisfaction and loyalty |
| Guest Lifetime Value (CLV) | revenue per guest over relationship lifetime | Justifies direct-booking investment and loyalty programs |

### Dimensions

| Dimension | Why |
| --- | --- |
| review_platform | Airbnb, Vrbo, Google, direct — scores differ by platform |
| property_id / property_type | Property-level quality tracking |
| stay_type | Solo, family, business — different expectations |
| loyalty_tier | Enrolled vs. non-enrolled guest behavior |
| guest_origin | Domestic vs. international satisfaction patterns |
| review_category | Cleanliness, communication, accuracy, location, value |

---

## 5. Channel & Distribution — `mv_channel_performance`

Source: reservations joined with channel/commission data

### Measures

| Metric | Formula | Rationale |
| --- | --- | --- |
| Channel Mix % | bookings_by_channel / total_bookings | Drives acquisition cost analysis — OTA vs. direct margin impact |
| Channel Revenue Share | revenue_by_channel / total_revenue | Revenue concentration risk per channel |
| Commission Cost | sum(commission_paid) | True cost of OTA distribution |
| Net Revenue per Channel | revenue - commission - fees per channel | Profitability by acquisition source |
| Conversion Rate | bookings / inquiries or views per channel | Channel effectiveness beyond volume |
| Channel ADR | channel_revenue / channel_rooms_sold | Pricing power varies by distribution channel |

### Dimensions

| Dimension | Why |
| --- | --- |
| channel | Airbnb, Vrbo, Booking.com, direct web, agency, etc. |
| property_id / property_type | Channel preference by property segment |
| booking_date | Channel mix shifts over time |
| season | Seasonal channel behavior |
| market_segment | Business vs. leisure channel preferences |
| device | Mobile vs. desktop conversion differences |

---

## 6. Operations & Housekeeping — `mv_operations`

Source: housekeeping/maintenance/task management tables

### Measures

| Metric | Formula | Rationale |
| --- | --- | --- |
| Minutes per Occupied Room (MinPOR) | housekeeping_minutes / rooms_cleaned | Industry-standard housekeeping productivity metric |
| Labor Hours per Occupied Room (HPOR) | labor_hours / rooms_sold | Operational efficiency independent of wage rates |
| Turnovers per Day | count(turnovers) / days | Operational load indicator for staffing |
| Maintenance Tickets Open | count(open_tickets) | Property condition and guest-readiness signal |
| Avg Time to Resolve | avg(resolved_date - created_date) | Maintenance responsiveness |
| Inspection Pass Rate | passed_inspections / total_inspections | Quality control for guest-ready units |

### Dimensions

| Dimension | Why |
| --- | --- |
| property_id / property_type | Unit-level ops comparison |
| task_type | Cleaning, inspection, maintenance, restocking |
| staff_member / team | Productivity and load balancing |
| day_of_week | Weekend turnover spikes |
| urgency / priority | Triaging operational workload |

---

## 7. Property Inventory (existing) — `mv_properties`

Source: `samples.wanderbricks.properties`

**Status:** Already implemented.

### Current Measures
* Total Properties (count)
* Avg Base Price
* Total Guest Capacity

### Current Dimensions
* Property Type
* Bedrooms
* Bathrooms
* Listed Date

### Recommended Additions
* **Dimensions:** geography/market, amenity tier, pet-friendly flag, accessibility, status (active/inactive)
* **Measures:** avg bedrooms, median base price, properties added (period), utilization rate (if joined with bookings)

---

## Recommended Dimensional Standards (Conformed)

These dimensions should be consistent across all metric views:

| Conformed Dimension | Description | Used In |
| --- | --- | --- |
| Date (role-playing) | Booking date, stay date, check-in, check-out, cancel date | All |
| Property | Type, location, brand tier, unit count | All |
| Geography | Destination market, submarket, guest origin | Revenue, Bookings, Channel |
| Market Segment | Leisure, corporate, group, extended stay | Revenue, Bookings, Channel |
| Booking Channel | Airbnb, Vrbo, direct, OTA, agency | Bookings, Channel, Revenue |
| Guest Type | Solo, family, business, first-time/returning | Experience, Bookings |
| Rate Plan / Price Tier | Standard, promo, seasonal, discounted | Revenue, Bookings |
| Season | High, shoulder, low, holiday, event | All |
| Room/Unit Type | Bedrooms, capacity, view, amenity tier | Properties, Revenue, Ops |
| Loyalty Tier | Enrolled/not, tier level | Experience, Revenue |
| Stay Length Bucket | 1-2n, 3-6n, 7n+, extended | Bookings, Revenue |

---

## Implementation Priority

| Priority | Metric View | Depends On | Business Value |
| --- | --- | --- | --- |
| Done | `mv_properties` | properties table | Inventory baseline |
| P1 | `mv_bookings_revenue` | bookings + properties | Core revenue visibility — RevPAR, ADR, Occupancy |
| P1 | `mv_booking_patterns` | bookings | Demand forecasting and yield management |
| P2 | `mv_financial_performance` | P&L / cost tables | Profitability — GOPPAR, CPOR, labor efficiency |
| P2 | `mv_channel_performance` | bookings + channel data | Distribution cost optimization |
| P3 | `mv_guest_experience` | reviews + guest profiles | Loyalty, retention, and brand health |
| P3 | `mv_operations` | housekeeping/maintenance | Operational efficiency and quality control |

---

## Sources

* [STR (Smith Travel Research) — Glossary & P&L Reporting Guidelines](https://str.com)
* [CoStar — GOPPAR & RevPAR Definitions](https://www.costar.com/products/str-benchmark/resources/data-insights-blog/what-goppar-how-can-it-benefit-your-hotels)
* [Hostaway — Vacation Rental KPIs & Glossary](https://www.hostaway.com/blog/airbnb-vacation-rental-kpis/)
* [Hostfully — Vacation Rental KPIs](https://www.hostfully.com/blog/vacation-rental-kpis/)
* [AirDNA — Short-Term Rental Analytics](https://www.airdna.co/blog/how-to-analyze-a-short-term-rental)
* [Guesty — Industry Report 2025](https://www.guesty.com/wp-content/uploads/2025/09/Industry-Report-2025-V1.pdf)
* [Shiji — Q2 2026 Guest Experience Benchmark](https://www.hospitalitynet.org/news/4133543)
* [Vrbo — Quality & Trust Research 2026](https://www.hospitalitynet.org/news/4133733)
* [Hospitality Net — Tools & Data for Decision Making](https://www.hospitalitynet.org/opinion/4126467)
* [Databricks — Dimensional Modeling Best Practices](https://learn.microsoft.com/azure/databricks/ldp/best-practices/dimensional-modeling)
