# R one-liners for daily analysis

Here is a set of R one-liners that I use on a daily basis for my data analysis. See also the Stephen Turner's [bioinformatics one-liners](https://github.com/stephenturner/oneliners) that gave me the inspiration.


## Contents

- [Working with matrix](#matrix)
- [Reordering](#reordering)



## Matrix
[[back to top](#matrix)]

Use rownames as a column  
    matrix %>% as.data.frame %>% rownames_to_column("new_variable_name")

Matrix to long data frame  
`matrix %>% as.data.frame() %>% rownames_to_column("var1") %>% gather(var2, value, -1)`



## Reordering
[[back to top](#reordering)]



Extract fields 2, 4, and 5 from file.txt:

    awk '{print $2,$4,$5}' input.txt


Print each line where the 5th field is equal to ‘abc123’:

    awk '$5 == "abc123"' file.txt


Print each line where the 5th field is *not* equal to ‘abc123’:

    awk '$5 != "abc123"' file.txt







