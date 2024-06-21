library(ggplot2)
library(dplyr)
library(readxl)
library(plotly)

p <- ggplot(data, aes(x = ARADJQ, y = ARADJP, group = interaction(ARADJT, ARDESC), color = ARADJT)) +
    geom_line(size = 0.05) +
    geom_point(aes(shape = ARDESC), size = .05) +  # Adjust point size here (e.g., size = 2)
    labs(title = "Comparison of ARADJP vs ARADJQ",
         x = "ARADJQ",
         y = "ARADJP",
         color = "ARADJT",
         shape = "ARDESC") +
    theme_minimal() +
    xlim(0, 10000)

# Convert ggplot to plotly
interactive_plot <- ggplotly(p)

interactive_plot <- layout(
    interactive_plot,
    xaxis = list(
        tickvals = seq(0, 10000, by = 500),
        ticktext = seq(0, 20, by = 1)
    )
)

# Print the interactive plot
interactive_plot


