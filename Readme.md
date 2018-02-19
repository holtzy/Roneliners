# R one-liners for daily analysis

Here is a set of R one-liners that I use on a daily basis for my data analysis. See also the Stephen Turner's [bioinformatics one-liners](https://github.com/stephenturner/oneliners) that gave me the inspiration.


## Contents

- [Working with matrix](#matrix)
- [Reordering](#reordering)



## Matrix
[[back to top](#matrix)]

Use rownames as a column:

    matrix %>% as.data.frame() %>% rownames_to_column("new_variable_name")

Matrix to long data frame

    matrix %>% as.data.frame() %>% rownames_to_column("var1") %>% gather(var2, value, -1)
    
Matrix to heatmap

    matrix %>% as.data.frame() %>% rownames_to_column("var1") %>% gather(var2, value, -1) %>% ggplot( aes(x=var1, y=var2)) + geom_tile()
    
Diagonal to NA

    diag(matrix) <- NA
    



## Reordering
[[back to top](#reordering)]

Reorder a factor using a specific order (`forcats`):

    data %>% mutate( myfactor = fct_relevel( myfactor, "level1", "level2", "level3") )
    
Reorder a factor following the median of a numeric column (`forcats`):

    data %>% mutate( myfactor = fct_reorder( myfactor, mynumeric, fun=median))

Other solution with `dplyr`:

    data %>% arrange( mynumeric ) %>% mutate( myfactor = factor(myfactor, levels=myfactor)






