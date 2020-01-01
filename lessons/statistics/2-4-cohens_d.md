[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

Here's are the mean pregnancy lengths for first babies and others:

firsts.prglngth.mean(), others.prglngth.mean()
(38.60095173351461, 38.52291446673706)

And here's the difference (in weeks):

firsts.prglngth.mean() - others.prglngth.mean()
0.07803726677754952

This functon computes the Cohen effect size, which is the difference in means expressed in number of standard deviations:

def CohenEffectSize(group1, group2):

    """Computes Cohen's effect size for two groups.
    
    group1: Series or DataFrame
    group2: Series or DataFrame
    
    returns: float if the arguments are Series;
             Series if the arguments are DataFrames
    """
 ​   
    diff = group1.mean() - group2.mean()
    var1 = group1.var()
    var2 = group2.var()
    n1, n2 = len(group1), len(group2)
​
    pooled_var = (n1 * var1 + n2 * var2) / (n1 + n2)
    d = diff / np.sqrt(pooled_var)
    return d
    
Compute the Cohen effect size for the difference in pregnancy length for first babies and others.

print(CohenEffectSize(firsts.prglngth, others.prglngth))
0.028879044654449883

Using the variable totalwgt_lb, investigate whether first babies are lighter or heavier than others.

Compute Cohen’s effect size to quantify the difference between the groups. How does it compare to the difference in pregnancy length?

print("firsts mean weight: " + str(firsts.totalwgt_lb.mean()))
print("others mean weight: " + str(others.totalwgt_lb.mean()))
​
firsts mean weight: 7.201094430437772
others mean weight: 7.325855614973262

print(CohenEffectSize(firsts.totalwgt_lb, others.totalwgt_lb))
-0.088672927072602

According to the data the above results tell us that first babies took an average of .078 weeks longer in pregnancy and weighed .125 pounds lighter than other babies. The corresponding Cohen's D values confirm this with values of .029 for pregnancy length in weeks and -.089 for total weight in pounds. 
