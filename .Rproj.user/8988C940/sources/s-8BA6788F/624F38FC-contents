# this script produces analysis regarding ILI data

# load libs
library(data.table)
library(ggplot2)

# load data
data <- readRDS("data/data_processed.RDS")

# PLOT1: aggregate week 1-4 by region and year
d1 <- data[, .(ILITOT = sum(ILITOTAL)), by = c("REGION", "SESS")]

  # loop over state names and save figures on figure  folder
usaStates <- data[, unique(REGION)]
abv <- c("CA", "NY", "TX", "WA")

for(i in seq_along(usaStates)){
  
  p <- ggplot(data=d1[REGION == usaStates[[i]]], 
              aes(SESS, ILITOT)) + 
    geom_line(aes(group=REGION), colour="white", size=2) + 
    geom_line(aes(group=REGION), colour="black", size=1.25) +
    geom_point(colour="white", size=3) +
    geom_point(colour="black", size=2) +
    geom_label(aes(label = scales::number(ILITOT)), nudge_y = d1[REGION == usaStates[[i]], diff(c(min(ILITOT), max(ILITOT)))]/20) + 
    theme_minimal() + 
    scale_x_continuous(labels = data[, unique(SESS_CD)]) + 
    scale_y_continuous(labels = scales::number) + 
    labs(x=NULL, y=NULL, 
         title=paste0("Outpatients with influenza-like illness (ILI) in ", abv[[i]]),
         subtitle="[-10,+10] weeks",
         caption= "Source: FluView Interactive (https://gis.cdc.gov/grasp/fluview/fluportaldashboard.html)")
  
  tiff(paste0("figures/", abv[[i]], "_ili.tiff"))
  print(p)
  dev.off()
  
}

rm(list=ls())