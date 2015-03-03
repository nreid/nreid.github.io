---
layout: post
title: Comparative RNA-seq
---

I just dove into a really cool project looking at patterns of gene expression underlying osmotic adaptation in a phylogenetic comparative context. I think this work is really, really cool, but from the very start, we're faced with problems that I'm not sure how to deal with. 

The choice I'm currently mulling is whether we should try to assemble transcriptomes de novo for each species, or map them all back to a common reference. If we do reference mapping, things are computationally simpler and a larger gene set will ultimately be evaluated, but it seems that there must be some biases associated with the mapping, including mismapping resulting from divergence, failure to account for gene duplication/extinction among species etc. On the other hand, if we attempt de novo assemblies, we vastly increase the computational complexity, presumably many genes won't be assembled in many species, and thus won't be analyzed, but we will probably get a more accurate quantification of those genes that are included. 

Further complicating things, I've already tried mapping back to the reference genome with the Tuxedo pipeline, and mapping rates for species that diverge from the reference are stunningly low. Things get much better if I map to the transcriptome using a sensitive aligner like Stampy, but it seems we'll lose some of the benefit of reference mapping if we have to use our established species-specific transcriptome. 

I've been trying to review the literature, but there isn't a whole lot on this issue, but these papers have been helpful in thinking about this:

Vijay, Nagarjun, et al. *"Challenges and strategies in transcriptome assembly and differential gene expression quantification. A comprehensive in silico assessment of RNA‐seq experiments."* Molecular ecology 22.3 (2013): 620-634.

Benjamin, Ashlee M., et al. *"Comparing reference-based RNA-Seq mapping methods for non-human primate data."* BMC genomics 15.1 (2014): 570.

Hornett, Emily A., and Christopher W. Wheat. *"Quantitative RNA-Seq analysis in non-model species: assessing transcriptome assemblies as a scaffold and the utility of evolutionary divergent genomic reference species."* BMC genomics 13.1 (2012): 361.

