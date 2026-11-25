# Recombination Lab

An interactive, single-page simulator for teaching meiotic crossing over and genetic mapping. Students can follow one or two crossovers through meiosis, inspect the four resulting gametes, and solve mapping problems from simulated genotype counts.

The page runs entirely in a browser. It has no dependencies, build step, account requirement, or network requirement.

## Start

Open [`index.html`](index.html) in a modern browser. To share it through a static website, place `index.html` at the site root. Keep this `README.md` beside it if the simulator is published as its own GitHub repository.

## What it does

### Visual meiosis

- Shows a replicated pair of homologous chromosomes. Blue solid and orange dashed chromatids are also distinguished by their allele labels.
- Lets the user choose two or three genes, their physical positions, and parental phase.
- Steps through pairing, one or two crossovers, chromatid exchange, meiosis I and II, and the four gametes.
- Shows a centromere surrounded by a nonrecombining heterochromatic interval. Crossover intensity rises along each arm toward a distal plateau.

### Mapping practice

- Generates genotype counts for 100, 1,000, or 10,000 gametes and offers a CSV download.
- The guided view calculates adjacent two-point recombination fractions. For three genes, it also shows apparent double recombinants, the coefficient of coincidence (COC), and interference.
- **Student problem** hides the chromosome, positions, phase, and solution. **Generate new sample** repeats the current hidden setup.
- **New mapping problem with three linked genes** creates a new problem with three random gene letters, a random physical order and phase, and new positions on one chromosome arm. The genotype table uses alphabetical columns and shuffled rows, so its layout does not reveal gene order. **Reveal solution** shows the phase, order, and calculations. The student-mode CSV contains genotype and count only.

## Model and interpretation

- The chromosome has 100 arbitrary physical units. Coordinates 44–56 form a nonrecombining interval around the centromere. Crossover intensity approaches a plateau toward either chromosome end.
- Crossovers occur on a tetrad between randomly selected nonsister chromatids. A local inhibition rule makes nearby crossovers less likely; its strength is adjustable. The animated examples select chromatid pairs that make each exchange visible. The population sampler does not impose that visual constraint.
- Each gamete is sampled from a separate meiosis. Three-gene classroom datasets are additionally conditioned to have COC no greater than 1: the simulator redraws a batch, or for difficult settings replaces some observations with independently generated parental gametes. **These conditioned datasets are for teaching calculations, not for statistical inference about interference.** Two-gene datasets are unconditioned.
- The model's population recombination fraction approaches 50% for distant genes. A finite sample may show more than 50% recombinant gametes by chance; the simulator allows this. When an observed fraction exceeds 50%, the guided view does not assign it a two-point map distance.
- Multiplying an observed recombination fraction by 100 gives an *apparent* two-point distance in cM. Multiple exchanges can make it smaller than the true map length, especially for distant genes. COC is observed apparent double recombinants divided by the number expected from the two observed adjacent-interval recombination fractions; interference is 1 − COC.
- The random generator uses the browser's `Math.random` and does not currently support a reproducible seed.

This is an illustrative teaching model, not a calibrated map of a particular organism. The classroom COC limit is a design choice; unrestricted data can yield COC above 1. For a discussion of crossover patterning and COC, see [Zhang et al., *PLOS Genetics* (2014)](https://doi.org/10.1371/journal.pgen.1004042).

## Files

| File | Purpose |
| --- | --- |
| [`index.html`](index.html) | Complete simulator: interface, animation, and data generator |
| [`README.md`](README.md) | Setup, classroom use, and model notes |
