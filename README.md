# Market Opportunity Analytics for Industrial B2B Services in Mexico

## A Municipal Prioritization Model for Nearshoring-Related Business Opportunities

---

## 1. Executive Summary

This project develops a municipal-level analytical framework to identify potential market opportunities for industrial B2B services in Mexico.

The model is built around a simple business logic: industrial B2B opportunities are more likely to emerge where there is strong manufacturing activity but limited local availability of scaled B2B service providers.

The objective is not to predict nearshoring investment causally. Instead, the project builds a territorial prioritization model that combines manufacturing demand, general B2B service supply, and scaled B2B capacity into a final municipal opportunity score.

The final analytical output is the **Final Opportunity Score Base**, which ranks municipalities by their potential industrial B2B opportunity gap and classifies them into interpretable market profiles.

---

## 2. Data Pipeline and Analytical Base

The project follows a staged data pipeline:

```text
Municipal Industrial-B2B Integrated Panel
        ↓
Complete-Case Modeling Base
        ↓
Final Opportunity Score Base
```

### 2.1 Municipal Industrial-B2B Integrated Panel

The first analytical layer combines municipal manufacturing indicators with DENUE-based B2B service supply indicators.

This integrated panel is not yet the final scoring base. It is the raw analytical input used to connect two sides of the market:

- manufacturing activity, interpreted as potential demand for industrial B2B services;
- local B2B service supply, interpreted as the existing support ecosystem.

### 2.2 Complete-Case Modeling Base

The **Complete-Case Modeling Base** is the cleaned modeling dataset used to estimate the scores.

Main input file:

```text
data/processed/modeling_base/08_modeling_base_complete_cases.csv
```

Unit of observation:

```text
year × municipality
```

Years included:

```text
2018 and 2023
```

### 2.3 Final Opportunity Score Base

The final analytical output is the **Final Opportunity Score Base**.

Main output file:

```text
data/processed/modeling_base/final_scores/01_municipality_industrial_b2b_opportunity_scores.csv
```

This base contains:

- municipal identifiers;
- manufacturing demand indicators;
- B2B supply indicators;
- B2B size-structure indicators;
- industrial demand score;
- general B2B supply score;
- scaled B2B supply score;
- final opportunity score;
- opportunity rank;
- opportunity category;
- opportunity subtype.

The **Final Opportunity Score Base** is the main working file for maps, rankings, reporting, clustering, and portfolio outputs.

---

## 3. Conceptual Framework: Demand, Supply, and the Opportunity Gap

The project is based on a demand-supply gap logic.

A municipality with a large manufacturing base may generate demand for logistics, technical services, maintenance, professional services, business support, and operational support.

However, high industrial activity alone does not automatically imply a market opportunity. If the municipality already has a strong and scaled B2B service ecosystem, it may represent a consolidated industrial hub rather than an underserved opportunity.

The opportunity gap emerges when strong industrial demand coexists with weak scaled B2B supply.

```text
High industrial demand
        +
Low scaled B2B supply
        =
Potential industrial B2B opportunity gap
```

A simplified interpretation matrix is:

| Industrial demand | Scaled B2B supply | Interpretation |
|---|---|---|
| High | Low | Potential industrial B2B opportunity gap |
| High | High | Industrial ecosystem hub |
| Low | Low | Lower initial priority |
| Low | High | Service hub with lower industrial demand |

This framework separates industrial strength from market opportunity. The project does not simply rank the largest industrial municipalities. It identifies municipalities where industrial activity appears relatively strong compared with the local availability of scaled B2B services.

---

## 4. Industrial Demand Score

### 4.1 Conceptual Motivation

The industrial demand score measures the relative strength of the municipal manufacturing base.

The underlying assumption is that municipalities with more manufacturing establishments, employment, value added, income, and investment are more likely to generate demand for industrial B2B services.

This demand is not observed directly. It is proxied through manufacturing activity.

### 4.2 Variables Used

| Variable | Interpretation |
|---|---|
| `total_manufacturing_establishments` | Number of potential industrial clients or operating units |
| `total_manufacturing_employment` | Labor scale and operational complexity |
| `total_manufacturing_value_added` | Economic and productive relevance |
| `total_manufacturing_income` | Scale of manufacturing market activity |
| `total_manufacturing_investment` | Capital intensity and productive commitment |

### 4.3 Normalization and Weighting Logic

Each component is transformed into an annual percentile rank. This allows municipalities to be compared within the same year.

The score is calculated as:

```text
industrial_demand_score =
0.25 × P(total_manufacturing_establishments)
+ 0.20 × P(total_manufacturing_employment)
+ 0.25 × P(total_manufacturing_value_added)
+ 0.20 × P(total_manufacturing_income)
+ 0.10 × P(total_manufacturing_investment)
```

Where:

```text
P(x) = annual percentile rank of variable x
```

The score gives relatively high weight to manufacturing establishments because B2B demand depends not only on the size of industrial employment, but also on the number of potential firms or operating units that may require services.

### 4.4 Interpretation

A high `industrial_demand_score` indicates a municipality with a strong relative manufacturing base.

It should be interpreted as potential industrial demand for B2B services, not as direct observed demand or confirmed purchasing behavior.

---

## 5. General B2B Supply Score

### 5.1 Conceptual Motivation

The general B2B supply score measures the presence and diversity of the local B2B service ecosystem.

This score answers:

```text
Does the municipality have a local ecosystem of services that can support industrial activity?
```

It does not yet answer whether those services have enough operational scale.

### 5.2 Variables Used

| Variable | Interpretation |
|---|---|
| `denue_logistics_storage_establishments` | Logistics, transport, and storage services |
| `denue_professional_technical_establishments` | Professional, technical, consulting, and specialized services |
| `denue_business_support_establishments` | Operational and administrative support services |
| `denue_b2b_support_scian_classes` | Diversity of B2B service activities |

### 5.3 Normalization and Weighting Logic

Each component is transformed into an annual percentile rank.

The score is calculated as:

```text
b2b_supply_score =
0.35 × P(denue_logistics_storage_establishments)
+ 0.25 × P(denue_professional_technical_establishments)
+ 0.20 × P(denue_business_support_establishments)
+ 0.20 × P(denue_b2b_support_scian_classes)
```

Logistics receives the highest weight because, in a nearshoring-related industrial context, transportation, storage, and connectivity services are especially relevant for production networks and supply chains.

### 5.4 Avoiding Double Counting

The variable `denue_b2b_support_establishments` is not included in the composite score because it aggregates the underlying B2B components.

Including both the total and its components would double-count the same structure.

Instead, `denue_b2b_support_establishments` is retained as a descriptive variable for interpretation.

### 5.5 Interpretation

A high `b2b_supply_score` indicates that the municipality has a relatively developed B2B service ecosystem.

However, this score does not distinguish whether the ecosystem is mostly composed of micro and small establishments or whether it includes medium and large service providers.

---

## 6. Scaled B2B Supply Score

### 6.1 Why B2B Presence Is Different from B2B Scale

A municipality may have many B2B establishments, but if most are micro or small units, the ecosystem may be fragmented.

The project therefore separates:

```text
B2B presence
```

from:

```text
B2B scaled capacity
```

This distinction matters because serving industrial clients may require administrative capacity, operational reliability, specialized staff, financial strength, certifications, or the ability to handle larger contracts.

### 6.2 Why Micro and Small Establishments Are Not Treated as Equivalent to Medium or Large Firms

Micro and small establishments are not treated as additive equivalents of medium or large firms.

For example, ten micro establishments do not necessarily have the same capacity as one medium-sized establishment. They may not share management, financing, certifications, operational systems, or the ability to coordinate large service contracts.

For that reason, micro and small establishments are retained for interpretation, but they are not included in the scaled B2B supply proxy.

### 6.3 Scaled Capacity Proxy

The scaled B2B supply proxy is based on medium and large B2B establishments:

```text
b2b_scaled_capacity_proxy =
65.5 × denue_b2b_medium_establishments
+ 150 × denue_b2b_large_establishments
```

The value `65.5` is the midpoint of the medium-size employment range:

```text
(31 + 100) / 2 = 65.5
```

The value `150` is used as a conservative reference value for large establishments, because the large-employment interval is open-ended.

### 6.4 Zero-Adjusted Percentile Normalization

The first version of the percentile normalization assigned an artificial average percentile to municipalities with zero scaled B2B capacity because many municipalities were tied at zero.

To avoid this, the final version uses a zero-adjusted rule:

```text
if b2b_scaled_capacity_proxy == 0:
    scaled_b2b_supply_percentile = 0

if b2b_scaled_capacity_proxy > 0:
    scaled_b2b_supply_percentile =
    annual percentile rank among municipalities with positive scaled B2B capacity
```

This adjustment makes the interpretation more direct:

```text
zero scaled capacity = zero scaled B2B supply percentile
```

### 6.5 Interpretation

A high `scaled_b2b_supply_percentile` indicates that a municipality has relatively strong B2B providers with medium or large establishment size.

A low value indicates weak or absent scaled B2B supply.

---

## 7. Final Industrial B2B Opportunity Score

### 7.1 Formula

The final opportunity score combines industrial demand and scaled B2B supply:

```text
industrial_b2b_opportunity_score =
industrial_demand_percentile × (1 - scaled_b2b_supply_percentile)
```

### 7.2 Interpretation

The score increases when:

```text
industrial_demand_percentile is high
```

and:

```text
scaled_b2b_supply_percentile is low
```

In simple terms:

```text
Higher score = stronger industrial demand + weaker scaled B2B supply
```

### 7.3 What a High Score Means

A high score suggests that a municipality may have a potential industrial B2B opportunity gap.

It indicates that manufacturing activity is relatively strong, while the local availability of scaled B2B providers appears relatively weak.

### 7.4 What a High Score Does Not Mean

A high score does not mean:

- confirmed unmet demand;
- causal evidence of nearshoring;
- guaranteed business success;
- future investment prediction;
- a full site-selection recommendation.

The score is a prioritization tool. It identifies municipalities that may deserve deeper business analysis.

---

## 8. Opportunity Categories and Subtypes

### 8.1 Main Opportunity Categories

| Category | Interpretation |
|---|---|
| `Top priority opportunity` | Very high industrial demand and low scaled B2B supply |
| `Priority opportunity` | High industrial demand and low scaled B2B supply |
| `Developing industrial market` | Medium/high industrial demand with limited scaled B2B supply |
| `Industrial ecosystem hub` | Strong industrial demand and strong scaled B2B supply |
| `Service hub, lower industrial demand` | Strong B2B supply but lower industrial demand |
| `Lower initial priority` | Lower industrial demand and lower scaled B2B supply |
| `Intermediate / monitor` | Residual or borderline cases |

### 8.2 Opportunity Subtypes

| Subtype | Interpretation |
|---|---|
| `Atomized B2B opportunity` | B2B exists, but appears micro/small and not scaled |
| `Limited scaled B2B opportunity` | Some B2B exists, but general and scaled supply are limited |
| `Broad B2B gap` | No observable B2B support and no scaled B2B |
| `Low scaled B2B opportunity` | Some scaled B2B exists, but remains weak |
| `Mixed opportunity case` | Intermediate opportunity profile |
| `Not opportunity subtype` | Municipality is not classified as an opportunity case |

### 8.3 Why Atomized B2B Opportunity Is the Main Narrative

The strongest business narrative is not necessarily the absence of any B2B services.

The most interesting case is:

```text
high industrial demand
+
existing B2B ecosystem
+
no observable scaled B2B supply
```

This is classified as:

```text
Atomized B2B opportunity
```

This subtype suggests that the municipality may already have service activity, but the ecosystem appears fragmented or concentrated in micro and small establishments.

That makes it more analytically credible than a broad gap with no observable B2B activity, which may require additional validation.

---

## 9. Main Outputs

The final outputs are stored in:

```text
data/processed/modeling_base/final_scores/
```

Main files:

| File | Description |
|---|---|
| `01_municipality_industrial_b2b_opportunity_scores.csv` | Final Opportunity Score Base |
| `01_municipality_industrial_b2b_opportunity_scores.parquet` | Parquet version of the final base |
| `02_top_opportunity_ranking.csv` | Top municipalities by opportunity score |
| `03_opportunity_category_summary.csv` | Summary by opportunity category |
| `04_opportunity_subtype_summary.csv` | Summary by opportunity subtype |
| `05_scoring_methodology_notes.txt` | Methodological notes |

---

## 10. Preliminary Findings

This section will be expanded after the final maps and tables are produced.

Initial diagnostic results suggest that the absence of scaled B2B supply is common across municipalities. The zero-adjusted normalization was therefore necessary to avoid overstating scaled B2B supply in municipalities with no medium or large B2B establishments.

The preliminary ranking highlights municipalities where industrial demand is strong and scaled B2B supply is weak. Some cases represent atomized B2B ecosystems, while others represent broader gaps that require additional validation.

---

## 11. Limitations

This project is descriptive and prioritization-oriented.

The score should not be interpreted as:

- a causal estimate of nearshoring;
- a forecast of future investment;
- a direct measure of unmet demand;
- a substitute for local market research;
- a complete site-selection model.

Additional variables that could improve the model include:

- IMMEX presence;
- exports;
- foreign direct investment;
- industrial parks;
- road and logistics infrastructure;
- energy availability;
- water availability;
- security;
- labor/talent availability;
- business costs;
- firm-level service provider capacity.

DENUE-based establishment counts are useful for territorial comparison, but they do not measure actual service quality, contract capacity, specialization, or firm revenues.

The scaled B2B supply proxy uses employment-size categories, not exact employment counts. The value used for large establishments is a conservative approximation.

---

## 12. Next Steps

The next steps are:

1. Build national maps of the final opportunity score, categories, and subtypes.
2. Create a short executive report with maps, rankings, and key findings.
3. Validate the top municipalities manually.
4. Develop clustering to segment municipal market profiles.
5. Prepare GitHub-ready documentation, figures, and tables.
6. Build a clean reproducible notebook for the final pipeline.
7. Explore future model extensions using IMMEX, exports, FDI, industrial parks, infrastructure, energy, water, and security indicators.
