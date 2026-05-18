# CalendarSUMO interval bundle v1

This package is a modest six-file starting point for the SUMO/Allen continuation
of the Gregorian temporal-arithmetic work.

## Files

1. `CalendarSUMO_Core.kif`
   - numeric month bridge
   - class-valued date and date-time constructors
   - declarations for arithmetic predicates
   - `validCalendarDate`

2. `CalendarSUMO_Arithmetic.kif`
   - Gregorian month-length axioms
   - leap/nonleap February case
   - basic recursive `dateCalculation` rules
   - no caches, anchors, activation atoms, or acceleration rules

3. `CalendarSUMO_Allen.kif`
   - Allen-style endpoint relations over SUMO `BeginFn`, `EndFn`, and `before`

4. `CalendarSUMO_Intervals.kif`
   - interval realization functions
   - month/year and day/month bridge axioms
   - month adjacency
   - successor-day meeting
   - minute/day placement and minute adjacency

5. `CalendarSUMO_Derived.kif`
   - intentionally empty in v1, reserved for separately justified or checked lemmas

6. `CalendarSUMO_Benchmarks.kif`
   - a small conjecture-style suite aligned with the current manuscript examples

## Suggested load order

1. Core SUMO/MILO ontology
2. `CalendarSUMO_Core.kif`
3. `CalendarSUMO_Arithmetic.kif`
4. `CalendarSUMO_Allen.kif`
5. `CalendarSUMO_Intervals.kif`
6. optionally `CalendarSUMO_Derived.kif`
7. `CalendarSUMO_Benchmarks.kif` when selecting proof goals

## Scope

This package is intentionally small. It uses the prior tptp temporal files
as donors for the shared calendar constructors and the basic normalization style,
but it does not import their caches, activation atoms, or acceleration layers.

The benchmark file contains conjecture-style formulas marked by comments. A
downstream SUMO/Sigma or KIF-to-TPTP workflow can select those formulas as goals.

## Validation

The included `check_calendar_sumo_kif.py` performs lightweight structural checks:
parenthesis balance, ASCII sanity, a small date-literal validity pass, and scans
for forbidden cache/activation tokens in the semantic files.

It is not a full SUO-KIF parser and does not replace loading the files in the
intended SUMO toolchain.
