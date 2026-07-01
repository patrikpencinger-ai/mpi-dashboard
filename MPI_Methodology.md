# Market Potential Index (MPI) — Methodology

**Phase 1 · South‑East Europe appliance & electronics markets**
Scope: Croatia, Slovenia, Bosnia & Herzegovina, Hungary, Bulgaria, Serbia, Montenegro, Kosovo, Albania, North Macedonia.
Categories: TV (OLED as premium subset), Refrigerators (multi‑door/side‑by‑side as premium subset), Washing machines, Tumble dryers (incl. combo washer‑dryer), Dishwashers, Microwave ovens, Vacuum cleaners, Room AC (residential), System AC (professional).

---

## 1. The problem it solves

A flat "€ per inhabitant" target is unfair across these markets, because:

- **Buying power differs** — a household in Slovenia (AIC ≈ 86, EU27=100) can afford far more, and more premium, than one in Kosovo (AIC ≈ 39).
- **Household structure differs** — appliances are bought per *household*, and household size ranges from ~2.2 (Bulgaria, Hungary) to 4.33 (Kosovo). Population overstates the number of buying units in large‑household markets.
- **Environment differs** — air‑conditioning demand is driven by climate and tourism, not income; a hot, touristic coast (Croatia, Montenegro, Albania) is a different market from alpine Slovenia.
- **Category maturity differs** — washing machines are saturated everywhere; dishwashers and dryers are still largely first‑purchase markets in the Balkans.

The MPI converts these structural facts into a single, comparable **potential** number per country × category, so that **targets** can be set as fair shares of potential and **actual sales** can be scored as performance *relative to potential* — comparable across countries and sales offices regardless of their size or wealth.

---

## 2. The model

A multiplicative **Cobb‑Douglas / log‑linear** demand model. Every driver enters as a ratio to a regional reference, so each term equals **1.00× at the regional average** and reads as a clean "× / ÷ versus the regional norm".

```
RAW_volume(c,k) = Base(c,k)
                × (AIC_c  / AIC_ref )^β_k          ← buying power
                × (CDD_c  / CDD_ref )^cw_k          ← climate (cooling)
                × (TOUR_c / TOUR_ref)^tw_k          ← tourism / hospitality
                × (URB_c  / URB_ref )^uw_k          ← urbanisation / apartments
                × Share_k(AIC_c)                    ← premium-subset / adoption share (logistic)

RAW_value(c,k)  = RAW_volume(c,k) × ASP(c,k)
ASP(c,k)        = ASP_base_k × (AIC_c/AIC_ref)^aspSens_k × (PLI_c/PLI_ref)^0.5
```

**Why multiplicative:** it is dimensionless, interpretable (each exponent is a constant elasticity), collapses to the base when all exponents are 0, and decomposes cleanly into per‑driver contributions for the transparency table.

### 2.1 Demand base
- **Households** for all residential appliances (one fridge/washer/TV decision per home). Households = population ÷ average household size.
- **Commercial/services building stock** (a relative index) for **System AC** — a B2B category driven by offices, retail and hotels, not households. It is kept on its own base and **excluded from the residential composite** so per‑household and per‑building intensities are never averaged together.

### 2.2 Buying power (β, income elasticity)
Driver = **Actual Individual Consumption (AIC) per capita in PPS** (EU27=100) — what households actually consume, purchasing‑power‑adjusted. Preferred over GDP because it is not distorted by investment/government/external components and correctly handles remittance‑funded consumption (Kosovo, BiH).

| β range | Behaviour | Categories |
|---|---|---|
| 0.35 – 0.50 | Saturated **necessity** — everyone owns one; wealth changes the *mix*, not the unit count | washing machine, basic refrigerator, vacuum, microwave, mainstream TV |
| 1.20 – 1.30 | **Discretionary** — adoption climbs steeply with income | dishwasher, tumble dryer, room AC, system AC |

Over the region's ~2.2× AIC spread, β≈0.4 yields ~1.4× per‑household variation (matching replacement‑driven necessities), while β≈1.3 yields ~3× (matching the real dishwasher/dryer penetration gap between Slovenia and the Western Balkans).

### 2.3 Environmental & structural drivers
- **Climate (cw):** cooling‑degree‑days, dominant for Room AC (cw 0.85) and System AC (0.65). **Negative for dryers (−0.40)** — sunny, dry climates line‑dry outdoors and suppress dryer demand (the one counter‑intuitive sign in the model; do not let an auto‑fit flip it).
- **Tourism (tw):** highest for System AC (0.65, hotels/HoReCa) and meaningful for coastal Room AC (0.25); trivial elsewhere.
- **Urbanisation (uw):** positive for dishwashers and dryers (apartments lack outdoor drying / need the plumbing profile), Room/System AC (heat‑island, offices); slightly **negative** for large multi‑door fridges (don't fit the smallest urban flats).

### 2.4 Premium subsets — no double counting
OLED (of TV) and multi‑door (of fridges) are carved from the parent with an income‑scaling **logistic share**, and they **carry the parent's low β** — so income is applied *once* (via the share), never stacked as a second high elasticity. They are shown separately for premium‑mix targeting and are **excluded from the parent's composite** so no unit is counted twice. Combo washer‑dryers sit inside the dryer line. (Tumble dryer is modelled as its own discretionary category with a single income channel — a high β and **no** extra share logistic.)

### 2.5 Value vs volume
ASP rises with buying power (within‑tier quality ladder, kept deliberately *small* for parent categories since premium mix is already captured by the subset lines) and with the local **price level (PLI)** at half pass‑through. So **value** potential diverges across countries more than **unit** potential — exactly the "€ per inhabitant isn't the same" effect.

### 2.6 Reference & normalisation
References are scope means. Crucially, **shares and the intensity index are reference‑invariant**: the reference enters as a common multiplicative constant that cancels when normalising, so the choice of reference does not bias the comparison. The **intensity index** is each country's RAW/Base divided by the scope's unweighted mean RAW/Base **within that category** → scope average = **100 by construction**, and it is never pooled across categories with different bases.

---

## 3. Outputs

| Output | What it answers | Use |
|---|---|---|
| **Potential share %** (volume & value) | What slice of the region is each country worth? | Split a top‑down target |
| **Intensity index** (per‑household, avg=100) | Is a household here worth more or less than the regional average? | Fair, size‑neutral comparison |
| **Absolute units / €** | How big is the prize? | Sizing — *calibrate the scale by entering real annual market totals per category* |
| **Perf‑abs** = actual ÷ own absolute potential | Is this office over/under‑executing? | **Headline performance — non‑zero‑sum** (one office's result never moves another's) |
| **Perf‑rel** = actual share ÷ potential share | Is this office capturing more than its fair slice? | Secondary; zero‑sum within the scope |
| **Composite country MPI** | Overall attractiveness across residential categories | Portfolio view |

**Performance scale:** 100 = at potential, ≥110 over (green), 90–110 in‑line (amber), <90 under (red). Small‑base / low‑confidence markets are flagged **"thin"** — their score is statistically noisy.

**Target allocation:** `Target_c = TotalScopeTarget_k × PotentialShare_c`. Use as the *starting point* for a negotiation, modified by a transparent adjustment layer (distribution coverage, listing gaps, known constraints) so managers see fair, actionable targets rather than a model‑dictated quota.

---

## 4. Important framing — read this as **structural (stock) potential**

The index estimates the relative **size and richness** of each market — *not* an annual unit forecast. Two things follow:

1. **Anchor the absolute scale yourself.** Enter the realistic total annual market size per category (Assumptions tab). Shares come from the structural model; the absolute total comes from your knowledge of the real annual market — which already embeds replacement rate and saturation. This is the cleanest way to turn stock potential into addressable annual potential without a full installed‑base cohort model.
2. **Pasting a full year of actuals doubles as a calibration backtest.** If the model systematically scores one category low everywhere (or one country high everywhere), that's a signal to re‑tune the relevant β — not necessarily a sales problem. Re‑tune to data, then freeze parameters under change control so performance scoring stays credible.

---

## 5. Data

Indicative real figures for framework validation (replace with your internal panels/sell‑out):

- **AIC & GDP in PPS, comparative price levels** — Eurostat 2024 first estimates (EU27=100); non‑EU candidates via the Eurostat PPP project (Kosovo is **not** in it — its AIC is an estimate, flagged low‑confidence).
- **Population, households, household size** — national censuses 2021–2024 (Kosovo 2024, Serbia 2022, Montenegro 2023, Albania 2023, N. Macedonia 2021) and Eurostat.
- **Cooling‑degree‑days** — Eurostat/EEA (EU members) and Spinoni et al. climatology (non‑EU Balkans, estimated).
- **Tourism overnights** — Eurostat / national tourism boards.
- **Urbanisation, GDP‑PPP** — World Bank.

Each country carries a **data‑confidence badge** (H/M/L). Western‑Balkan non‑EU states carry more uncertainty than EU members.

> ⚠️ Indicative ASP and total‑market sizes are placeholders. Replace ASP with invoice‑level sell‑in price per country‑category, and the totals with your real market sizing, before using the absolute € figures operationally.

---

## 6. Known limitations & Phase‑2 roadmap

Surfaced by an econometric + appliance‑industry + BI review. None block Phase‑1 use as a *relative* index; all sharpen it.

**Your planned layers**
- **Product‑authority matrix — BUILT (Authority tab).** An editable country × category grid of mandate weights (1 = full authority, 0 = out of scope, decimals for shared). It produces a **strategy‑weighted composite** = Σ_k value(c,k) × authority(c,k), shown side‑by‑side with the neutral demand composite plus the priority‑shift (Δ share), and it can optionally re‑weight the target split in the Targets tab. Kept deliberately separate from the neutral model so "attractive because of real potential" ≠ "attractive because we prioritised it". Premium subsets inherit their parent's authority. This grid is also the bridge to the RPI (retailer sell‑through is measured only within categories an office actually has authority over).
- **RPI (Retailer Potential Index) — BUILT (Retailers tab).** Distributes each country's authority‑weighted category potential across its retail landscape: `RPI(retailer r, category k) = countryPotential(c,k) × auth(k,c) × [reach_r × channelFit(archetype_r, k) / Σ_r reach × fit]`. Retailers partition the country's in‑scope potential exactly (Σ retailers = country total). Outputs per retailer: fair‑share potential (€/units), share, and — on entering actual sell‑through — a performance index (actual ÷ potential); plus **whitespace** (potential in accounts with no sales = distribution gap), a **channel‑routing** view (which channel owns which category), and a **cross‑country rollup** (office scorecard: in‑scope potential, active coverage %, performance). Seeded with six **channel archetypes** (electronics specialist, mass/hyper, e‑commerce, kitchen/built‑in, DIY, B2B/HVAC) as an editable SAMPLE template — replace names + reach with your real accounts. Channel fit is what makes a specialist own TV/OLED, a kitchen studio own dishwashers, and an HVAC distributor own System AC.

**Drivers to add (in rough priority)**
1. **Grey / cross‑border imports** — *the* credibility issue for small border markets (Kosovo/Montenegro/N. Macedonia/BiH residents buy in Serbia, Italy, Greece). Add a net‑catchment adjustment so an office isn't punished for demand that leaked to a neighbour, or group leak‑paired markets. Until then, the "thin" flag on small markets is the interim safeguard.
2. **Installed‑base age / replacement waves** — turns stock potential into an explicit annual flow (new + replacement + upgrade) with category survival curves (WM ~10–12y, fridge ~12–15y, TV ~7–9y, AC ~10–15y).
3. **Electricity price & EU energy‑label regime** — run‑cost gate on AC/dryer adoption and a lift to the efficient/premium mix in EU members.
4. **FX / affordability shocks** for non‑euro markets (HUF, RSD, denar, lek); per‑country ASP from invoices; e‑commerce attribution rule for cross‑border online.
5. **Housing** — new‑build first‑fit (built‑in dishwashers, AC pre‑install), a dedicated coastal **second‑home** stock split out from hotel tourism, apartment vs detached mix.

**Methodological refinements**
- Replace the constant‑elasticity term with a **bounded logistic penetration** for saturated necessities (so high‑income markets don't multiply unbounded), and an explicit **income × climate interaction** for AC (so hot‑but‑poor markets aren't credited rich‑market AC potential).
- **Calibrate β** against external penetration anchors (Eurostat/GfK ownership, OLED share, AC stock) and, once available, regress `ln(units/base)` on the log‑drivers to recover exponents with standard errors.
- **Propagate uncertainty** (Monte‑Carlo over β ranges) and show potential/performance as bands, flagging any over/under‑potential call whose interval straddles 100.

---

*All inputs and parameters are editable live in the dashboard's Assumptions tab; the model recomputes instantly. The engine is dependency‑free and runs offline by double‑clicking `index.html` (also served at https://mpi.er45.com).*
