# Rack & PDU Management

[Italiano](README.md) · **English**

A single-file web tool for designing and **electrically verifying** data centre
racks: PDU load distribution, phase balancing, N+1 redundancy verification and
upstream power sizing.

No installation, no server, no external dependencies: double-click `index.html`
and it runs. All data stays on the user's machine.

## What it answers

The question is not "how much does this rack draw", but **"what happens when one
supply path fails"**. That is the case that matters at design time and the one
that normal-operation figures hide: two PDUs sitting at 45% look comfortable, but
lose one and the survivor jumps to 90%.

## Use it online

The application runs directly in your browser, nothing to download:

**https://robertobenassi.github.io/RackPDUManagement/**

The interface is available in English and Italian — use the IT/EN switch at the
top left.

## Key features

### Design verification
- **N+1 redundancy**: failure scenarios (normal, loss of feed A, loss of feed B)
  are recalculated on every change across the main breaker, phases and individual
  breakers. Each load bar shows both the current value and, with a marker, the
  value it would reach under fault. Per-rack verdict and installation summary.
- **Upstream power** (optional): each PDU can declare which source feeds it. Real
  topologies follow from that — a single UPS on both feeds, two independent UPS in
  2N, an N+1 parallel bank, or a UPS installed inside the rack. When both feeds
  trace back to the same source, the tool flags that redundancy exists only
  downstream. This section is **off by default**: with it disabled, nothing above
  the PDUs enters the calculations, so anyone who has already done the upstream
  study elsewhere is not handed assumptions they did not ask for.
- **Outlets**: C13/C19 count per side with plug type per device, because you can
  have current available and no free outlet.

### Calculation engine
- Configurable line-to-neutral voltage and real power factor.
- **Power factor and diversity at three levels**: device, rack, project. A storage
  rack can carry a different power factor from a compute rack.
- Real and apparent power kept distinct (kW and kVA) throughout.
- **Neutral current**: vector imbalance across the three phases plus third-harmonic
  contribution, which loads the neutral on switching power supplies even when the
  phases are perfectly balanced. Harmonic content is configurable.
- Configurable warning and alarm thresholds.
- Heat load (BTU/h), required airflow and estimated weight.

### Day-to-day use
- Multiple racks (12U, 24U, 42U, 45U, 48U) with an installation-wide summary.
- Library of PDU profiles; every field remains editable.
- Balance optimiser using two-level bin packing across phase **and** breaker,
  computed against the worst case.
- Drag and drop devices within the rack, with position swapping between devices of
  equal height.
- English and Italian interface, undo/redo, search and filters.
- JSON project files, CSV export, printing of one rack or all of them.

## Offline use

1. Download `index.html`
2. Open it in a recent browser (Firefox, Chrome, Edge, Safari)
3. Add your devices and configure the PDUs

Nothing is transmitted anywhere. Autosave uses the browser's local storage; to keep
or share a project use **Download configuration**, which produces a JSON file.

## Disclaimer

This tool supports design work. It does not replace verification by a qualified
professional, nor compliance with the applicable standards (IEC 60364, local wiring
regulations and any others that apply). Battery runtime is an **estimate** based on
an exponential law with a configurable exponent: always check it against the
manufacturer's discharge curves before putting it in a design document. Always
verify results against the nameplate data of the equipment actually installed.

## Licence

Dual-licensed:

- **Non-commercial use**: [GPL-3.0](LICENSE), free and open source.
- **Commercial use**: requires a commercial licence. See
  [COMMERCIAL-LICENSE.md](COMMERCIAL-LICENSE.md) or contact the author.

## Author

Roberto Benassi — [robertobenassi.com](https://www.robertobenassi.com)
