---
title: "mRNA Display Results Analysis"
date: 2019-09-01T00:00:00-00:00
categories:
  - blog
toc: true
toc_label: "Table of Contents"
toc_icon: "th-list"
tags:
  - mRNA display
  - drug discovery
  - graph theory
  - python
  - NetworkX
---
## Introduction

[mRNA display][szostak-ref] is a very elegant technique which occasionally enabled the discovery of functional peptide ligands. Those discoveries have inspired a lot of optimism in drug industry and research and brought billions-worth of funding to the field. To date, however, the mechanism of this technique remains vaguely understood, which often leads to dubious experimental designs followed by biased interpretations of results.

Recent improvement of sequencing techniques allowed to take detailed 'snapshots' of mRNA-library at every cycle. Understandably, new types of data require new methods of analysis. Hear I provide a novel method of [analysis of mRNA-display results][mrna-display], based on basic graph theory and implemented in [python][python] using [NetworkX][networkx] library.

For experimental data I rely on a successful [mRNA display][mrna-display-data], against biotin-tagged human recombinant PHD2, I performed according to the previously published [protocol][hayashi-ref] with minor modifications. Regrettably so, the results of this research are yet to see the light.

## mRNA-Display Background

### Bio-Chemistry

mRNA display is based on the 'survival of the fittest' algorithm. Beginning with a highly diverse collection of structurally different ligands:

1. ligands are mixed with a target, and some bind to the target
2. poorly binding ligands are washed away
3. ligands which bound well are amplified

The process is repeated several times. In the result some ligands may be amplified to a much higher level than the other, and such ligands are considered to have a better binding properties.

Indeed, as a result of successful mRNA display it may be possible to find some ligands which bind well to the target. Nevertheless, such simplistic approach fails to explain, why in some cases after multiple cycles of mRNA display the most amplified ligand has weaker binding properties than some much less amplified ligands.

### Bayesian Approach

#### Priors

##### Selection Library

* random peptide region was 8-12 amino-acids long
* for peptide-encoding region NNK library was used (where N = A/C/G/T; and K = G/T, total 32 codons)

Thus, the original library diversity is between 10^12 to 10^18 (~1 pmol to ~1 µmol).

* original library amount
* the library was amplified using 5 cycles of PCR (i.e. )
* library amount used for selection

##### Selection Process

* target amount ~10^-6 M
* ligand concentration ~10-6 M



#### Likelyhood

<figure class="align-center">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/mrna_display_results_by_cycle.png" alt="">
  <figcaption>a result of successful mRNA display</figcaption>
</figure>

[szostak-ref]: https://www.sciencedirect.com/science/article/pii/S1359644613003553
[mrna-display-repo]: https://github.com/nikita-loik/mrna-display
[python]: https://www.python.org/
[networkx]: https://networkx.github.io/
[mrna-display-data]: https://github.com/nikita-loik/mrna-display/tree/master/sample_input
[hayashi-ref]: https://onlinelibrary.wiley.com/doi/abs/10.1002/anie.201108118

<!-- [mrna-display-results-by-cycle]: /assets/images/mrna_display_results_by_cycle.png -->
