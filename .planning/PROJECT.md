# DOCSight

## What This Is

A self-hosted DOCSIS cable internet diagnostic tool that monitors modem signal health, runs speed tests, tracks broadband quality, and generates diagnostic reports. Built with Python/Flask, SQLite, MQTT, and Docker. Used by self-hosters who want deep visibility into their cable connection quality without relying on ISP tools.

## Core Value

Accurate, real-time signal health assessment that helps users detect and escalate cable line problems before they cause visible service degradation.

## Requirements

### Validated

- ✓ DOCSIS signal polling via modem drivers (6 built-in) — existing
- ✓ Signal health assessment with configurable thresholds — existing
- ✓ Dashboard with metric cards (DS Power, US Power, SNR, Errors) + health badges — existing
- ✓ Speed test integration (Ookla) — existing
- ✓ BQM broadband quality monitoring (ThinkBroadband image integration) — existing
- ✓ Smokeping latency monitoring — existing
- ✓ BNetzA regulatory reporting — existing
- ✓ Weather correlation module — existing
- ✓ Journal/notes system — existing
- ✓ PDF diagnostic report generation — existing
- ✓ Module system with community registry — existing (#122, #128, #127, #130)
- ✓ Regional threshold profiles as community modules — existing (#130)
- ✓ Theme system with community themes — existing
- ✓ Settings UI with module management — existing
- ✓ Dark mode — existing
- ✓ Mobile-responsive layout with sidebar — existing
- ✓ SNR metric card with health badge and range — existing

### Active

- [ ] Community-contributed modem drivers via module system (#131)
- [ ] Non-DOCSIS modem/router support with GenericDriver (#129)
- [ ] Daily modulation performance distribution (#92)
- [ ] Before/After signal quality comparison (#50)
- [ ] Prometheus-compatible /metrics endpoint (#59)
- [ ] Modem restart detection via error counter reset (#60)

### Out of Scope

- BQM native charts from CSV/XML (#136) — blocked on ThinkBroadband API access, revisit when unblocked
- Community segment heatmap (#61) — moonshot, future milestone
- Peering quality check (#70) — moonshot, future milestone

## Context

- Existing codebase: ~743 tests, mature module system, 6 built-in modem drivers
- Module system supports: collectors, routes, settings, thresholds, themes — but NOT drivers yet
- Community request (#129) for non-DOCSIS support prompted the driver extensibility work
- Analysis features (#92, #50) requested by users who want deeper insight into signal quality over time
- Prometheus endpoint (#59) enables integration with existing monitoring stacks (Grafana, etc.)
- Modem restart detection (#60) fills a gap — restart events are currently invisible

## Constraints

- **Tech stack**: Python/Flask, SQLite, MQTT, Docker — no framework changes
- **Backwards compatibility**: Existing modem drivers and modules must continue working
- **Single-container deployment**: DOCSight runs as one Docker image on user NAS devices
- **Test coverage**: Maintain 743+ tests, all passing

## Key Decisions

| Decision | Rationale | Outcome |
|----------|-----------|---------|
| Driver contribution via module system | Reuses existing module infrastructure instead of new plugin system | — Pending |
| GenericDriver for non-DOCSIS | Enables all modem-agnostic features without a real DOCSIS modem | — Pending |
| Sample-based modulation distribution | Compute from poll samples, not inferred time ranges — avoids misleading data | — Pending |

---
*Last updated: 2026-03-01 after initialization*
