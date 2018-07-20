# R one-liners for daily analysis

Here is a set of R one-liners that I use on a daily basis for my data analysis. See also the Stephen Turner's [bioinformatics one-liners](https://github.com/stephenturner/oneliners) that gave me the inspiration. Note that the vast majority of the examples need the [tidyverse library](https://www.tidyverse.org) to be loaded. `library(tidyverse)`.


## Contents

- [Working with matrix](#matrix)
- [Reordering](#reordering)
- [Colors](#colors)
- [Shiny](#shiny)
- [Tidyr](#tidyr)
- [Dplyr](#dplyr)
- [Read a file](#read)
- [R markdown](#rmd)




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






## Colors
[[back to top](#colors)]






## Shiny
[[back to top](#shiny)]






## Tidyr
[[back to top](#tidyr)]







## Dplyr
[[back to top](#dplyr)]

Rename columns:

    data %>% rename(new_name=old_name, other_new_name=other_old_name)

Rename X by Y in a columns:

    data %>% mutate( new = recode(old, X="Y") )

Replace by x in column 1 if column 2 as a certain value:

    mtcars %>% mutate(mpg=replace(mpg, cyl==4, NA))




## R markdown
[[back to top](#rmd)]

See the [cheatsheet](https://www.rstudio.com/wp-content/uploads/2015/02/rmarkdown-cheatsheet.pdf) for basic tips.

Horizontal line to show a separation:

    ***
    
Center an image

    <center>
    ![caption](/path/to/img)
    </center>
    
Change background color of a specific part:
 
    <style>
    div.blue { background-color:#e6f0ff; border-radius: 5px; padding: 20px;}
    </style>
    <div class = "blue">
    Add the text you want
    </div>
    
Use buttons for secondary titles:

    # Title 1  {.tabset .tabset-fade .tabset-pills}
    ## Title2
    
Show a data frame using the DT library:

    datatable(data, rownames = FALSE, filter="top", options = list(pageLength = 5, scrollX=T) )

Add some white space to give some air in the document:

    <br>
    


## Format a number

A pvalue

A huge number

    scales::comma(n)

On the axis of a ggplot
    
    scale_y_comma


