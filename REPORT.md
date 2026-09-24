# One Dot, Two Thousand People
### The Geography of Educational Backlog in Mexico

**Application exercise 2 — Mapping inequality**
Samuel Dávila · Oscar Baltazar

---

### 1. Description of the data: what we are mapping, and where

We map **educational backlog** (*rezago educativo*) across Mexico's 32 federal entities. The indicator
is defined by INEA as the population aged 15 and over that has not completed lower-secondary education,
and it is reported in three nested, mutually exclusive levels: people who are **illiterate**, people who
are literate but did **not complete primary school**, and people who completed primary but **not lower
secondary**. Figures are official estimates as of **31 December 2025**.

The phenomenon is inequality in access to education, narrowed to something measurable: not attitudes or
quality, but the stock of adults whom the education system never carried to the legal minimum. Nationally
this is **27,233,798 people — 26.6% of all Mexican adults**. At state level the rate ranges from 16.6%
(Mexico City) to 44.9% (Chiapas).

We treat this as a manifestation of **structural violence**: no identifiable actor decides to deny
Chiapas an education, yet the arrangement reliably produces the outcome, and it does so along the same
north–south axis that organises income, infrastructure and public investment in Mexico. The deprivation
is inherited rather than chosen, and it is spatially patterned — which is precisely what makes a map the
right instrument.

Two facts in the data drove every design decision that follows:

- **Rate and volume disagree.** Chiapas has the worst rate (44.9%) but the State of Mexico has the most
  people (3,249,316). Mexico City has the *best* rate in the country and still holds more people in
  backlog (1,283,013) than the whole of Guerrero (1,024,811). A map showing only one of these misleads.
- **Equal rates can mean unequal depths.** In Guerrero, 26.0% of those in backlog cannot read or write at
  all; in Coahuila the figure is 6.7%. The south is not only further behind — it is further down.

### 2. Description of the graphic resources

**A dot-density map, not a choropleth.** A choropleth can only render a rate, and a rate erases the
people: it paints the State of Mexico pale despite it holding the largest affected population in the
country. In our map **each dot represents 2,000 people** (13,618 dots in total), placed at random inside
their own state. Density therefore encodes absolute volume — the thing a rate map structurally cannot
show.

**Colour encodes depth, not intensity.** Each dot is coloured by the level of backlog it belongs to:
**violet** for illiteracy, **red** for primary incomplete, **amber** for lower secondary incomplete. The
ramp runs dark to light with severity, so the visually heaviest ink marks the deepest deprivation. The
result is that regional *composition* becomes legible: the southern states read violet-heavy, the
northern states almost purely amber. Two variables — how many, and how far behind — sit in one mark.

**Albers Equal-Area Conic projection.** This is a substantive choice, not a stylistic one. In a dot map,
area *is* the denominator: a projection that inflates the north relative to the south would spread
identical dot counts over different areas and invite the reader to mistake a projection artefact for a
data signal. Albers preserves area exactly, so equal ink means equal ground.

**A ranked stacked-bar panel** returns the rate that the dot map deliberately subordinates. All 32 states
are ordered by percentage, each bar segmented by the same three colours, with the national average marked
at 26.6%. Read together, the two panels make the argument: the map shows where the people are, the bars
show where the burden is heaviest, and the gap between the two orderings is the finding.

**Accessibility and honesty.** The palette was validated computationally rather than by eye: on the
all-pairs colour-vision-deficiency test the worst pair scores ΔE 15.3 under deuteranopia (target ≥ 8) and
ΔE 20.8 for normal vision (floor ≥ 15). Because amber falls below 3:1 contrast against the paper, every
category is also labelled in the legend and every state's value is printed numerically, so no reading
depends on colour alone. The poster states explicitly that dot placement is random within each state and
does not indicate where individuals live — the honest claim a dot map makes is about *how many* and *what
kind*, aggregated to the state.

**Production.** The map was built from the raw INEA workbook in Python (pandas, NumPy, Matplotlib) and
exported at A2 (42 × 59.4 cm, 300 dpi). The full method — parsing, validation, projection mathematics,
rejection sampling and composition — is documented in a Jupyter notebook in the repository below, with
a fixed random seed so the poster is exactly reproducible.

### 3. Reference

Instituto Nacional para la Educación de los Adultos (INEA), Dirección de Prospectiva, Acreditación y
Evaluación. *Estimación de la población de 15 años y más en rezago educativo por entidad federativa, al
31 de diciembre de 2025.*
https://www.gob.mx/inea/documentos/estimaciones-del-rezago-educativo-al-31-de-diciembre-de-2025

Boundary geometry: OpenStreetMap contributors, public GeoJSON of Mexico's federal entities.

Code and data: `https://github.com/KibaSpark/mapping-inequality`
