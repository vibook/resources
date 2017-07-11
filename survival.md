- [cutoff finder](http://molpath.charite.de/cutoff/)
- [cutoff finder paper](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3522617/)
- [Cutpoint determination in continous predictive variables](http://www.stata.com/meeting/spain14/abstracts/materials/es14_perez.pdf)

```
zscore = (C2-AVERAGE($C$2:$C$325))/STDEV($C$2:$C$325)
rank = IF(D2>=MEDIAN($D$2:$D$325),"High","Low")
```

```
> library(survival)
> library(ggplot2)
> library(survminer)

> a <- read.csv("Mydata.csv", header=TRUE, sep=",")
> fit_median=survfit(Surv(TIME, EVENT)~rank_median,data=a)
> ggsurvplot(fit_median, pval=TRUE, legend="right")
> ggsurvplot(fit_median, pval=TRUE, legend="right", break.time.by=50, xlim=c(0,250))

> sdf <- survdiff(Surv(TIME, EVENT)~rank_median,data=a)
```

cut-point
```
> library(grid)
> library(mvtnorm)
> library(stats4)
> library(modeltools)
> library(zoo)
> library(strucchange)
> library(sandwich)
> library(party)
> library(maxstat)

> methy <- read.csv("TCGA_LAML_hMethyl450.csv", header=TRUE, sep=",")
> stat <- maxstat.test(Surv(OS, OS_IND)~cg10262052, data=methy, smethod="LogRank", pmethod="exactGauss", abseps=0.01)
> stat

Maximally selected LogRank statistics using exactGauss

data:  Surv(OS, OS_IND) by cg10262052
M = 3.3604, p-value = 0.01507
sample estimates:
  estimated cutpoint 
-0.4242
> plot(stat)

> methygroup = ifelse(methy$cg10262052<=-0.4242, 0, 1)
> methygroup = factor(methygroup)
> levels(methygroup) = c("below -0.4242", "above -0.4242")

> fit <- survfit(Surv(OS, OS_IND) ~ methygroup, data=methy)
> fit
Call: survfit(formula = Surv(OS, OS_IND) ~ methygroup, data = methy)

n events median 0.95LCL 0.95UCL
methygroup=below -0.4242  62     48    243     184     365
methygroup=above -0.4242 117     68    608     486     854
> plot(fit)
> survdiff(Surv(OS, OS_IND)~methygroup, data=methy)
Call:
  survdiff(formula = Surv(OS, OS_IND) ~ methygroup, data = methy)

N Observed Expected (O-E)^2/E (O-E)^2/V
methygroup=below -0.4242  62       48       31      9.27      13.2
methygroup=above -0.4242 117       68       85      3.39      13.2

Chisq= 13.2  on 1 degrees of freedom, p= 0.000282 
> out=coxph(Surv(OS, OS_IND)~methygroup, data=methy)
> out
Call:
  coxph(formula = Surv(OS, OS_IND) ~ methygroup, data = methy)

coef exp(coef) se(coef)     z       p
methygroupabove -0.4242 -0.686     0.504    0.191 -3.59 0.00033

Likelihood ratio test=12.2  on 1 df, p=0.000471
n= 179, number of events= 116 

ggsurvplot(fit, pval=TRUE, legent.title="cg10262052",
 legend.labs=c("below cut-point", "above cut-point"),
 xlab="Time(days)", break.time.by=500, main="TCGA LAML hMethyl 450 - cg10262052",
 legend="right", palette=c("#00BFC4", "#F8766D"))
```
