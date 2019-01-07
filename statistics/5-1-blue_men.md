[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

>> 34.3% of the population meets the height requirements,between 5'10 and 6'1, to be a blue man.

(python)

import scipy

#convert heights listed in inches to centimeters
low_ht = (5*12+10) * 2.54
hi_ht = (6*12+1) * 2.54

#use the CDF function to determind percentile ranks
low_pr = scipy.stats.norm.cdf(l_ht, 178, 7.7)
hi_pr = scipy.stats.norm.cdf(h_ht, 178, 7.7)

#subtract the percentile ranks 

print(hi_pr - low_pr)
