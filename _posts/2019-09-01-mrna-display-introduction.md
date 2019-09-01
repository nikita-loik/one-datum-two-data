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

Hear I provide a novel method of [analysis of mRNA-display results](mrna_display), based on basic graph theory and implemented in [python](python_page) using [NetworkX](networkx_page) library.

As an experimental case for analysis I rely on my mRNA display, against biotin-tagged human recombinant PHD2, performed by me according to the previously published [protocol](hayashi_ref) with minor modifications.

Regretably so, the results of this research are yet to see the light.

[mrna_display]: https://github.com/nikita-loik/mrna-display
[python_page]:   https://www.python.org/
[networkx_page]: https://networkx.github.io/
[hayashi_ref]: https://onlinelibrary.wiley.com/doi/abs/10.1002/anie.201108118