<p align="center">
<a href="https://iopscience.iop.org/collections/2632-3338_focus_issue_THAI">
<img src="THAI_logo_label.png"
     alt="THAI logo"></a>
</p>

<h1 align="center">
Code to reproduce figures in the THAI trilogy
</h1>
<h4 align="center">
Python code to analyze and visualize <a href="https://thai.emac.gsfc.nasa.gov/organization/thai">climate model output</a> for the TRAPPIST-1 Habitable Atmosphere Intercomparison (THAI).
</h4>

<h6 align="center">
Most figures from the THAI trilogy can be reproduced using Jupyter Notebooks in this reporistory.
Python scripts contain functions to preprocess and clean the data. They also contain common and model-specific variables for convenience. Contributions are welcome.
</h6>

<p align="center">
<a href="https://www.python.org/downloads/">
<img src="https://img.shields.io/badge/python-3.10-black.svg"
     alt="Python 3.10"></a>
<a href="LICENSE">
<img src="https://img.shields.io/badge/license-MIT-black.svg"
     alt="License: MIT"></a>
<a href="https://github.com/psf/black">
<img src="https://img.shields.io/badge/code%20style-black-000000.svg"
     alt="black"></a>
<br>
<a href="https://doi.org/10.3847/PSJ/ac6cf0">
<img src="https://img.shields.io/badge/DOI-10.3847%2FPSJ%2Fac6cf0-purple"
     alt="Published Part 1"></a>
<a href="https://iopscience.iop.org/article/10.3847/PSJ/ac6cf2">
<img src="https://img.shields.io/badge/DOI-10.3847%2FPSJ%2Fac6cf2-purple"
     alt="Published Part 2"></a>
<a href="https://iopscience.iop.org/article/10.3847/PSJ/ac6cf1">
<img src="https://img.shields.io/badge/DOI-10.3847%2FPSJ%2Fac6cf1-purple"
     alt="Published Part 3"></a>
<br>
<a href="https://arxiv.org/abs/2109.11457">
<img src="https://img.shields.io/badge/arXiv-2109.11457-red"
     alt="Preprint: Part 1"></a>
<a href="https://arxiv.org/abs/2109.11459">
<img src="https://img.shields.io/badge/arXiv-2109.11459-red"
     alt="Preprint: Part 2"></a>
<a href="https://arxiv.org/abs/2109.11460">
<img src="https://img.shields.io/badge/arXiv-2109.11460-red"
     alt="Preprint: Part 3"></a>
</p>


## What's in this repo?
| File | Purpose |
|:-----|:--------|
| `names/` | Model-specific names of variables and coordinates |
| `THAI-Cloud-Distribution.ipynb` | Cloud maps and meridional profiles |
| `THAI-Global-Diag.ipynb` | Global diagnostics (tables)|
| `THAI-Meridional-Profiles.ipynb` | Meridional profiles of temperature, WVP, CWP and cloud fraction |
| `THAI-Radiation-Fluxes.ipynb` | Maps of radiation fluxes at TOA and the surface |
| `THAI-Rot-Div-Components.ipynb` | Helmholtz decomposition |
| `THAI-Save-Time-Mean.ipynb` | Average data in time and save in an intermediate dataset |
| `THAI-Save-Time-Series.ipynb` | Average selected variables spatially and save in an intermediate dataset |
| `THAI-Sfc-Temp-Hist.ipynb` | Histograms of surface temperature |
| `THAI-Substellar-Profiles.ipynb` | Profiles of temperature, lapse rate, radiative heating at the substellar point |
| `THAI-TL-Streamfunction.ipynb` | Mass streamfunction in tidally locked coordinates |
| `THAI-Time-Series.ipynb` | Time series |
| `THAI-Time-Spectrum.ipynb` | Time variability as a spectrum |
| `THAI-Zonal-Mean-Zonal-Wind.ipynb` | Zonally averaged zonal wind |
| `calc.py` | Calculation of various climate diagnostics |
| `commons.py` | Common project-specific objects |
| `const_ben1_hab1.py` | Constants for the Ben 1 and Hab 1 cases |
| `const_ben2_hab2.py` | Constants for the Ben 2 and Hab 2 cases |
| `grid.py` | Operations on GCMs' grids |
| `load_thai.py` | Functions to load and merge THAI datasets |
| `model_exocam.py` | Functions relevant only to ExoCAM |
| `model_lmdg.py` | Functions relevant only to LMD-G |
| `model_rocke3d.py` | Functions relevant only to ROCKE-3D |
| `model_um.py` | Functions relevant only to the UM |
| `mypaths.py` | Paths to files and directories relevant to this project |
| `paper.mplstyle` | Matplotlib stylesheet |
| `plot_func.py` | Plotting functions |

## Want to re-use the code? Here are the instructions.
### Set up Python
Skip the first two steps if you have Jupyter Lab with `nb_conda_kernels` installed already.
1. Install [Miniforge](https://github.com/conda-forge/miniforge).
2. Install necessary packages to the `base` environment. Make sure you are installing them from the `conda-forge` channel.
```bash
conda install jupyterlab nb_conda_kernels
```
3. Check out or download this repository.
4. In the command line, navigate to the downloaded folder and create a separate conda environment.
```bash
conda env create --file environment.yml
```

### Download THAI data
All GCM THAI data are permanently available for download [here](https://ckan.emac.gsfc.nasa.gov/organization/thai), with variables described for each dataset.
If you use those data in your own research, please cite the relevant paper and add the following statement:

> THAI data have been obtained from https://ckan.emac.gsfc.nasa.gov/organization/thai, a data repository of the Sellers Exoplanet Environments Collaboration (SEEC), which is funded in part by the NASA Planetary Science Divisions Internal Scientist Funding Model.

### Open the code
1. Start the Jupyter Lab, for example from the command line:
```bash
jupyter lab
```
2. Open noteboks in the `thai` environment and start coding.

### Pre-process data
If you want to re-draw figures from the THAI trilogy papers, we recommend that you create an intermediate dataset first by averaging the THAI data in time or in space.
To get a dataset of time-averaged variables, use the [THAI-Save-Time-Mean.ipynb](THAI-Save-Time-Mean.ipynb) notebook.
To get a dataset of selected time series, use the [THAI-Save-Time-Series.ipynb](THAI-Save-Time-Series.ipynb) notebook.
**Before running these notebooks, make sure the paths to THAI data are set up correctly in [mypaths.py](mypaths.py)!**
Also note that these two notebooks use [dask](https://dask.org) which uses multiple cores to speed up calculations. You can adapt the number of cores to be more suitable for your machine.

## Acknowledging our work
If you use code from this repository, please cite our papers:

    @article{Fauchez22_thai,
    author = {Fauchez, Thomas J. and Villanueva, Geronimo L. and Sergeev, Denis E. and Turbet, Martin and Boutle, Ian A. and Tsigaridis, Kostas and Way, Michael J. and Wolf, Eric T. and Domagal-Goldman, Shawn D. and Forget, Fran{\c{c}}ois and Haqq-Misra, Jacob and Kopparapu, Ravi K. and Manners, James and Mayne, Nathan J.},
    doi = {10.3847/PSJ/ac6cf1},
    issn = {2632-3338},
    journal = {PSJ},
    month = {9},
    number = {9},
    pages = {213},
    publisher = {IOP Publishing},
    title = {{The TRAPPIST-1 Habitable Atmosphere Intercomparison (THAI). III. Simulated Observables—the Return of the Spectrum}},
    url = {https://iopscience.iop.org/article/10.3847/PSJ/ac6cf1 https://iopscience.iop.org/article/10.3847/PSJ/ac6cf1/meta},
    volume = {3},
    year = {2022},
    }
    @article{Sergeev22_thai,
    author = {Sergeev, Denis E. and Fauchez, Thomas J. and Turbet, Martin and Boutle, Ian A. and Tsigaridis, Kostas and Way, Michael J. and Wolf, Eric T. and Domagal-Goldman, Shawn D. and Forget, Fran{\c{c}}ois and Haqq-Misra, Jacob and Kopparapu, Ravi K. and Lambert, F. Hugo and Manners, James and Mayne, Nathan J.},
    doi = {10.3847/PSJ/ac6cf2},
    issn = {2632-3338},
    journal = {PSJ},
    month = {9},
    number = {9},
    pages = {212},
    publisher = {IOP Publishing},
    title = {{The TRAPPIST-1 Habitable Atmosphere Intercomparison (THAI). II. Moist Cases—The Two Waterworlds}},
    url = {https://iopscience.iop.org/article/10.3847/PSJ/ac6cf2 https://iopscience.iop.org/article/10.3847/PSJ/ac6cf2/meta},
    volume = {3},
    year = {2022},
    }
    @article{Turbet22_thai,
    author = {Turbet, Martin and Fauchez, Thomas J. and Sergeev, Denis E. and Boutle, Ian A. and Tsigaridis, Kostas and Way, Michael J. and Wolf, Eric T. and Domagal-Goldman, Shawn D. and Forget, Fran{\c{c}}ois and Haqq-Misra, Jacob and Kopparapu, Ravi K. and Lambert, F. Hugo and Manners, James and Mayne, Nathan J. and Sohl, Linda},
    doi = {10.3847/PSJ/ac6cf0},
    issn = {2632-3338},
    journal = {PSJ},
    month = {9},
    number = {9},
    pages = {211},
    publisher = {IOP Publishing},
    title = {{The TRAPPIST-1 Habitable Atmosphere Intercomparison (THAI). I. Dry Cases—The Fellowship of the GCMs}},
    url = {https://iopscience.iop.org/article/10.3847/PSJ/ac6cf0 https://iopscience.iop.org/article/10.3847/PSJ/ac6cf0/meta},
    volume = {3},
    year = {2022},
    }
