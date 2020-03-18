# process data for analysis

# load libs
library(data.table)

# read raw data
data <- data.table::fread("data/ILINet.csv", skip = 1)

# specify period of time: November to whatever max week in winter we are
  # winter cutoff point, early APRIL ~ week 16
  # falL, last 10 weeks (week 42 - week 52)
  # data in 2020 is incomplete for winter: subset all years for whichever max week 2020 has
winterWks <- data[WEEK <=16L & YEAR == 2020L, unique(WEEK)]
fallWks <- 42:52

# subset data
d1 <- data[WEEK %in% fallWks | WEEK %in% winterWks, ]

# create new time category
  # FALL Y_i / WINTER Y_(i+1)
d1 <- d1[order(REGION, YEAR, WEEK), ]

periodLen <- length(c(fallWks,winterWks))
periodRevs <- nrow(d1)/periodLen
periodGroups <- periodRevs/length(d1[, unique(REGION)])

d1[, SESS := rep(rep(seq_len(periodGroups), each = periodLen), length(d1[, unique(REGION)]))]

sessLabs <- paste0(c(15:19), "-", c(16:20))

d1[, SESS_CD := sessLabs[1 + 
                           1*(SESS == 2L) + 
                           2*(SESS == 3L) + 
                           3*(SESS == 4L) + 
                           4*(SESS == 5L)]]

saveRDS(d1, "data/data_processed.RDS")
rm(list=ls())