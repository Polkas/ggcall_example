
# ggcall_imp

Package created as an example of easy implementation of ggcall.

Package created with

```
usethis::create_package(".")
usethis::use_testthat(edition = 3)
```

Upload standalone ggcall files

```
usethis::use_standalone("polkas/ggcall", "patchwork.R", ref = "v0.3.3")
```

Now the forest and barbell plot functions were created 

```r
remotes::install_github("https://github.com/Polkas/ggcall_imp")
library(ggcall.imp)

df <- data.frame(
  Category = c("A", "B", "C", "D"),
  Before = c(3.5, 4.2, 2.8, 5.1),
  After = c(4.0, 4.5, 3.1, 5.5)
)

# Create the barbell plot
barbell_plot(df, "Category", "Before", "After", group_labels = c("Before", "After"))
```

```r
df <- data.frame(
  Treatment = c("Treatment A", "Treatment B", "Treatment C"),
  Estimate = c(0.2, 0.5, -0.1),
  CI_lower = c(0.1, 0.3, -0.3),
  CI_upper = c(0.3, 0.7, 0.1)
)

# Create the forest plot
forest_plot(df, "Estimate", "CI_lower", "CI_upper", "Treatment")
```

