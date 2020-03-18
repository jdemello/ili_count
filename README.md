# ili_count

## Count of influenza-like illness for selected US states

You can find the charts in `figures/...`.

I use `R` to manipulate the data and produce the charts. I use `data.table`, `ggplot2` and `scales` for this analysis. To download these packages, open `R` console and enter the following:

```r
pkgs <- c("data.table", "scales", "ggplot2")

for(i in seq_along(pkgs){
  if(!nzchar(system.file(package = "pkgs[[i]]))) install.packages(pkgs[[i]])
}
```
