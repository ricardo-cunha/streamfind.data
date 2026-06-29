# streamfind.data

R package with supporting data and other assets for the R package [StreamFind](https://github.com/odea-project/StreamFind).

<p align="center">
  <img src="inst/extdata/logos/streamfind.png" width="50%" />
</p>

## Installation

With R (>= 4.2.0) configured and [pak](https://pak.r-lib.org/) installed:

``` r
pak::pkg_install("odea-project/streamfind.data")
```

## Data Overview

Demo data is organized under `inst/extdata/data/` by technique.

### Mass Spectrometry (`mass_spec/`)

| Demo | Path | Description |
|------|------|-------------|
| **Basic TOF** | `mass_spec/basic_tof/` | TOF data in centroid mzML, centroid mzXML, and profile mzML formats spiked with chemical and internal standards. Includes suspect list (`suspects.csv`) and internal standards (`internal_standards.csv`). |
| **Basic Orbitrap** | `mass_spec/basic_orbitrap/` | Orbitrap MS1-only data in profile mzML and mzXML formats. |
| **Wastewater** | `mass_spec/wastewater/` | TOF data from a wastewater analysis project with blanks, influent, and ozonated secondary effluent samples in positive and negative polarity. Includes suspect list (`suspects.csv`) and internal standards (`internal_standards.csv`). |
| **MRM** | `mass_spec/mrm/` | Multiple Reaction Monitoring data: estrogens (negative polarity, `ms_spiked_estrogens.csv`), nitrosamines (positive polarity), and environmental chemical standards (positive polarity). |

### Raman Spectroscopy (`raman/`)

Raman spectra of Bevacizumab drug product and blank measurements in `.asc` format.

## Access Functions

``` r
# Mass spectrometry files
get_mass_spec_files()                                  # All MS files
get_mass_spec_basic_tof_files()                        # Basic TOF
get_mass_spec_basic_orbitrap_files()                   # Basic Orbitrap
get_mass_spec_wastewater_files()                       # Wastewater project
get_mass_spec_mrm_files()                              # MRM (all)
get_mass_spec_mrm_environment_files()                  # MRM environment
get_mass_spec_mrm_estrogens_files()                    # MRM estrogens
get_mass_spec_mrm_nitrosamines_files()                 # MRM nitrosamines

# Raman files
get_raman_files()                                      # All Raman .asc files

# CSV chemical lists (return file paths)
get_mass_spec_wastewater_suspects_csv()                # Wastewater suspects
get_mass_spec_wastewater_internal_standards_csv()      # Wastewater IS
get_mass_spec_basic_tof_suspects_csv()                 # Basic TOF suspects
get_mass_spec_basic_tof_internal_standards_csv()       # Basic TOF IS
get_mass_spec_mrm_estrogens_csv()                      # MRM estrogens
```

Read a CSV with `data.table::fread()`:

``` r
library(data.table)
suspects <- fread(get_mass_spec_wastewater_suspects_csv())
```
