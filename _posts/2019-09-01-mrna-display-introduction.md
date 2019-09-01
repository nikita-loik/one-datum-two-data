---
title: "mRNA Display Introduction"
date: 2019-09-01T00:00:00-00:00
categories:
  - blog
toc: true
tags:
  - mRNA display
  - drug discovery
  - graph theory
  - python
  - NetworkX
---

mRNA display is a very elegant technique which occasionally enabled the discovery of functional short-peptides. Those discoveries have inspired a lot of optimism in drug industry and research and brought billions-worth of funding to the field.  To date, however, the mechanism of this technique remains vaguely understood, which often leads to dubious experimental designs followed by biased interpretations of results.

Recent improvement of sequencing techniques allowed to take detailed 'snapshots' of mRNA-display system at every cycle of the evolution. Understandably, new types of data require new methods of analysis.

Hear I provide a novel method of [analysis of mRNA-display results][mrna-display], based on basic graph theory and implemented in [python][python] using [NetworkX][networkx] library.

As an experimental case for analysis I rely on my mRNA display, against biotin-tagged human recombinant PHD2, performed by me according to the previously published [protocol][hayashi-ref] with minor modifications.

Regrettably so, the results of this research are yet to see the light.

[mrna-display]: https://github.com/nikita-loik/mrna-display
[python]:       https://www.python.org/
[networkx]:     https://networkx.github.io/
[hayashi-ref]:  https://onlinelibrary.wiley.com/doi/abs/10.1002/anie.201108118