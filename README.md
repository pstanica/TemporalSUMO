# CalendarSUMO interval bundle (SUMO-aligned version)

This version aligns the interval layer with the temporal predicates already
present in SUMO.  It avoids introducing duplicate `allen*` predicates for
relations that SUMO already defines.

The KIF files now use those SUMO predicates directly.  `CalendarSUMO_3Allen.kif`
is retained only as an explanatory compatibility file and introduces no new
axioms.

One caveat is recorded explicitly in `CalendarSUMO_3Allen.kif`: SUMO
`overlapsTemporally` is broader than Allen's strict directional `overlaps`
relation.  SUMO's relation means that two intervals have a common temporal part
and is symmetric/reflexive.  Allen's strict overlap is directional:
`Begin(I) < Begin(J) < End(I) < End(J)`.  The present package does not need
strict directional overlap, so no replacement predicate is declared.  The Allen
file contains a commented optional template for `strictTemporalOverlap` in case
a later extension genuinely needs that relation.

## Normal load order

1. Core SUMO/MILO ontology
2. `CalendarSUMO_1Core.kif`
3. `CalendarSUMO_2Arithmetic.kif`
4. `CalendarSUMO_3Allen.kif` (explanatory placeholder; no new axioms)
5. `CalendarSUMO_4Intervals.kif`
6. optionally `CalendarSUMO_5Derived_Optional.kif`
7. `CalendarSUMO_6Benchmarks.kif`

Do not concatenate the files into one new file for checking unless Sigma has
already loaded the Core signature in the KB.  `CalendarSUMO_1Core.kif` remains a
signature file: it contains declarations and domain/range information only and
should be loaded before formulas using the new calendar predicates and interval
functions.

## Scope

The package is intentionally modest.  It does not include caches, activation atoms, acceleration rules, or solver performance claims.  The benchmark file contains
representative conjecture-style formulas only.
