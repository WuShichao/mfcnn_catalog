# Gravitational Wave Signal Recognition of O1 Data by Deep Learning
**He Wang<sup>1</sup>, Zhoujian Cao<sup>∗,2</sup>, Xiaolin Liu<sup>2</sup>, Shichao Wu<sup>2</sup>, and Jian-Yang Zhu<sup>1</sup>**


<sub>1. Department of Physics, Beijing Normal University, Beijing 100875, China</sub>
<sub>2. Department of Astronomy, Beijing Normal University, Beijing 100875, China</sub>  
<sub>*. corresponding author


## Introduction ##
`MFCNN` is our GW Event Trigger Generator (ETG), which is a matched-filtering-aided CNN.

This repository contains the `MFCNN` GW triggers catalog, for now, we offer O1 GW triggers triggered by `MFCNN`, we will add O2 & O3 triggers here in the near future. If leaving the data quality alone, we find 3363 triggers in O1 which include `GW150914`, `GW151012` and `GW151226`. If we consider only the data which pass the `CBC_CAT3` test, there are 2069 triggers in O1.

Here, we only offer the triggers which pass the `CBC_CAT3` test, so totally 2069 triggers in O1 data.


## Analysis Details ##
The details of `MFCNN` and our analysis are available in this [preprint paper](https://arxiv.org/abs/1909.13442).


## Accessing the Catalog: mfcnn_catalog_O1.hdf5 ##
There are two groups within the file, `/known_events` and `/complete`. Under each group, you can find a dataset with the same name. The `complete` dataset is the full dataset from our analysis.


```python
import h5py

catalog = h5py.File('./mfcnn_catalog_O1.hdf5', 'r')

# Get a numpy structured array of the candidate event GPS time and duration.
all_candidates = catalog['complete']
bbh_candidates = catalog['known_events']

# Show the GPS time of GW150914, GW151012 & GW151226.
print(bbh_candidates[:,0])
# Show the trigger duration of GW150914, GW151012 & GW151226.
print(bbh_candidates[:,1])

# Just like above, we can show all triggers' GPS time & trigger duration.
print(all_candidates[:,0])
print(all_candidates[:,1])
```

##### File format #####
Both datasets are structured arrays which have the following columns.

| Column           | Description                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| 0 |     The GPS time of `MFCNN` triggers.                                        |
| 1 |     The GPS time-centric trigger duration (in seconds).                                    |


## License and Citation
![Creative Commons License](https://licensebuttons.net/l/by-nc-sa/4.0/88x31.png "Creative Commons License")

This work is licensed under a [Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0) License](https://creativecommons.org/licenses/by-nc-sa/4.0/).

We encourage use of these data in derivative works. If you use the material provided here, please cite the paper using the reference:

```
@article{wang2019gravitational,
  title={Gravitational wave signal recognition of O1 data by deep learning},
  author={Wang, He and Cao, Zhoujian and Liu, Xiaolin and Wu, Shichao and Zhu, Jian-Yang},
  journal={arXiv preprint arXiv:1909.13442},
  year={2019}
}
```


## Acknowledgments ##
We are thankful to Hao Wei and Jing Li for many helpful discussions. This work was supported by the NSFC (No. 11690023 and No. 11622546) and by the Collaborative research program of the Institute for Cosmic Ray Research (ICRR), the University of Tokyo. Z. Cao was supported by "the Fundamental Research Funds for the Central Universities", "the Interdiscipline Research Funds of Beijing Normal University" and the Strategic
Priority Research Program of the Chinese Academy of Sciences, grant No. XDB23040100.
