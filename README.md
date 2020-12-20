### RBT4TCSC 
RBT4TCSC is an R package. This package is built based on the following references.
[1] Liu T., Ditzhaus, M. and Xu, J. A resampling-based test for two crossing survival curves. Pharm Stat. 2020;19:399–409.
[2] Lin X., Xu Q. A new method for the comparison of survival distributions. Pharm Stat. 2010;9:67-76.

### Installation
First download the RBT4TCSC_0.1.0.tar and install the package through Package Archive File.

### Exmple use
library(RBT4TCSC)
alpha=0.05
samSize1=25
samSize2=25
tau=8  #(0,tau) is the time interval that one is interested in
## Generate two sample
sur.time1=rexp(samSize1,1/2);   
censored.time1=runif(samSize1,0,8);
obs.time1=apply(cbind(sur.time1,censored.time1),1,min)# Observed time

sur.time2=rexp(samSize2,1/5);
censored.time2=runif(samSize2,0,8);
obs.time2=apply(cbind(sur.time2,censored.time2),1,min)

censor1<-sur.time1<=censored.time1;
censor2<-sur.time2<=censored.time2

sample1=cbind(obs.time1,censor1);
sample2=cbind(obs.time2,censor2)

## The ABC function is based on [1] and will return the valute of Tn, 95% quantile bootstrap version of Tn, and 95% quantile of Z
ABC(sample1,sample2,tau,alpha)
## The Lin is based on [2] and will return the statistics value 
LinStatABC(sample1,sample2)
