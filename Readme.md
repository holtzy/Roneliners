# R one-liners for daily analysis
===================

Here is a set of R one-liners that I use on a daily basis for my data analysis. See also the Stephen [Turner bioinformatics one-liners](https://github.com/stephenturner/oneliners) that gave me the inspiration.





## Reordering

## Matrix

Use rownames as a column
`matrix %>% as.data.frame %>% rownames_to_column("new_variable_name")`

Matrix to long data frame
`matrix %>% as.data.frame() %>% rownames_to_column("var1") %>% gather(var2, value, -1)`



REORDERING
--------





