# 📊 Census and Presidential Elections Dashboard

This interactive dashboard, built using **R**, **Shiny**, and **Flexdashboard**, explores U.S. census data (2008–2023) alongside presidential election data (2000–2020). The application presents an integrated view of social indicators and voting trends at the state level.

---

## 🚀 Features

- **Census Data Visualization**: Analyze poverty levels, income distribution, and social wealth classifications across states.
- **Election Results**: Explore voting patterns over five presidential election cycles.
- **Dynamic Interactivity**: Built with Shiny for responsive charts and user-driven filtering.
- **Visual Enhancements**: Uses `ggplot2`, `plotly`, `gt`, `flextable`, and `magick` for polished visualizations.

---

## 📁 Data Sources

- U.S. Census Data:  
  [Link](https://raw.githubusercontent.com/dilernia/STA418-518/main/Data/census_data_state_2008-2023.csv)

- Presidential Elections Data:  
  `data/countypres_2000-2020.csv` (uploaded to repository or read locally)

---

## 🛠 Technologies Used

- **R** and **RMarkdown**
- **Flexdashboard** for layout
- **Shiny** for interactivity
- **Packages**:  
  `tidyverse`, `ggplot2`, `plotly`, `lubridate`, `mice`, `naniar`, `maps`, `scales`, `magick`, `grid`

---
## Vizualisations

### Scatterplot
```r
#scatterplot of homecost vs rent.
m <- ggplot(
  census_data,
  aes(
    x = median_monthly_home_cost,
    y = median_monthly_rent_cost,
    color = social_wealth_class,
    size = social_wealth_class
  )
) +
  geom_point(alpha = 0.3) +
  scale_fill_brewer(palette = "Set1") +
  labs(
    x = "Median monthly home cost ($)",
    y = "Median monthly rent cost ($)",
    caption = "Data Source: TidyCensus & US Census Bureau"
  ) +
  theme_bw() +
  theme(legend.position = "bottom")

ggplotly(m, tooltip = c("x", "y", "color", "size")) |>
  layout(
    legend = list(
      title = list(
        text = "Wealth Class"),
      orientation = "h",
      x = 0.7,
      xanchor = "right",
      y = -0.5
    )
  )
```
### Bar plot
```{r}
bar_plot <- census_data |> 
  group_by(county_state) |> 
  summarize(
    average_monthly_home_cost = mean(median_monthly_home_cost, na.rm = TRUE),
    average_monthly_rent = mean(median_monthly_rent_cost, na.rm = TRUE)
  ) |> 
  ungroup() |> 
  arrange(desc(average_monthly_home_cost)) |> 
  slice_head(n = 10) |> 
  pivot_longer(
    cols = c(average_monthly_home_cost, average_monthly_rent),
    names_to = "cost_type",
    values_to = "value"
  ) |> 
  mutate(county_state = factor(county_state, levels = unique(county_state)))|>
  ggplot( aes(x = county_state, y = value, fill = cost_type)) +
  geom_bar(stat = "identity", position = "dodge") +
  scale_fill_viridis_d() +
  labs(
    x = "State",
    y = "Average monthly cost ($)",
    caption = "Data source: TidyCensus R & United States Census website"
  ) +
  theme_minimal() +
  theme(
    axis.text.x = element_text(angle = 45, hjust = 1),
    legend.position = "bottom"
  )

ggplotly(bar_plot, tooltip = c("x", "y", "fill")) |>
  layout(
    legend = list(
      title = list(
        text = "Wealth Class"))
  )
```
---

## 📦 Installation and Deployment

### To Run Locally:

1. Clone the repository.
2. Open `dashboard.Rmd` in RStudio.
3. Click **"Run Document"** or use:

```r
rmarkdown::run("dashboard.Rmd")
```

### To Deploy on GitHub Pages:

1. Render the dashboard:

```r
rmarkdown::render("dashboard.Rmd")
```

2. Move the `.html` file to `/docs` folder (or root).
3. Enable GitHub Pages in repository settings (source = `main`, folder = `/docs` or `/`).
4. Access your dashboard at:  
   `https://yourusername.github.io/your-repo-name/`

---

## 👤 Author

**Obadiah Kiptoo**  
\_MSc in Data Science and Analytics, Grand Valley State University | Applied Statistics graduate, Moi University, Kenya | Passionate about data analysis, visualization and Machine Learning

For inquiries or collaboration, feel free to reach out!

**email**: Obadiahkiptoo1998@gmail.com
