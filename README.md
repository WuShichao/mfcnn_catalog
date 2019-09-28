# Gravitational Wave Signal Recognition of O1 Data by Deep Learning
**He Wang<sup>1</sup>, Zhoujian Cao<sup>∗,2</sup>, Xiaolin Liu<sup>2</sup>, Shichao Wu<sup>2</sup>, and Jian-Yang Zhu<sup>1</sup>**


<sub>1. Department of Physics, Beijing Normal University, Beijing 100875, China</sub>
<sub>2. Department of Astronomy, Beijing Normal University, Beijing 100875, China</sub>  
<sub>*. corresponding author


## Introduction ##
`MFCNN` is our GW Event Trigger Generator (ETG), which is a matched-filtering-aided CNN.

This repository contains the `MFCNN` GW triggers catalog, for now, we offer O1 GW triggers triggered by `MFCNN`, we will add O2 & O3 triggers here in the near future. If leaving the data quality alone, we find 3955 triggers in O1 which include `GW150914`, `GW151012` and `GW151226`. If we consider only the data which pass the `CBC-CAT3` test, there are 2242 triggers in O1.

Here, we only offer the triggers which pass the `CBC-CAT3` test, so totally 2242 triggers in O1 data.


## Analysis Details ##
The details of `MFCNN` and our analysis are available in this [preprint paper](https://arxiv.org/abs/xxxx.xxxxx).

## Accessing the Catalog: mfcnn_catalog_O1.hdf ##
There are two datasets within the file, `/known_events` and `/complete`. The `complete` set is the full dataset from our analysis.


```python
import h5py

catalog = h5py.File('./mfcnn_catalog_O1.hdf', 'r')

# Get a numpy structured array of the candidate event GPS time and duration.
all_candidates = catalog['complete']
bbh_candidates = catalog['known_events']
```


## License and Citation
![Creative Commons License](https://i.creativecommons.org/l/by-sa/3.0/us/88x31.png "Creative Commons License")

This work is licensed under a [Creative Commons Attribution-ShareAlike 3.0 United States License](http://creativecommons.org/licenses/by-sa/3.0/us/).

We encourage use of these data in derivative works. If you use the material provided here, please cite the paper using the reference:

```
@article{Wang:2019XXX,
      author         = "He Wang, Zhoujian Cao, Xiaolin Liu, Shichao Wu, and Jian-Yang Zhu",
      title          = "{Gravitational wave signal recognition of O1 data by deep learning}",
      year           = "2019",
      eprint         = "xxxx.xxxxx",
      archivePrefix  = "arXiv",
      primaryClass   = "gr-qc",
      SLACcitation   = "%%CITATION = ARXIV:xxxx.xxxxx;%%"
}
```


## Acknowledgments ##
We are thankful to Hao Wei and Jing Li for many helpful discussions. This work was supported by the NSFC (No. 11690023 and No. 11622546) and by the Collaborative research program of the Institute for Cosmic Ray Research (ICRR), the University of Tokyo. Z. Cao was supported by “the Fundamental Research Funds for the Central Universities”, “the Interdiscipline Research Funds of Beijing Normal University” and the Strategic
Priority Research Program of the Chinese Academy of Sciences, grant No. XDB23040100.
