# Zonation5RData

Educational GeoTIFF layers for [Zonation](https://github.com/zonationteam/Zonation5) and [ZonationR](https://github.com/thiago-cav/ZonationR) workflows. Rasters use WGS84 (EPSG:4326). This package is **not** on CRAN; install from GitHub.

## Installation

```r
# install.packages("pak")  # if needed
pak::pak("thiago-cav/Zonation5RData")
```

Or with **remotes**:

```r
# install.packages("remotes")
remotes::install_github("thiago-cav/Zonation5RData")
```

## Usage

After installation, data live under `inst/extdata` in the package sources. From R:

```r
library(Zonation5RData)

# Root of packaged extdata
zonation5rdata_root()

# List top-level names under extdata
zonation5rdata_example()

# List every file under extdata/biodiversity/ (e.g. all species GeoTIFFs)
head(zonation5rdata_list("biodiversity"))
length(zonation5rdata_list("biodiversity"))

# Absolute paths (e.g. for terra::rast(), or batch processing)
# head(zonation5rdata_list("biodiversity", full.names = TRUE))

# Only files directly in other_layers/ (no subfolders)
zonation5rdata_list("other_layers", recursive = FALSE)

# Resolved path to one file (errors if missing)
zonation5rdata_example("other_layers/gHM_Europe.tif")

# Same via components:
zonation5rdata_path("biodiversity", "Fagus_sylvatica.tif")
zonation5rdata_path("other_layers", "gHM_Europe.tif")
zonation5rdata_path("other_layers", "area_mask.tif")
```

To read a raster (example with **terra**):

```r
# install.packages("terra")
# terra::rast(zonation5rdata_path("other_layers", "gHM_Europe.tif", must_work = TRUE))
```

## Contents and attribution

Layer descriptions, folder layout, and references can be accessed with:
```r
zonation5rdata_info()
```



Please cite this package and the original data sources (see `metadata.md`) when you use these materials.

## Licence

Package code: MIT (see `LICENSE`). Data layers retain their original licences and citation requirements as described in `metadata.md`.
