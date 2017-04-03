# time-series-clustering

library(TSclust)
library(dplyr)
library(magrittr)
library(ggplot2)
library(reshape2)


#directory setting
WD <- getwd()
setwd(WD)

#Create sythetic data set

# a random process
n <- 10
df1<- matrix(rep(0,52*n),nrow = 52 , ncol = n)
for(i in 1:n){
  df1[,i]<- matrix(rnorm(52)*i)
}

#An Auto Regressive Process
n <- 10
df2<- matrix(rep(0,52*n),nrow = 52 , ncol = n)
for(i in 1:n){
  df2[,i] <-arima.sim(model=list(ar=c(.9,-.2)),n=52)
}

# A Moving Average Process
n <- 10
df3<- matrix(rep(0,52*n),nrow = 52 , ncol = n)
for(i in 1:n){
  df3[,i] <-arima.sim(model=list(ma=c(-.7,.1)),n=52)
}

#Bind the data together 
df <- cbind(df1,df2,df3)


# Time warping and the distance matrix
data_ts_df <- as.data.frame(df)
colnames(data_ts_df) <- seq(1,ncol(df),1)
d <- diss(data_ts_df, METHOD ="ACF" )
is.na(d) <- sapply(d, is.infinite)
d[is.na(d)] <- 0
d[is.nan(d)] <- 0

# Hirarchial Clustering
clust<- hclust(d)
tr <- cutree(clust,k = 3)


# Prepare data for plot
tr <- rbind(tr,colnames(tr))
tr <- t(tr)
data <- data.frame(t(data_ts_df))
test <- melt(cbind(data,ID = rownames(data)),id.vars = "ID")
group <- data.frame(group = as.numeric(tr),ID =  as.numeric(rownames(tr)))
test1 <- merge(test,group, by = "ID")

# Plot Data
p <- ggplot(data=test1, aes(x = variable, y = value, colour = group, group = ID) ) +
  geom_line( show.legend = F ) + facet_wrap(~group)
  
