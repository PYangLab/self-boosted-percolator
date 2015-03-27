[Home](http://sydney.edu.au/engineering/it/~yangpy/index.html) > [Software](http://sydney.edu.au/engineering/it/~yangpy/software/Software.html) > self-boosted-percolator


# Self-boosted Percolator incorporated to X!Tandem, MASCOT, and SEQUEST, and integrated with ProteinProphet in Trans-Proteomic Pipeline #

## Introduction ##

[Percolator](http://per-colator.com/) is a popular algorithm for peptide-spectrum match (PSM) evaluation `[1]`. It uses a semi-supervised learning algorithm to learn a score for each PSM indicating the confidence of the match between the theoretical peptides and the observed spectra. We recently extended the original Percolator algorithm by implementing a cascade semi-supervised learning procedure where the algorithm repeatedly learning using its previous results. We call this implementation "self-boosted Percolator" (Figure 1).

<img src='http://self-boosted-percolator.googlecode.com/svn/sb-percolator.png' align='middle' alt='Before SSO Sampling' height='320' />

Figure 1. Schematic illustration of the cascade learning in self-boosted Percolator.

Here we incorporate self-boosted Percolator for X!Tandem, MASCOT, and SEQUEST search results in the framework of [Trans-Proteomic Pipeline](http://tools.proteomecenter.org/wiki/index.php?title=Software:TPP) (TPP) `[2]`, and integrate the PSM evaluation results from self-boosted Percolator with [ProteinProphet](http://tools.proteomecenter.org/wiki/index.php?title=Software:ProteinProphet) `[3]` for protein inference and identification (Figure 2). By incorporating self-boosted Percolator into the TPP pipeline, the algorithm can now be used conveniently as a key component in large-scale protein identification.

<img src='http://self-boosted-percolator.googlecode.com/svn/integratedSBP.png' align='middle' alt='Before SSO Sampling' height='320' />

Figure 2. Self-boosted Percolator is integrated with TPP.



## Example ##

  * Obtain the executable `BoostedPercolator.jar` from downloads link.

  * Using X!Tandem search result on ups1 dataset as an example. Obtain test data `ups1.xtandem.pep.xml.zip` and unzip the file.

  * Issue the following commend to see available options:
```
     java -jar BoostedPercolator.jar
```

  * Issue the following commend to test on the ups1 dataset:
```
     java -jar BoostedPercolator.jar -t ups1.xtandem.pep.xml
```

  * The output is written into the file called `boostPercolator_psm.xml` by default. Once you obtain this file, it can be further processed by `ProteinProphet` to generate protein identifications.

## Citation ##
Please cite the following publication if you use the tool.

  * Pengyi Yang, Jie Ma, Penghao Wang, Yunping Zhu, Bing B. Zhou, Jean Yee-Hwa Yang, Improving X!Tandem on peptide identification from mass spectrometry by self-boosted Percolator, _IEEE/ACM Transactions on Computational Biology and Bioinformatics_, 9(5):1273-1280, 2012 [PubMed](http://www.ncbi.nlm.nih.gov/pubmed/22689082) [[pdf](http://rp-www.cs.usyd.edu.au/~yangpy/publication/self-boosted%20percolator%20for%20xtandem.pdf)]

## Reference ##
`[1]` L. Kall et al. (2007) _Nat. Methods_, 4(11), 923-925.

`[2]` E. Deutsch et al. (2010) _Proteomics_, 10(6), 1150-1159.

`[3]` A. Nesvizhskii et al. (2003) _Analytical Chemistry_, 75, 4646-4658.