[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

>> The actual mean is: 1.024205155043831
The biased mean is: 2.403679100664282

Bias is due to households with no kid not being surveyed and kids with large households with occur with more freguency 

    '''

    import math
    import nsfg
    import thinkstats2
    import thinkplot

    # Read in file
    file = nsfg.ReadFemResp()
    # Use the NSFG respondent variable NUMKDHH to construct the actual distribution for the number of children
    # pmf = probability mass function
    pmf = thinkstats2.Pmf(file.numkdhh, label='actual')
    # Plot distribution
    thinkplot.Pmf(pmf)
    thinkplot.Config(xlabel='No. of children', ylabel='PMF')


    # compute the biased distribution from children survey

    # define BiasPmf function from ThinkStats book
    def BiasPmf(pmf, label):
        new_pmf = pmf.Copy(label=label)

        for x, p in pmf.Items():
            new_pmf.Mult(x, x)
        new_pmf.Normalize()
        return new_pmf


    # Create biased pmf using function & plot
    biased_pmf = BiasPmf(pmf, label='biased')

    # Plot the actual and biased distributions,
    thinkplot.PrePlot(2)
    thinkplot.Pmfs([pmf, biased_pmf])
    thinkplot.Show(xlabel='Number of children', ylabel='PMF')
    # Compute means
    print(f"The actual mean is: {pmf.Mean()}")
    print(f"The biased mean is: {biased_pmf.Mean()}")

    '''
