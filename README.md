# Count of influenza-like illness for selected US states

### Software requirements

I use `R` to manipulate the data and produce the charts. I use `data.table`, `ggplot2` and `scales` for this analysis. To download these packages, open `R` console and enter the following:

```r
pkgs <- c("data.table", "scales", "ggplot2")

for(i in seq_along(pkgs){
  if(!nzchar(system.file(package = "pkgs[[i]]))) install.packages(pkgs[[i]])
}
```

The `data/process_data.R` file reads the raw data and manipulate it to use in `analysis/analysis.R`. So the script flow is `data/process_data.R` --> `analysis/analysis.R`, pretty simple!

### Source

FluView: https://gis.cdc.gov/grasp/fluview/fluportaldashboard.html. Go on "Download Data" --> "Custom download". Years of 2015-2020 for CA, NY, TX, WA.
