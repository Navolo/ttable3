## ttable3


Mean or Median Comparison for a lot of variables between two groups with formatted table output.

### Syntax

    ttable3 varlist [if] [in], by(groupvar) [ format(%fmt) unequal welch median rowname
                   notitle nostar tvalue pvalue ]


### Description

The official command ttest tests that a single variable has the same mean within the
    two groups defined by groupvar, while another official command median do similar
    things for group medians.  ttable3 performs ttest for a group of variables specified
    in varlist with formatted table output. When median is specified, it performs median
    test.


### Examples

        +---------------+
    ----+ The auto data +-----------------------------------------------------------------

        * t-test
        . sysuse auto,clear
        . ttable3 price wei len mpg, by(foreign)
        . ttable3 price wei len mpg, by(foreign) f(%8.2f)

        * Median test
        . ttable3 price wei len mpg, by(foreign) median

        * Restrict to two-groups
        . tab rep78
        . ttable3 price wei len mpg if rep78==3|rep78==4, by(rep78)

        * Report t-value and ommit the satrs
        . ttable3 price wei len mpg, by(foreign) nostar tvalue

        +------------------------+
    ----+  Save in Excel or Word +--------------------------------------------------------

    you can use the user-written logout command to export the results into Excel or Word:

        . logout, save(Tab2_corr) excel replace: ttable3 price wei len mpg, by(foreign)
            notitle


### Acknowledgements

codes from ttable2 by Xuan Zhang and Chuntao Li have been incorporated for t-test.
    Any comments will be appreciated

### Author

- Yujun,Lian (Arlion) Department of Finance, Lingnan College, Sun Yat-Sen University.
- E-mail: arlionn@163.com.
- Blog: http://www.jianshu.com/u/69a30474ef33
- Homepage: https://www.zhihu.com/people/arlionn/
