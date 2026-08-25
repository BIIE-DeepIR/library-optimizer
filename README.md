# Library Optimizer

A planning calculator for pooled variant libraries in genome engineering, built by
[BIIE](https://github.com/BIIE-DeepIR).

**Live app: <https://biie-deepir.github.io/library-optimizer/>**

## What it does

Estimates how much of a designed variant library you actually recover through a
pooled screen, and sizes each downstream experimental step accordingly.

Coverage is modelled with Poisson occupancy:

```
unique variants = L x (1 - e^(-N/L))
```

where `L` is library size and `N` is the number of integrated cells.

### Inputs

Library size, cells per transfection, number of transfections, post-transfection
viability, and integration efficiency.

### Experimental checkpoints

| # | Step | Output |
|---|------|--------|
| 1 | Culture expansion | Minimum culture volume to maintain target coverage |
| 2 | Freeze-down | Vials required for 1x / 2x / 3x backup banks |
| 3 | FACS / MACS sort | Unique variants recovered post-sort |
| 4 | PCR amplification | Template copies per variant, total gDNA, reactions needed |
| 5 | NGS sequencing | Runs required, with kit recommendations |

Supports HDR via Cas9 and serine integrase landing-pad insertion (Bxb1, PhiC31),
across Jurkat, CHO, Expi293, HEK-293, primary B/T cells, and *S. cerevisiae*.

Sequencer presets cover the Illumina MiSeq i100 series, Oxford Nanopore MinION,
and the instruments available through the ETH Basel Genomics Facility.

## Running locally

No build step and no dependencies. Clone the repository and open `index.html`
in any modern browser:

```bash
git clone https://github.com/BIIE-DeepIR/library-optimizer.git
cd library-optimizer
open index.html
```

All computation runs client-side. No data is transmitted anywhere.

## Repository layout

```
index.html            the application
assets/fonts/         Sofia Pro webfonts
assets/biie-logo.png  logo
```

## License

MIT - see [LICENSE](LICENSE).
