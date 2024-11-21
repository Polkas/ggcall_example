
# ggcall.example

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
remotes::install_github("https://github.com/Polkas/ggcall_example")
library(ggcall.example)

# Print the body of the function
forest_plot

df <- data.frame(
  Treatment = c("Treatment A", "Treatment B", "Treatment C"),
  Estimate = c(0.2, 0.5, -0.1),
  CI_lower = c(0.1, 0.3, -0.3),
  CI_upper = c(0.3, 0.7, 0.1)
)

# Call the function, gg_plot is a ggplot object
gg_forest <- forest_plot(df, "Estimate", "CI_lower", "CI_upper", "Treatment")
gg_plot

# Retrieve the plot construction code
call_forest <- ggcall(gg_plot)

# Optionally: Style the code with styler
# install.packages("styler")
styler::style_text(paste(deparse(call_forest), collapse = "\n"))

# Optionally: add assignments to call
styler::style_text(paste(deparse(ggcall_add_assignments(call_forest)), collapse = "\n"))

# Optionally: reevaulate the call
eval_ggcall(call_forest)

df <- data.frame(
  Category = c("A", "B", "C", "D"),
  Before = c(3.5, 4.2, 2.8, 5.1),
  After = c(4.0, 4.5, 3.1, 5.5)
)

gg_barbell <- barbell_plot(df, "Category", "Before", "After", group_labels = c("Before", "After"))

call_barbell <- ggcall(gg_barbell)

eval_ggcall(gg_barbell)
```

